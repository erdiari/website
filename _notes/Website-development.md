---
title: How did i setup this website using GitHub actions and obsidian
tags:
  - Web-Development
toc: true
comments: false
season: winter
---
--> This article still in WIP. Feel free to give me feedback

There is an indisputable force that pushes developers to open blog sites. There is a million way to do keep a blog site. Here is how i did it.

## Motivations
I am a sucker for tools that, allegedly, boost your productivity. Even so much as so that i can call it a hobby. So it would not be surprise that i found about obsidian. I hopped on to the hype train, i watched all the videos that implied they will teach me the ultimate ways of production and thought absolutely nothing. At the same time, i succumbed to the dark temptations of opening a blog site. So i have researched a way in to combining both and I can proudly say that i have found a way.
## Reasons
Well all the jokes aside, i have found that using Obsidian, Jekyll and github pages is an amazing way to host a blog site. Obsidian is a amazing tools to write markdown documents. Jekyll is a Static Site Generator. This is a way of saying that it takes [Markdown](https://daringfireball.net/projects/markdown/), [Liquid](https://github.com/Shopify/liquid/wiki), HTML and CSS files and generates multiples of html files with those files and template files. Github pages is a GitHub service to serve a part of a GitHub repository of static HTML files to web. Coincidentally it officially supports Jekyll. This means GitHub can take Markdown files, generates pure html and css using Jekyll then finally serve them.

So i write my blog sites using obsidian, push them to a GitHub repository. Then Github automatically generates HTML and CSS using Jekyll. Then serves them. Github Pages also support custom domains, so you can use it to host in your own domain as i do with mine. 

## Technical details
First step was to fork [note.link](https://github.com/Maxence-L/notenote.link), the obsidian optimized theme for Jekyll. Theme files in Jekyll are set of html template files. Difference between a template files and normal html is that template files have places specified with custom syntax. This places are populated with content from markdown files. For example, markdown file has a title attribute and template has a place for titles.The `note.link` is a fork of [simply-jekyll](https://github.com/raghudotcc/simply-jekyll) and it has obsidian specific features.

%% 
 ```html
<main>
	<h1>{{page.title}}</h1>
	{%- include content.html -%}
	<hr>
	{%- include backlinks.html -%}
	{%- include related.html -%}
</main>
```
%%
_actual code from_ [_layouts](https://github.com/Maxence-L/notenote.link/tree/master/_layouts)

The second step was to actually set up GitHub to create and host static html files. As is, the `note.link` isn't supported by GitHub pages. We have to change some files according to this [issue](https://github.com/Maxence-L/notenote.link/issues/5#issuecomment-762508069). 
Then we have to setup GitHub pages. To do that we have to find pages section at repository settings. We have to change deployment source from `deploy from branch` to  `GitHub Actions` . Then we are going select GitHub Pages Jekyll. (You can set your domain name in there too!)
![change](/assets/img/jekyll-github-pages.png)
This creates a sample config for Github Actions, GitHub's own CI/CD tool. Github actions, uses a special [YAML file](https://github.com/erdiari/website/blob/master/.github/workflows/jekyll-gh-pages.yml) to specify  which actions to do and when. This sample setup, builds Jekyll site when a commit is pushed to main branch and deploys it. I deemed it is enough for my own use case. 

Last step is setting up the obsidian to work with GitHub. First we create a empty vault. Then we are going to turn on community plugins and download [obsidian-git](https://github.com/denolehov/obsidian-git). It comes bundled with a git implementation called [isomorphic-git](https://isomorphic-git.org/) which uses pure JS, which means we can use git even thought there is no git installed at in our environment. This is necessary if we aim to use it with our phones. 
We have to  configure obsidian-git if we didn't have a working git setup in our system with proper authentication (like on our cellphones). You can do this in obsidian-git plugin settings by giving a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). 