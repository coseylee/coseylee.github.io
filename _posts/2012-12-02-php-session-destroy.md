---
date: 2012-12-02 20:21:26+00:00
layout: post
title: 安全注销 PHP SESSION 会话
categories:
- 技术生活
tags:
- PHP
---

啥也不多说了，要完全删除 SESSION 会话，同时也要删除相关 COOKIE 及 SESSION 文件，才能完全保证彻底注销。

我们往往会直接使用：
{% highlight php %}
<?php
setcookie(session_name(), ’’, time() - 42000)
{% endhighlight %}

也能实现注销 COOKIE，但是升级到 5.3/5.4 以后，以及 IE 可能会清除 COOKIE 不够彻底，如果要安全的、完整的注销 SESSION，可以使用：

{% highlight php %}
<?php
$params = session_get_cookie_params();
setcookie(session_name(), ’’, time() - 42000, $params[’path’], $params[’domain’], $params[’secure’], $params[’httponly’]);
{% endhighlight %}