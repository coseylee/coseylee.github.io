---
date: 2013-06-08 17:51:40+00:00
layout: post
title: Phar 与 Suhosin (Debian)
categories:
- 技术生活
tags:
- Phar
---

由于项目需要，核心框架文件用 Phar 打包，在本地测试没有任何问题，到了测试环境却一片空白，没有任何输出、也没有错误记录。

一开始怀疑 PHP 不支持 Phar，但是使用的 PHP 版本的确是 5.3，然后又怀疑是Apache，然而解析 Phar 应该不需要Apache参与的。

找了大半天问题出在哪里，结果在phpinfo()里看到“suhosin”，会不会是它呢？结果一查，果然如此。

解决方法很简单：

>// suhosin.ini  
>suhosin.executor.include.whitelist = phar