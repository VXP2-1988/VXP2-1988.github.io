---
layout: post
title:  Ticketing Site Part 5
date:   2022-06-10
tags:   project-ticketing-site
categories: 
---
### Implementing Email Functions
Finally finished the core email functionality. Email body is generated using Flask's render_template() method and the PDF attachement is generated using xhtml2pdf. I ended up creating a separate template for the pdf because xhtml2pdf only recognizes a specific subset of CSS rules and that would limit my formatting options for the website. After some testing I decided to put the CSS rules in the html file head because it was faster, which also means I can use any CSS rules. I may need to change it back though, so I'll keep the more flexibile implementation. 

I spent the most time getting xhtml2pdf to write the document directly into memory and then load it as an attachment. My first version saved the pdf file to disk, which took too long on my local machine and longer with the free tier of Heroku. Since it was so expensive to create the file, write it, then read it, then delete it, I opted to keep it in memory instead. 

The documentation mentioned that it was possible to use StringIO to keep the file in a buffer but provided no example. Using StringIO like any other file object returned an error message that xhtml2pdf was expecting a string argument and got binary. The stack trace concluded with this line in xhtml2pdf's document.py file:
`File "/home/logan/projects/test-pdf-email/venv/lib/python3.10/site-packages/xhtml2pdf/document.py", line 180, in pisaDocument
context.dest.write(data)  # TODO: context.dest is a tempfile as well...
TypeError: string argument expected, got 'bytes'
`
`def do_pdf(html):
    mydest = StringIO()
    status = pisa.CreatePDF(
        src=html,
        dest=mydest
    )   
    return mydest`
My reading had suggested that it was not necessary to use open() on StringIO, but passing the object directly like an open file stream was getting me nowhere.

After setting some breakpoints and examining the library, I noticed that the dest field of the returned object contained a BytesIO object if I didn't include a dest parameter in my CreatePDF() call. I tried using that BytesIO object as an open file as well to no avail, pdf.read() just returned `b''`when I opened the object using `with result as pdf:`
However, the debugger and documentation showed me that getvalue() was returning the bytes and data that I was interested in. That method finally allowed me to get plain bytes that I could encode and add as an attachement.

The rest of the time I worked on getting the invoice pdf formatting up to requirements of my client. After removing the old and outdated inline styles they provided me and writing new ones, I now have a result they're happy with and that can be changed and extended easily to fit future requirements. Now that I have all the core functions they wanted complete, it's time for me to work on getting automated testing setup. I'd also like to revisit StringIO and BytesIO, since I don't understand why write() and read() aren't working like I expected.

### BytesIO and StringIO
Chalk that one up to overthinking, I guess. On closer examination it was obvious that StringIO is a string buffer, and that I was attempting to write a PDF as bytes into it. If I change StringIO to BytesIO, then it runs without errors. Good to know for the future - when I'm dealing with buffering files, use the raw data, strings are only useful if the contents are readable as strings. This is a lesson in knowing what kind of data I'm trying to read and write.