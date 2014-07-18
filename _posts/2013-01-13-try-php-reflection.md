---
layout: post
title: PHP 中反射（Reflection）简单记录
categories:
- 技术生活
tags:
- PHP
---

最近在项目（基于CodeIgniter）中，需要对控制器中的方法做自定义的访问控制，简单来说只允许访问控制器中存在并且属性为 public 的方法。

使用PHP内置的反射类就很好的解决问题。

{% highlight php %}
<?php
$rc = new ReflectionClass($this);
if ($rc -> hasMethod($this -> action))
{
    $rm = new ReflectionMethod($this, $this -> action);
    if (!$rm -> isPublic())
    {
        $this -> output('error', '404');
    }
}
else
{
    $this -> output('error', '404');
}
{% endhighlight %}