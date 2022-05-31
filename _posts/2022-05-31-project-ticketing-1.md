---
layout: post
title:  Ticketing Site Part 1
date:   2022-05-31
tags:   project-ticketing-site
categories: 
---
### Introduction
I'll be setting up the backend first, since I already have Flask and Heroku experience. Additionally, since the data-storage portion of the site is its primary function, it makes sense to setup that element first. Users need a way to store, send, and retrieve data.

I'll be following [this guide](https://testdriven.io/blog/developing-a-single-page-app-with-flask-and-vuejs/) to set up a sample app first, so that I can familiarize myself with the process of linking Flask and Vue.

I followed the Flask setup portion without issue, creating the venv, building a basic app, and creating a basic route to ping. I pushed the new backend to **loganagol/flask-vue-crud**. 

Vue installation was slightly more involved. Running 
`npm install -g @vue/cli@latest`
caused several EACCES permission errors. I had previously installed Node from source since the version in the Ubuntu repositories was outdated, but my configuration was evidently not working properly. I followed [this](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) and installed nvm. I restarted and the errors remained. Checking my .bashrc file, my environment variables seemed to be set correctly.

`export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion`

...

After an hour of troubleshooting, it looks like I may need to completely remove npm and node and reinstall. I checked my bash history and discovered some things. When I installed Node and NPM for class on 4/13/2022 it looks like I followed option 2 in [this](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04) guide and installed from the NodeSource PPA since the official PPA was outdated. 

`1218  curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
1219  sudo apt-get install -y nodejs`