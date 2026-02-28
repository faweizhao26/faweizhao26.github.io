---
title: "Build a Free Blog with GitHub and Hugo"
date: 2022-07-24T15:01:29+08:00
categories:
- Life
tags:
- hugo
- GitHub
description: ""
weight: # Set to 1 to pin this post; leave empty to sort by date.
draft: false
comments: true
showToc: true
TocOpen: true
hidemeta: false
disableShare: false
showbreadcrumbs: true
cover:
    image: ""
    caption: ""
    alt: ""
    relative: false
---

This post uses macOS as an example and shows how to build a free blog with GitHub and Hugo. It is a beginner-level tutorial.

## GitHub and Hugo basics

### GitHub

GitHub is a hosting platform for open-source and private software projects. It provides distributed version control with Git and source code management.

### Hugo

Hugo is an open-source static-site generator with 300+ themes. Hugo sites can be hosted on GitHub Pages, Netlify, Heroku, GoDaddy, DreamHost, and more. No database or expensive runtime (Ruby, Python, PHP) is required.

Official site: https://gohugo.io/

GitHub repo: https://github.com/gohugoio/hugo

With these two tools, you can build a blog.

## Prerequisites

Before starting, you need:
- a GitHub account
- Hugo installed on your computer (search online for tutorials)
- git configured (search online for tutorials)

## Steps

### Generate a site with Hugo

1. Open the macOS Terminal and run:

```
hugo new site myblog
```

`myblog` is your local folder name. You can change it, for example `blog`.

2. Find the blog path

By default the folder is `/Users/zhaofawei/myblog`. Open it and you will see folders like `content`, `theme`, `config.toml`, and so on.

3. Enter the folder in Terminal:

```
cd /Users/zhaofawei/myblog
```

### Download and set a theme

1. Choose a theme on the Hugo theme site

Hugo themes: https://themes.gohugo.io/

I chose PaperMod as an example.

2. Download the theme

In Terminal:

```
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```

Each theme page provides a download command you can copy.

To verify, check that the theme folder exists under `theme`.

3. Configure `config.toml`

Theme configuration controls page appearance and metadata. You can search for tutorials; I also did so and am not an expert.

### Run the site locally

1. Create a post

In Terminal:

```
hugo new posts/blog.md
```

`posts` is the folder under `content`, and `blog` is the post name.

You can also create an `.md` file manually and fill in content. Post style (summary, TOC, timestamps) depends on theme configuration.

2. Preview locally

```
hugo server
```

Open http://localhost:1313/ in your browser.

### Deploy to GitHub

1. Create a repository on GitHub

The repository name must match your username exactly, with `.github.io` appended.

Example: my GitHub profile is https://github.com/faweizhao26, so the repository must be `faweizhao26.github.io`.

Create it with default settings.

Repository URL: https://github.com/faweizhao26/faweizhao26.github.io (initially empty).

2. Generate the public folder

Make sure your terminal is at the site root, then run:

```
hugo --theme=PaperMod --baseUrl="https://faweizhao26.github.io/" --buildDrafts
```

> Replace the URL and theme with your own.

This generates a `public` folder containing the entire static site. After each update, push the `public` folder to GitHub.

> This command can be simplified to:
> `hugo`

3. Push to GitHub

Run the following steps:

Go into the public folder:

```
cd /Users/zhaofawei/myblog/public
```

Initialize git:

```
git init
```

Add files:

```
git add .
```

(Optional) check status:

```
git status
```

Commit:

```
git commit -m "new blog"
```

Connect to GitHub:

```
git remote add origin https://github.com/faweizhao26/faweizhao26.github.io.git
```

Push:

```
git push -u origin master
```

After these steps, your site will be live at https://faweizhao26.github.io/ (replace with your own username).

If the last command fails, you can force push:

```
git push -f origin master
```

That is the basic setup.

## Update the blog

1. Delete the `public` folder locally
2. Add new content under `posts`
3. Run `hugo` to generate a new `public` folder
4. Push again using the steps above

> There is a comment system on this blog. You can log in with your GitHub account to leave a comment. I work in open-source community operations. I am far from an expert, but I would love to connect and discuss. My WeChat ID: zhaofawei26.
