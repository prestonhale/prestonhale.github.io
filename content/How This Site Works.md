---
title: How This Site Works
---
This site is powered by three git repos.

### A [[https://github.com/jackyzha0/quartz|Quartz]] Fork

https://github.com/prestonhale/quartz

This is basically a straight fork of Quartz with a small modification to the docker file to allow custom arguments to be passed in. When the repo is pushed it builds that docker container and submits the container to the Github Container Repo. This repo will only need changes to keep it up to date with the Quartz mainline or to make changes to the Dockerfile used to build this Quartz site.

Note: There's a really janky hack where any page with the slug "index" uses the "recentNotesPage" layout. This only works for me, because I want the index page to be recent notes, but would absolutely break Quartz generally. A better solution would be to use a page tag to override the layout. E.g. `override_layout=recentPageLayout`.

### The Public Github Pages Repo

https://github.com/prestonhale/prestonhale.github.io

Where the content that is used to generate this very Quartz site is held. This site is a Github Pages site built from this repo. Except for updating the the Github Actions Workflows this repo should never need to be manually committed to.

### A private obsidian vault 
This one has no link because its private. 

I wanted a private repo for this to be able to commit work in progress pages and keep a truly private vault. It was also important to me that when I finally do submit to public the messy commit history (possibly including my rejected/changed/typo-ridden first drafts) doesn't appear in the public repo. At the same time I wanted to be able to keep a commit history for the public repo to see the changes over time to the site. 

When commits are merged to the `public` branch of this repo it triggers the Github Actions workflow on the public repo. The public repo then checks out both repos, syncs from the private repo to the public repo, builds and deploys the site, then automatically commits the new changes back to the public repo. The commit history (and indeed the .git folder) of the private repo is never shared with the public repo.

ToDo
- There's a lot of copying in the build process. From the private to the public repo and then from the public repo to the build dir that the image uses. Its definitely possible to just bbuild from the public repo checkout