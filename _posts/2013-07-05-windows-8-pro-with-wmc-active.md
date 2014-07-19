---
layout: post
title: Windows 8 Pro 无需激活直接恢复 WMC 激活备份
categories:
- 技术生活
tags:
- Windows8
---

前两天升到 8.1 Preview，感觉的确不错，但是问题比较多，不太适合日常使用，所以重新装回 Win8。

本来是通过电话激活，并通过 WMC 再次激活的，但是手欠啊，把 Pro 的激活搞丢了，只剩 WMC 的激活备份了。

微软没有提供直接安装 WMC 的方法，只能在激活的前提下通过密钥升级到 WMC 版本。

那现在的问题就是如何从 Pro 升级到 WMC，或者直接安装含有 WMC 的镜像。后者网上有人发出过集成 WMC 的镜像，但我没有试过，不知道可行不可行。

那前者如何在未激活的状态下安装 WMC 呢？?? 答案就是用 WMC Trial Key，可以在未激活的状态下直接安装到 WMC，然后通过备份恢复就好了。

具体过程：

>1、正常安装 Pro 版 Win8。  
>2、进入系统，使用 WMC Trial Key（RR3BN-3YY9P-9D7FC-7J4YF-QGJXW），升级到 Pro WMC 版本。  
>3、更换 WMC 备份时的激活密钥，停止 SP 服务，恢复激活文件，激活成功。