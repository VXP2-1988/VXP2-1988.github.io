---
layout: post
title:  Ticketing Site Part 2
date:   2022-06-05
tags:   project-ticketing-site
categories: 
---
### Changing Tact
Work has been busy for the past few days and I haven't had time to work on the ticketing project. After several hours working with the Vue app and Flask routers I've reevaluated my workload and I'm not going to be able to complete this project this month with my current workload. There's too much new stuff to learn and I'm working on this solo.

Additionally, I'd like to have something to deliver sooner to my client, who has expressed more interest in this project lately. Since the login, ticketing, and site data storage functions are relatively straightforward, I'll be implementing them in Flask and Jinja and leaving the more involved features for later implementation with a better frontend framework. That way I can finish this on time, deliver something with the core functionality, and get more familiarity with login systems before jumping into Vue.

### Sunday, June 5 Work Summary
Created a basic SQL schema to store user credentials. 

Implemented a login system using Flask-Bcrypt. User passwords are salted and hashed using bcrypt, the password is never stored on server. Credentials are then stored in SQL database. The logged in user is stored in the session cookie and protected with a randomly-generated secret key. All secrets are stored as environment variables and loaded using python-dotenv.

Basic sign in and sign out work. Since this website isn't meant for public use, only a logged-in admin user can create a new account. Anyone not logged in is presented with a login screen or redirected there if they try to access URL's directly.

Added nav links and basic templates for all fundamental website functions. This includes invoicing and data view, account settings, and all user accounts view (for admins). Basic styling with Bootstrap 5.

Copied the invoicing forms from the old site, cleaned them a little, and implemented them in-template. Created Javascript to add event listeners to labor and material sections so that extra table rows can be added on click. 

### References
[How Does Flask Secret Key Work](https://stackoverflow.com/questions/22463939/demystify-flask-app-secret-key)