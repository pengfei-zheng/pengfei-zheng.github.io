---
categories: Notebook
title: Build personal blog with Github Pages and minimal-mistakes-jekll theme
toc: true
---

# 1.Create a Github Pages repository.

**Offilal guide: https://pages.github.com/**

## 1.1.Create a repository.

Head over to GitHub(https://github.com/) and create a new repository named username.github.io, where username is your username (or organization name) on GitHub.


If the first part of the repository doesn’t exactly match your username, it won’t work, so make sure to get it right.
It's unnecessary to configure other options.

![CreateRepository](https://pengfei-zheng.github.io/assets/images/notebook/CreateRepository.png)

## 1.2.Clone the repository to local.

# 2.Download and use minimal-mistakes jekll theme.

Download the release version of Minimal-mistakes(https://github.com/mmistakes/minimal-mistakes). Extract the file into your repository and replace the some file with same name.

Remove some folders and files.

`rm -r .editorconfig .gitattrib utes .github docs test CHANGELOG.md minimal-mistakes-jekyll.gemspec README.md screensh ot-layouts.png screenshot.png index.md`

# 3.Start edit your personal blog.

## 3.1.Minimal-mistakes official quick start guide.
https://mmistakes.github.io/minimal-mistakes/docs/configuration/

## 3.2.Change favicon.
What is favicon?

![favicon](https://pengfei-zheng.github.io/assets/images/notebook/favicon.png)

Convert a picture to ico. Then put it into `assets/images/` or other folder that you like. Rename the picture as 'favicon.ico' or other name you like.

Add the following code into  `_include/head/custom.html`. Please note the name of ico file.

`<link rel="shortcut icon" href="/assets/images/favicon.ico">`

# 4.Commit and push your code to GitHub.

# 5.Visit your own website.

The url of website is https://username.github.io, for example https://pengfei-zheng.github.io
