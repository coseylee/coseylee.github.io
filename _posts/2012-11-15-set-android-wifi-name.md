---
layout: post
title: Android 修改 WiFi 设备名称
categories:
- 纯属爱好
tags:
- Android
---

Android 设备默认设备名是android-xxxxxx格式的，在路由里就能看到。当手机过多的时候无法区分设备，所以找了方法，修改wifi设备名。

首先下载“脚本管理器”，进入/system/bin中，找到setprop，打开，第二行写入“net.hostname xxxxx”， xxxxx就是想要设备的名称，再点击上面的五个图标中的su、boot、net，再点保存，重启手机生效。

{:.center}
[![点击查看原图](/uploadfile/201211/615545ae92cff126d3d4b3b8ea0b60d820121115022311.png)](/uploadfile/201211/615545ae92cff126d3d4b3b8ea0b60d820121115022311.png)