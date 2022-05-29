---
layout: post
title:  Software Engineering Final Project Retrospective
date:   2022-05-27 10:56
categories:
tags:   webdev software-eng
---
### Overview
The final project for Software Engineering was a SaaS (Software as a Service) web application built in Flask. Development was a 10-week long process using the Agile development framework. Each 2-week-long sprint had 3 standup meetings, 1 sprint planning meeting, and 1 sprint retrospective. The end result was an image sharing forum with user signup, post creation, and commenting functions. Spec sheet is as follows.

- Developed in Python, Flask, and Javascript.
- Three CRUD resources (User, Post, Comment).
- Several views (view all posts, view single post, create post, edit post).
- Bootstrap for responsive design.
- Unit and e2e test suite using pytest.
- Asynchronous Javascript to Create/Read/Update/Delete comments without reload.
- Asynchronous Javascript to Update post list without reload.
- Deployed to heroku.

I was responsible for the initial all posts view, the view for each individual post, and the comment system. I also implemented environment variables with python-dotenv, edited the SQL schema, and created the initial models. The most time-consuming portion was the comment code. Initially I implemented comments as templates that would be rerendered after each change, but that wasn't elegant. I re-implemented the system in Javascript from scratch, using the Flask routers to handle POST requests sent using the JS fetch() method, and then updating the DOM once a response was received. The end result looked and functioned nicely, although in future using a Javascript frontend framework would be preferable.

### What I Learned
I learned how to use Flask routers and Javascript to handle get and post requests. I learned how to do end-to-end testing and setup test schemas. I also learned a little about login systems and bcrypt. Of course, this was a group project, so I also gained experience working in a team. My team was pretty good, although communication could have been improved.

### Takeaways
This was a useful project that taught me a lot about modern web development. In future projects I'd like to work more with CI/CD principles, earlier and more frequent testing, login systems, and Javascript frameworks. It's tempting to begin coding right away, but especially in more complicated projects it's helpful to hash out all the deployment, relationships, and routing first.