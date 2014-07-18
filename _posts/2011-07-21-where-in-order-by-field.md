---
layout: post
title: WHERE IN ... ORDER BY FIELD ...
categories:
- 技术生活
tags:
- MySQL
- PHP
- SQL
---

刚在 PPC 上看到一个提问，我感觉用下面的语句会靠谱些儿吧。。。就是对 WHERE IN 进行排序。  

问题地址：[http://bbs.phpchina.com/thread-219422-1-2.html](http://bbs.phpchina.com/thread-219422-1-2.html)

{% highlight sql %}
SELECT `id` FROM `db_table` WHERE `id` IN (5, 3, 6, 2, 1) ORDER BY FIELD (`id`, 5, 3, 6, 2, 1);
{% endhighlight %}

查询结果会按照5, 3, 6, 2, 1 进行排序。