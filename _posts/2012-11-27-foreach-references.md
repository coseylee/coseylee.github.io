---
layout: post
title: Foreach 引用遍历时要小心！
categories:
- 技术生活
tags:
- PHP
---

关于 PHP 中 Foreach 中的一个小坑。

{% highlight php %}
<?php
$arr = array(1, 2, 3);
foreach ($arr as &$v) { somecode.... }
foreach ($arr as  $v) { somecode.... }
print_r($arr);
{% endhighlight %}

我们期待的结果是：

{% highlight php %}
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
)
{% endhighlight %}

而实际结果却是：

{% highlight php %}
Array
(
    [0] => 1
    [1] => 2
    [2] => 2
)
{% endhighlight %}

原因分析：

1. 当一次遍历时，因为使用地址引用传值，所以遍历结束时，$val 指向的是 $arr 最后一个元素 $arr[2]，此时 $arr 并没有变化。  
2. 而当第二次遍历时，再向 $val 赋值时，由于 $val 已指向 $arr[2]，所以 $arr[2] 也随 $val 改变而改变。  
3. 当第二段代码执行第二次的时候，$arr[2] 为2，所以第三次再执行的时候，相当于给 $arr[2] 赋值它自己，$arr[2] = $arr[2]，最后的结果就是 $arr[2] 为2。