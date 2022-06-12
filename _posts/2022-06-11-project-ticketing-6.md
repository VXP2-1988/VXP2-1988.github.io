---
layout: post
title:  Ticketing Site Part 6
date:   2022-06-11
tags:   project-ticketing-site
categories: 
---
Didn't have a lot of time today, but I added some error messages for bad logins. Also cleaned up my code from yesterday with a better understanding of BytesIO objects. Finally, did some testing and noticed that the smtp server login took a few seconds. This made sending invoices slower than I'd like and delayed the rest of the program. 

Rather than leaving the connection open to save time, I used Threads() to asynchronously call my email helper methods. Now when the invoice is generated, the html is sent to a new thread for message construction/sending, and the program continues on. The result is a much snapper invoice sending process. On send, the program immediately redirects to show all invoices and a few seconds later the email appears. Ran into some issues because the new thread has a different context and so doesn't have access to the session cookie or invoice ORM object. Solved by copying the relevant variables before sending them to the thread.

Also added simple logging functionality to show the IP address, user agent, account name, and other information a user logs in with. Helps me to keep track of who's using the site and when. Email notifications are sent using a similar async process.