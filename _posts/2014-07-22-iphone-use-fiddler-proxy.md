---
layout: post
title: iPhone 使用 Fiddler 进行 HTTPS 网络抓包
date: 2014-07-22 23:55
categories:
- 技术生活
tags:
- iPhone
- Fiddler
---

Fiddler 是著名的 HTTP(S) 抓包工具，功能十分强悍。Fiddler 采用代理的方式进行抓包，所以使用范围就非常广泛，不仅可以在 PC 端使用，更可以在移动设备上使用。

要在 iPhone 上使用并且可以抓取 HTTPS 数据包的话需要按以下方式设置。

**Fiddler 设置**

[![1](/uploadfile/201407/22/fiddler-1.jpg)](/uploadfile/201407/22/fiddler-1.jpg)

选择 `Tools -> Fiddler Options`，打开 Fiddler 配置。

[![2](/uploadfile/201407/22/fiddler-2.jpg)](/uploadfile/201407/22/fiddler-2.jpg)

勾选 `Decrypt HTTPS traffic`，并选择 `...from remote clients only` 和 `Ignore server certificate errors`。

[![3](/uploadfile/201407/22/fiddler-3.jpg)](/uploadfile/201407/22/fiddler-3.jpg)

然后切换到 `Connections` 选项卡，配置监听的端口号并允许远程连接，确保防火墙中允许 Fiddler 端口可以远程连接。

设置好后，关闭 Fiddler 重新打开，其他设备就可以连接 Fiddler 进行抓包了。

**iPhone 设置**

因为要抓取 HTTPS 数据，所以需要在 iPhone 上安装证书。

[![4](/uploadfile/201407/22/fiddler-4.jpg)](/uploadfile/201407/22/fiddler-4.jpg)

在手机浏览器中访问 Fiddler 的代理地址，就是 Fiddler 所在电脑的IP加上监听的端口号比如：`http://192.168.1.10:8888`。  
点击下方的 `FiddlerRoot certificate` 打开安装证书界面。

[![5](/uploadfile/201407/22/fiddler-5.jpg)](/uploadfile/201407/22/fiddler-5.jpg)

点击 `安装` 就将证书安装到 iPhone 里了。

[![6](/uploadfile/201407/22/fiddler-6.jpg)](/uploadfile/201407/22/fiddler-6.jpg)

最后设置 iPhone 代理服务器为 Fiddler 就一切都 OK 了。

之后在 iPhone 访问网页，就可以在 Fiddler 中看到数据了。

>PS: 微信通讯不走代理，无法通过 Fiddler 抓包，但是微信内访问网页正常。


