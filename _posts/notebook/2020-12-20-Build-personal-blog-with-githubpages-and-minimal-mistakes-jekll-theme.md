---
categories: Notebook
layout: single
classes: wide
title: Build personal blog with Github Pages and minimal-mistakes-jekll theme
---

# !!!Usage limits of GitHub Pages

<https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/about-github-pages>

GitHub Pages sites are subject to the following usage limits:

- GitHub Pages source repositories have a recommended limit of 1GB.

- Published GitHub Pages sites may be no larger than 1 GB.

- GitHub Pages sites have a soft bandwidth limit of 100GB per month.

- GitHub Pages sites have a soft limit of 10 builds per hour.

# 1.Create a Github Pages repository.

## 1.1.Offilal guide
<https://pages.github.com>

## 1.2.Create a repository.

Head over to GitHub(<https://github.com/>) and create a new repository named username.github.io, where username is your username (or organization name) on GitHub.


If the first part of the repository doesn’t exactly match your username, it won’t work, so make sure to get it right.
It's unnecessary to configure other options.

![CreateRepository](https://pengfei-zheng.github.io/assets/images/notebook/CreateRepository.png)

## 1.3.Clone the repository to local.

# 2.Download and use minimal-mistakes jekll theme.

## 2.1.Download minimal-mistakes
Download the release version of Minimal-mistakes(<https://github.com/mmistakes/minimal-mistakes>). 

## 2.2.Extract files to local
Extract the files into your repository and replace the files with same name.

## 2.3.Remove some folders and files.

`rm -r .editorconfig .gitattrib utes .github docs test CHANGELOG.md minimal-mistakes-jekyll.gemspec README.md screensh ot-layouts.png screenshot.png index.md`

# 3.Start edit your personal blog.

## 3.1.Minimal-mistakes official quick start guide.
<https://mmistakes.github.io/minimal-mistakes/docs/configuration/>

## 3.2.Change favicon.
What is favicon?

![favicon](https://pengfei-zheng.github.io/assets/images/notebook/favicon.png)

Convert a picture to ico. Then put it into `assets/images/` or other folder that you like. Rename the picture as 'favicon.ico' or other name you like.

Add the following code into  `_include/head/custom.html`. Please note the name of ico file.

`<link rel="shortcut icon" href="/assets/images/favicon.ico">`

# 4.Commit and push your code to GitHub.

# 5.Visit your own website.

The url of website is `https://username.github.io`, for example <https://pengfei-zheng.github.io>
