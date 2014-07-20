---
date: 2012-04-12 09:56:54+00:00
layout: post
title: Python Web 开发名词解释
excerpt: Python 在 Web 开发中的名词解释
categories:
- 技术生活
tags:
- Python
---

**Nginx/Apache/Lighttpd**:

>相当于一个 Request Proxy，根据配置，把不同的请求转发给不同的 Server 处理，例如静态的文件请求自己处理，这个时候它就像一个 Web Server，对于动态页面这样的请求转发给 Flup 这样的 Server/Gateway 进行处理。

**Flup**

>一个用 Python 写的 Web Server，也就是 CGI 中所谓的 Server/Gateway，它负责接收 Nginx/Apache/Lighttpd 等转发的请求，并调用你写的程序 (Application)，并将 Application 处理的结果返回到 Nginx/Apache/Lighttpd 再输出到浏览器中。

**FastCGI**

>Web Server 的一个模块，虽然 Flup 可以作为一个独立的 Web Server 使用，但是对于浏览器请求处理一般都交给 Nginx/Apache/Lighttpd 处理，然后由 Nginx/Apache/Lighttpd 转发给 Flup 处理，这样就需要一个东西来把 Nginx/Apache/Lighttpd 跟 Flup 联系起来，这个东西就是 FastCGI 协议。

**web.py**

>应该说有了上面的东西你就可以开始编写你的web程序了，但是问题是你就要自己处理浏览器的输入输出，还有cookie、session、模板等各种各样的问题了，web.py 的作用就是帮你把这些工作都做好了，它就是所谓的 Web Framework，另外一个出名的是 Django，不过感觉太复杂了，web.py 差不多就够用了。

**WSGI**

>除了 Flup 外还有很多其他人的写的 Server/Gateway, 这个时候就会出问题了，如果你在 Flup 上写了一个程序，现在由于各种原因你要使用 xdly 了，这个时候你的程序也许就要做很多痛苦的修改才能使用 xdly server 了，WSGI 就是一个规范，他规范了 Flup 这个服务应该怎么写，应该使用什么方式什么参数调用你写的程序(Application)等，当然同时也规范你的程序应该怎么写了，这样的话，只要都遵守 WSGI 的话，你的程序在两个上面都可以使用了，Flup 就是一个 WSGI Server。

