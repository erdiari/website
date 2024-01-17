---
title: How did i setup this website using GitHub actions and obsidian
tags:
  - Web-Development
toc: false
comments: true
season: winter
---
This post is still work in progress please give me feedback.

I wanted to start blogging. There is a million ways why like how there is a million way how. Why is unimportant let's look at how.
## Motivations
I have little obsession for programs that, allegedly, boost your productivity. Even so much as so, that i can call it my hobby. A significant portion of my life spent watching Youtube videos of different methods and tools that allegedly would make life whole better. So it was only matter of time that i have met obsidian. At the same time, i succumbed to the dark temptations of opening a blog site. So i have researched a way in to combining both and I can proudly say that i have found a way.
## Reasons
Well all the things aside, i have found that using Obsidian, Jekyll and Github pages is an amazing way to host a blog site. Obsidian is a amazing tools to write markdown documents. I also use it daily to take structured notes (For unstructured notes, i sue LogSeq. Go look it up, it is amazing). Jekyll is a Static Site Generator. This is technical way of saying that it takes [Markdown](https://daringfireball.net/projects/markdown/), [Liquid](https://github.com/Shopify/liquid/wiki), HTML and CSS files and generates multiples of html files with those files and template files. Github pages -- free the static website hosting of Github, supports jekyll out of the box. 

So i write my blog sites using obsidian, push them to a GitHub repository. Then Github automatically generates HTML and CSS using Jekyll to serves them using Github Pages. Pages also support custom domains, so you can use it to host in your own domain as i do with mine. 

## Technical details
First step was to fork [note.link](https://github.com/Maxence-L/notenote.link), the obsidian optimized theme for Jekyll. Theme files in Jekyll are set of html template files. Difference between a template files and normal html is that template files have places specified with custom syntax. This places are populated with content from markdown files. For example, markdown file has a title attribute and template has a place for titles.The `note.link` is a fork of [simply-jekyll](https://github.com/raghudotcc/simply-jekyll) and it has obsidian specific features.

The second step was to actually set up GitHub to create and host static html files. To do that, first of all, we have solve a little caveat. As is, the `note.link` uses `jekyll-toc module` which isn't supported by GitHub pages. We have to go and manually edit some files like mentioned in this [Github issue](https://github.com/Maxence-L/notenote.link/issues/5#issuecomment-762508069). 

Next step is to setup GitHub pages. To do that we have to find pages section at repository settings. We have to change deployment source from `deploy from branch` to  `GitHub Actions` . Then we are going select GitHub Pages Jekyll. (You can set your domain name in there too!)

![change](/assets/img/jekyll-github-pages.png)

This creates a sample config for Github Actions, GitHub's own CI/CD tool. Github actions, uses a special [YAML file](https://github.com/erdiari/website/blob/master/.github/workflows/jekyll-gh-pages.yml) to specify  which actions to do and when. This sample setup, builds Jekyll site when a commit is pushed to main branch and deploys it. I deemed it is enough for my own use case. 

Last step is setting up the obsidian to work with GitHub. First we create a empty vault. Then we are going to turn on community plugins and download [obsidian-git](https://github.com/denolehov/obsidian-git). It comes bundled with a git implementation called [isomorphic-git](https://isomorphic-git.org/) which uses pure JS, which means we can use git even thought there is no git installed at in our environment. We could also use built-in git of our system but if we aim to write anything with our mobile devices it is a necessary step. 

We have to  configure obsidian-git if we didn't have a working git setup in our system with proper authentication (like on our cellphones). You can do this in obsidian-git plugin settings by giving a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). 

Lastly i hated how crowded my sidebar is. So in my desktop, i have linked notes and asset folder to my everyday obsidian vault. I will not get in to detail as it can only be done in linux (Yes, i use arch btw). I believe everyone who reads this and using linux as a daily driver will be more than component enough to link a folder to another folder. 