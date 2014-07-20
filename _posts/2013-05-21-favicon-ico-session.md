---
date: 2013-05-21 00:55:28+00:00
layout: post
title: favicon.ico 与 session 诡异的问题
categories:
- 技术生活
tags:
- PHP
---

今天在搭框架调试 session 时，发生了很诡异的问题。

具体就是：每次刷新页面的时候，除了 cookie 指定的 session 外，都会生成一个新的 session。

调试了半天，最后没办法了，拿出 Fiddler 看下请求情况，发现除了正常请求页面外，会请求到 favicon.ico 这个文件，试着访问下看看，妥.......汗颜啊，访问的是 PHP 页面，因为所有请求都被转到 PHP 中了，而且 favicon.ico 文件恰好不存在。

解释如下：

>nginx配置所有请求都会转发到index.php（单入口），当访问服务器上不存在的文件时也会转发到index.php，因为没有favicon.ico，而且页面HTML也没有请求favicon.ico，但是浏览器会自动访问，所以访问到PHP页面。  
>对于ico这种文件，浏览器不会把 cookie 发给服务器，所以 PH P就当没有设置过 session 一样，重新生成了一个。  
>这就导致了如上的问题。