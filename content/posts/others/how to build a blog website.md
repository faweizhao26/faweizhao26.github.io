---
title: "利用 GitHub 和 Hugo 免费搭建博客平台"
date: 2022-07-24T15:01:29+08:00
categories: 
- 其他
tags: 
- hugo
- GitHub
description: ""
weight: # 输入1可以顶置文章，用来给文章展示排序，不填就默认按时间排序
draft: false 
comments: true
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: false # 底部不显示分享栏
showbreadcrumbs: true #顶部显示当前路径
cover:
    image: ""
    caption: ""
    alt: ""
    relative: false
---

本篇文章将以 Mac 为例，教你如何利用 GitHub 和 Hugo 来免费搭建一个用于写博客的平台。不过本文只是初级教程。

## GitHub 和 Hugo 简介

### GitHub 简介

GitHub 是一个面向开源及私有软件项目的托管平台，提供了 Git 的分布式版本控制和源代码管理功能。

### Hugo 简介

Hugo（雨果）是一个开源的用于静态网站构建的框架，拥有 300 多款主题。Hugo 站点可以托管在 GitHub Pages、 Netlify、Heroku、GoDaddy、DreamHost 等地方，无需数据库，也不需要依赖昂贵的运行时（Ruby、Python、PHP 等）。

官网地址： https://gohugo.io/

GitHub 地址： https://github.com/gohugoio/hugo

所以，基于以上，我们可以利用这两个工具，来搭建一个博客平台。

## 前提条件

在正式开始搭建前，你需要做以下两点：
- 注册一个 GitHub 账号
- 在电脑上安装 Hugo（可在网上搜索教程）
- git 配置（可在网上搜索教程）


## 搭建步骤

### 用 Hugo 生成博客

 1. 打开 Mac 自带的终端，输入以下命令：
 
 ```
 hugo new site myblog
 ```
 
 myblog 为生成的本地博客文件夹名称，可自定义，如 blog。
 
 2. 找到博客路径

博客文件夹的路径默认为 /Users/zhaofawei/myblog，可在 Mac 本地打开，看到文件夹的各个文件夹和文件，主要为：content（内容）、theme（主题）、config.toml（配置）等等。

3. 在终端输入以下命令，到博客文件夹下

```
cd /Users/zhaofawei/myblog
```

### 下载并设置主题

1. 首先在 Hugo 主题官网找一款喜欢的主题

Hugo 主题官网： https://themes.gohugo.io/

我选的是 PaperMod 这款主题，以此主题为例。

2. 下载主题

在终端输入以下命令：

```
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```

每个主题页面都有该主题下载的命令，可直接复制到终端。

如果想知道有没有下成功，最“傻瓜”的方式，就是到 Mac 本地的 myblog 文件夹的子文件夹 theme 里看下是否有文件，如果有则表明下载成功。

3. 配置 config.toml

配置博客主题，可在网上搜索更详细的教程，我也是如此做的，而且对这块也是一知半解，就不贻笑大方了。

此配置非常重要，涉及到你的博客页面的美观、页面信息等多方面的东西。

### 在本地启动博客

1. 首先在本地创建一篇博客

在终端输入以下命令创建一篇博客：

```
hugo new posts/blog.md
```

posts 为 content 文件夹内的博客文件夹，blog 为博客名（可自定义）。

也可以直接在 posts 文件夹内创建一个 md 文件，然后将相应的内容填写进去。博客的样式，如摘要、目录、时间显示等等都与主题配置有关，需要提前设置好。

2. 本地预览

```
hugo server
```

在浏览器打开以下链接即可预览： http://localhost:1313/。

### 将个人博客部署到 GitHub

1. 首先在 GitHub 新建一个仓库

仓库名称与你的昵称前缀完全相同。

举例来说，我的个人 GitHub 地址是：https://github.com/faweizhao26，所以昵称就是 faweizhao26，那么新建的仓库名称也必须是 faweizhao26.github.io。

创建时，其他可默认，设置好仓库名称即可点击创建按钮。

该仓库的路径为：https://github.com/faweizhao26/faweizhao26.github.io，不过目前还是一个空的仓库。

2. 生成 public 文件

注意：如果你目前终端的路径不在博客根目录，需要先回到根目录。

然后，在终端输入以下命令，将本地博客部署到 GitHub。

```
hugo --theme=PaperMod --baseUrl="https://faweizhao26.github.io/" --buildDrafts
```
> 里面的路径和主题可替换成你自己的。

执行后，站点根目录下会生成一个 public 文件夹，该文件下的内容即 Hugo 生成的整个静态网站。每次更新内容后，将 pubilc 目录里所有文件 push到 GitHub 即可。

> 此外，该命令可简化为：
> `hugo`

3. 推到 GitHub

依次执行如下步骤：

转到 public 文件夹下：

```
cd /Users/zhaofawei/myblog/public
```

初始化 Git 库：

```
git init 
```

添加刚刚新增的内容：

```
git add . 
```

查看新增的内容（该步骤可省略）：

```
git status
```

填写 commit 信息：

```
git commit -m "new blog"
```

连接 GitHub：

```
git remote add origin https://github.com/faweizhao26/faweizhao26.github.io.git
```

推到远程仓库：

```
git push -u origin master
```

执行完上述命令，你的内容即可推到 GitHub 上，那么这时候博客网站就生成了，地址为：https://faweizhao26.github.io/。那么你的博客网站地址则为：https://yourname.github.io/。

这时候打开，就能看到你添加的那篇博客了。

如果在执行上述最后一条命令时失败了，可输入以下命令强制提交：

```
git push -f origin master
```

以上就是搭建博客网站的基本步骤。

## 更新博客

1. 在本地删除 public 文件夹

2. posts 文件夹下添加新的内容

3. 用 hugo 命令生成新的 public 文件夹

4. 按照上述推到远端的步骤执行即可

> 我的博客网站添加了评论系统，您只需要使用 GitHub 账号登录即可留言评论。我目前做着开源社区的运营工作，不敢说自己多专业，但非常欢迎您加我好友交流讨论，我的微信：zhaofawei26。