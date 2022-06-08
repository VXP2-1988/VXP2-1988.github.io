---
layout: post
title:  Ticketing Site Part 4
date:   2022-06-07
tags:   project-ticketing-site
categories: 
---
So far I've been working on the email functionality. Initially started off using Flask-Mail, but switched to ussing smtplib because Google kept dropping Flask-Mail's authentication requests. Gmail changed the way they handle insecure apps on May 30, which may have something to do with that. Generated a app-specific password for my dev app. 

Spent a good while trying to figure out an issue where Google was rejecting my credentials for the new app. Turns out Flask only reloads environment variables on restart and it was still storing the old credentials, which makes sense on examination.

Now I can login to my Gmail smtp server using TLS and send messages. Client has stipulated that they want a PDF copy of the invoice sent to their inbox. I also need to send an HTML copy and a backup plaintext copy as the body header.

The Flask + Jinja combo has the ability to render HTML pages already. This means that I can use it to render an HTML page looking like the stored invoice, with all the invoice fields filled in. I can then use the returned rendered html and add it to the email message body. The email then appears the same way the form does on the webpage.

The invoice form for dispay is abstracted out into another sub-template, so that the email body and the invoice view body on the website are the same. This creates less code and a more consistent display.

### Work Summary, Tuesday
Spent most of the day on SMTP server stuff and creating the send email functionality. Also created all invoice views and modified the schema a little to allow for more flexible input. Also linked the all invoice view to the single invoice view. Did some miscellaneous clean up.

Tomorrow I'll have work but next up I need to work on automated testing, error checking, and add some error messages for the benefit of the user. The application has gotten large enough that I need to devote some time to making sure that each individual component works correctly.

I'd also like to either use the client's SMTP server or use my own. Currently I'm relying on Google's and setting up my own could be an interesting task. I have a spare Raspberry Pi 2 that isn't doing anything else.

Also seeing some good future applications for Vue. Invoice editing and management would best be done that way, doing too much server-side work rendering templates is asking for slowdowns and trouble. For now I'll keep that application in mind and keep the routes clean so that I can reuse them as the backend for an SPA application.