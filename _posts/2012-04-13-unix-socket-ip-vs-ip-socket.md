---
date: 2012-04-13 01:18:16+00:00
layout: post
title: Unix Socket 与 IP Socket (TCP/IP) 的区别
categories:
- 技术生活
tags:
- Socket
- Unix
---

`Unix Socket`: 是同一台机器上不同进程间的通信机制。  
`IP Socket`: 是网络上不同主机之间进程的通讯机制，可以使得同一主机的不同进程通信。

以 Nginx 与 PHP 通讯为例：  

因为 TCP 四层协议，相当于 Nginx 这边是四层从上往下走，然后到 PHP 进程那边，四层协议从下往上走，然后 PHP 执行完脚本产生 HTML，把数据再在四层里从上往下走输送到 Nginx 这边，而等在这边的 Nginx 进程把那些数据又从下往上走，然后经过一系列处理，再在四层协议里去走一遍，这次是经过 eth0 接口返回浏览器了。  

单次请求，相当于单单 Nginx 与 PHP 之间，那四层协议的代码都走了4次。
如果高并发时，亿级请求时呢，要消耗多少内存、CPU和时间拖延啊？  

如果用 Unix Socket，当然没有那4层协议的 C 代码了，虽然说也是要用到系统调用的。  

简而言之，Unix Socket 就是不同进程间的通信机制。  

一般都可以用 Unix Socket 的，除非 Nginx 进程与 PHP 进程不在同一台机器上。