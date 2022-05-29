---
layout: post
title:  Planning the Ticketing Site
date:   2022-05-29 11:04
categories: 
tags:   webdev software-eng
---
### Requirements
Company C wants a website with these requirements:
- Robust login system for 6-8 employees. Invite-only account creation.
- (?) password strength checking.
- Create and store job tickets, send a copy of ticket to manager's email.
- Store information resources in a way that allows them to be quickly accessed on-site. Stuff like site numbers, types of equipment at the site, and addresses.
- (?) send tickets directly into QuickBooks.
- (?) calendar and scheduling functionality for 6-8 employees.
- (?) map functionality to plan out travel times to locations.
- Admin dashboard to control account permissions, invite new users, see stored tickets, and control where tickets are sent after creation.
<p></p>
Cost is a factor, as this site is meant to save money, not introduce new costs. Regarding the potential calendar/planning function: the manager spends ~$30 monthly on a premium calendar service. Cloud costs should be kept below that limit if this feature is pursued. The site should be easy to update and manage, with no programming knowledge needed to add users or new content. Finally, the application should be easy to update and low-maintenance.

### Building the Tech Stack
#### Frontend
First decision is the front-end framework. This will be my first real project using a front-end javascript framework. I'll use Vue since the documentation is excellent, the learning curve is reasonable, and it came highly recommended by my 3155 professor. I did too much custom DOM manipulation in the last project and that's much better off left to a framework. 

Next up is the choice between static generated site or server-side ren. [This](https://www.smashingmagazine.com/2020/07/differences-static-generated-sites-server-side-rendered-apps/) article was helpful when researching the differences between statically generating and rendering an app on a server. Since this site will be doing potentially much more than serving some static pages, SSG is out. After reading [this](https://vuejs.org/guide/scaling-up/ssr.html) article on SSR, I've elected to pursue a single page application (SPA) with a backend API. The SEO problem with SPA isn't an issue, since this site will only be used internally. Plus, using an SPA  will give me flexibility to try out different backends during the learning process.

#### Backend
This may take a little longer to decide. I have experience using Flask and Heroku, but their free tiers aren't very reliable. 

Leaning towards Amazon EC2 for now, since that will give me experience setting up a bare-bones server. I could always start off using the Heroku I'm familiar with and then switch to something else later. Firebase is another good option that would eliminate the need for separate backend and hosting. Self-hosted is also an option. 

### Next Steps
1. Create Vue Application
2. Publish to internet
3. Link to backend
4. Setup authentication
5. Continue development