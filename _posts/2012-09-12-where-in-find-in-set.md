---
layout: post
title: 逗号分割字符的麻烦，记 WHERE IN 与 FIND_IN_SET
categories:
- 技术生活
tags:
- MySQL
---

A表ID为1的ids字段值为'1,2,3'。

B表中存有3条记录，ID分别是1、2、3。

本想使用下列语句查询出B表中的三条记录。

{% highlight sql %}
SELECT * FROM `table_a` WHERE `id` IN (SELECT `ids` FROM `table_b` WHERE `id` = 1);
{% endhighlight %}

结果却出乎意料，在群里吼了一下，大概是明白了，A表ID为1的ids字段只会被认为是`WHERE IN`中的一个值而已，并不是我所认为的1,2,3三个值。

换句话说它等于下面这个语句。

{% highlight sql %}
SELECT * FROM `table_a` WHERE `id` IN ('1,2,3');
{% endhighlight %}

而并不是我预想的下面这样。

{% highlight sql %}
SELECT * FROM `table_a` WHERE `id` IN ('1', '2', '3');
{% endhighlight %}

比较上面两条语句，就会发现问题了。  
那么该如何解决呢？

{% highlight sql %}
SELECT * FROM `table_a` WHERE FIND_IN_SET(`id`, (SELECT `ids` FROM `table_b` WHERE `id` = 1));
{% endhighlight %}

可以使用`FIND_IN_SET`来解决这个问题。  

