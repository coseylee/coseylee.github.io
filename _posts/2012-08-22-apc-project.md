---
layout: post
title: 鸟哥带头维护 APC 项目
categories:
- 技术生活
tags:
- APC
- PECL
- PHP
---

今天在黑大的群中突然得知 PECL 其中的 APC 项目由鸟哥（Laruence, [http://www.laruence.com](http://www.laruence.com)）维护。忍不住，就上去看了一眼哈哈，还是lead呢。

{:.center}
[![image](/uploadfile/upload/thum-7ab49f4b28b2f81efdc0270bfd937fb620120822065940.png)](/uploadfile/upload/thum-7ab49f4b28b2f81efdc0270bfd937fb620120822065940.png)

项目地址：[http://pecl.php.net/package/apc](http://pecl.php.net/package/apc)

在这里也恭喜鸟哥了，顺便说下PECL和PEAR的区别:

`Pear`：是 PHP 的扩展代码包，所有的扩展均以PHP代码的形式出现，功能强大，安装简单，甚至可以改改就用。使用的时候，要在代码中进行Include才能够使用。  

`Pecl`：是 PHP 的标准扩展，可以补充实际开发中所需的功能，所有的扩展都需要安装，在Windows下面以Dll的形式出现，在linux下面，需要单独进行编译，它的表现形式为根据PHP官方的标准用C语言写成，尽管源码开放但是一般人无法随意更改源码。

最直接的表述：`Pear` 是PHP的上层扩展，`Pecl` 是PHP的底层扩展。