---
title: How did i setup this website using github actions and obsidian
tags:
  - Web-Development
toc: true
comments: true
---
There is an indisputable force that pushes developers to open blog sites. There is a million way to do keep a blog site. Here is how i did it.

## Motivations
I am a sucker for tools that, allegedly, boost your productivity. Even so much as so that i can call it a hobby. So it would not be surprise that i found about obsidian. I hopped on to the hype train, i watched all the videos that implied they will teach me the ultimate ways of production and thought absolutely nothing. At the same time, i succumbed to the dark temptations of opening a blog site. So i have researched a way in to combining both and I can proudly say that i have found a way.
## Reasons
Well all the jokes aside, i have found that using Obsidian, Jekyll and github pages is an amazing way to host a blog site. Obsidian is a amazing tools to write markdown documents. Jekyll is a Static Site Generator. This is a way of saying that it takes [Markdown](https://daringfireball.net/projects/markdown/), [Liquid](https://github.com/Shopify/liquid/wiki), HTML and CSS files and generates multiples of html files with those files and template files. Github pages is a GitHub service to serve a part of a GitHub repository of static HTML files to web. Coincidentally it officially supports Jekyll. This means GitHub can take Markdown files, generates pure html and css using Jekyll then finally serve them.

So i write my blog sites using obsidian, push them to a GitHub repository. Then Github automatically generates HTML and CSS using Jekyll. Then serves them. Github Pages also support custom domains, so you can use it to host in your own domain as i do with mine. 

## Technical details
This implementation --- 