---
date: 2012-11-08 09:23:44+00:00
layout: post
title: 'Nginx 出现 11: Resource temporarily unavailable 解决方法'
categories:
- 技术生活
tags:
- PHP
- Nginx
---

因为我的开发环境在ubuntu上，然后使用samba共享文件夹，但是在Windows下修改文件后，会发现第一次访问Nginx会出现500错误。 

>"xxxx.js" failed (11: Resource temporarily unavailable), client: 192.168.88.2, server: xxx, request: "GET xxxx.js HTTP/1.1", host: "shop.cn", referrer: "http://xxxxx.com"

在网上找了一下解决方法，有的说是PHP-FPM的问题，有的说的是Nginx的问题，其实是 Samba 的问题，只要在 Samba 配置文件中加入这两个选项。  

>oplocks = no level2  
>oplocks = no

即可解决问题。  

这回再修改文件，终于不用再刷新两次了。