---
layout: post
title:  Ticketing Site Part 3
date:   2022-06-06
tags:   project-ticketing-site
categories: 
---
### Work Summary, Monday
Added tables for invoice, labor, materials. Connected tables to router and forms. Connected invoice to labor/materials as one-to-many relationship. Created separate table for grocery invoice and other invoice.

All grocery invoices can now be viewed in a page. Started work on email service.

Created heroku app to host website. Froze requirements, created procfile, and pushed everything to heroku. Deployed app. Added MySQL db addon to handle data storage. Updated environment variables.

Heroku app allows basic login, grocery invoice creation, and grocery invoice view all. 

All Feature List TODO:
* Mail server, send invoice.
* Print invoice.
* Single invoice view/edit linked to all invoices view.
* Automated testing.
* Error messages for login fail.
* Form validation.
* Error checking.
<p></p>
The User table is the only database table needed for core functionality. All other tables and the view all/search functionality are proof-of-concept for my client. As such, I'll focus on the core features for now: email invoices, print invoice, testing, and login fail messages.