---
date: 2011-06-28 09:40:53+00:00
layout: post
title: 猪八戒 Flash 上传组件 Auntion 作品
categories:
- 技术生活
---

猪八戒 大牛 Auntion 的作品

{:.center}
[![1](/uploadfile/201107/thum-f3f508b6880b901b00e3aa91dd4fa5d520110718120917.jpg)](/uploadfile/201107/thum-f3f508b6880b901b00e3aa91dd4fa5d520110718120917.jpg)

HTML 代码:
{% highlight html %}
<div id="upload" class="mt10">
<div id="at_uploadbutton">
    <!--insertUploadButton-->
    <span id="at_upload_exp_span" style="position:relative;z-index:1;left:12px;top:5px;*top:2px">最多可添加五个附件，每个大小不超过10MB。<a href="http://help.zhubajie.com/568.html" kesrc="http://help.zhubajie.com/568.html" target="_blank">无法正常上传?</a></span></div>
    <div id="at_upload">
        <input type="hidden" name="files" id="files"/>
        <!--储存要使用的附件-->
    </div>
    <div id="number"></div>
</div>
{% endhighlight %}

Javascript:
{% highlight javascript %}
/* 使用上传组件 */
var uploadFileApply = new at_upload("/assets/button.swf", ’/post/upload’, $("#at_uploadbutton").get(0));
uploadFileApply.onError = function(index, msg)
{
    at_infoTrace.show(msg, "e");
}
{% endhighlight %}

[源码下载](/uploadfile/201107/04844605ca0c6250c1756ced2a730f1b20110718114458.zip)