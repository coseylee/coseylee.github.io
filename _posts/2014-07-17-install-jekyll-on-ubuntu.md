---
layout: post
date: 2014-07-17
title: 在 Ubuntu 上安装 Jekyll 小记
categories: 技术
tag: ubuntu jekyll
---

这两天打算把之前注销的GitHub帐号重新启用，用来写博客用。  
GitHub Pages 使用的是 Jekyll 引擎解析，在本地安装上可以调试预览页面效果。

**大概安装步骤**

1. 安装 RVM。
2. 使用 RVM 安装 Ruby。
3. 用 RubyGems 安装 Jekyll。

**1、安装 RVM**

`curl -L https://get.rvm.io | bash -s stable`

**2、使用 RVM 安装 Ruby**

`rvm install 1.9.3 # 安装1.9.3版本`  
`rvm 1.9.3 --default # 设置为默认版本`

**3、用 RubyGems 安装 Jekyll**

`gem install jekyll`

***

>如果运行 Jekyll 时报错的话，可以尝试安装下面的包：  
>`gem install execjs`  
>`gem install therubyracer`  
>`sudo apt-get install nodejs`
