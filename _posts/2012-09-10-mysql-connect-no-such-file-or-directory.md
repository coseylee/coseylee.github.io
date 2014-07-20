---
date: 2012-09-10 14:28:46+00:00
layout: post
title: 连接 MySQL 报错 “No such file or directory”
categories:
- 技术生活
tags:
- MySQL
- PHP
---

在 PHP 中连接 MySQL，报错 `“No such file or directory”`，大概原因就是 PHP 没有找到 MySQL 的 Unix Socket 的位置。

有两种可能：  
1. 根本没有启动 MySQL。（^_^）  
2. PHP 中 MySQL 的 Unix Socket 配置错误。

第二种可能的解决方案：

>根据使用驱动不同，大概 php.ini 中有 mysql.default_socket、mysqli.default_socket、pdo_mysql.default_socket 这几个项，然后将正确的 MySQL Unix Socket 文件填入即可。
>
>[![配图](/uploadfile/upload/072774b6b658b3603e1aa7198722775c20120910064254.png)](/uploadfile/upload/072774b6b658b3603e1aa7198722775c20120910064254.png)   



然后重启 PHP，使配置生效即可。