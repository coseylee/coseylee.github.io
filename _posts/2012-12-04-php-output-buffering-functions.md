---
date: 2012-12-04 09:40:52+00:00
layout: post
title: PHP 输出缓存及 output buffering 函数说明
wordpress_id: 126
categories:
- 技术生活
tags:
- PHP
---

正常情况下从 PHP 到浏览器的缓存依次有 `php buffer -> server buffer -> browser buffer`。  

而 `ob_` 系列函数正是操作 `php buffer`，`flush()` 则是操作 `server buffer`。

{% highlight php %}
<?php
flush() // 将server buffer中的内容发送到浏览器上。
ob_start() // 开启php buffer，所有输出将缓存到php buffer。
ob_flush() // 将php buffer放入server buffer。
ob_end_flush() // 同上唯一区别是ob_end_系列在使用后会关闭php buffer。
ob_get_flush() // 将php buffer数据返回，不输出，并关闭php buffer。
ob_clean() // 将php buffer清空。
ob_end_clean() // 同上，将php buffer清空，并关闭php buffer。
ob_get_clean() // 将php buffer数据返回，并将php buffer清空后关闭。
ob_get_contents() // 将php buffer数据返回。
{% endhighlight %}

另外还有一点就是当从 `buffer` 中将数据拿出并送出后，`buffer` 中的内容就会被删除，所以要取得 `buffer` 中的内容，要在强制输出之前进行。  
比如 `ob_get_contents()` 要在 `ob_flush()` 之前进行，否则取不到数据。