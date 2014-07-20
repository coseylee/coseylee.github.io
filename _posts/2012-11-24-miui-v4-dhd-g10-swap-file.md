---
date: 2012-11-24 00:06:08+00:00
layout: post
title: MIUI v4 DHD(G10) Android 开启 Swap 方法
categories:
- 纯属爱好
tags:
- Android
---

大概的原理就是在机身内存上建立 SWAP 文件，作为交换内存。

下面是实现方法，我就简单记录一下，具体的细节，自行谷歌。

首先使用 ADB 连接到设备上，当然 ROOT 权限不用说了。  
由于是占用机身内存，所以也要保证，机身内存上有足够的空间。  
MIUI 上本身有 busybox 工具，所以就不用安装了。

执行命令：
{% highlight bash %}
busybox dd if=/dev/zero of=/data/local/swap bs=1M count=128
busybox mkswap /data/local/swap
busybox swapon /data/local/swap
{% endhighlight %}

这样就建立了大小为128M的 SWAP 文件。
再执行命令以下命令，检查是否生效了。

{% highlight bash %}
cat /proc/meminfo
{% endhighlight %}

如果看到以下项的值不为空，就对了。

[![点击查看原图](/uploadfile/201211/d5f91bf6fed64692961a13b81b6df1a220121123162630.png)](/uploadfile/201211/d5f91bf6fed64692961a13b81b6df1a220121123162630.png)

为了每次开机都能自动挂载，需要加入自启动脚本。
{% highlight bash %}
#!/system/bin/sh

if [ ! -e "/data/local/swap" ]
then
    busybox dd if=/dev/zero of=/data/local/swap bs=1M count=128
    busybox mkswap /data/local/swap
    busybox swapon /data/local/swap
else
    busybox swapon /data/local/swap
fi
{% endhighlight %}

将以上代码保存为 01swap，放入/system/etc/init.d/下面，修改用户为root，权限644，即可。