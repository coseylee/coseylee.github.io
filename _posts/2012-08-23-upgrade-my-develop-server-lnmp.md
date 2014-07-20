---
date: 2012-08-23 18:19:40+00:00
layout: post
slug: 今天把自己的测试环境升级了，统统最新版
title: 今天把自己的测试环境升级了，统统最新版
categories:
- 技术生活
tags:
- PHP
- LAMP
- MySQL
- Nginx
- Ubuntu
---

看了 PHP 5.4 加了很多特性，最近刚用上 Windows 8，索性把测试环境都给升级了，把一些遇到的问题，作下记录。

**版本如下**：

>Ubuntu:12.04  
>Nginx:1.2.3 [http://nginx.org/download/nginx-1.2.3.tar.gz
](http://nginx.org/download/nginx-1.2.3.tar.gz)  
>Mysql:5.5 [http://cdn.mysql.com/Downloads/MySQL-5.5/mysql-5.5.27.tar.gz
](http://cdn.mysql.com/Downloads/MySQL-5.5/mysql-5.5.27.tar.gz)  
>PHP:5.4 [http://cn2.php.net/distributions/php-5.4.6.tar.gz](http://cn2.php.net/distributions/php-5.4.6.tar.gz)

因为是测试用的，所以就用 Ubuntu 了，从11.10升级到12.04，这个没什么好讲的，不过 Ubuntu 的体验还真不错，系统升级都很人性。

Ubuntu 桌面版有些类库并没有自带，因为我是升级的所以也没用上，不过也记录一下吧，要手动安装的类库如下（根据功能而定）。

**依赖库安装**
{% highlight sh %}
sudo apt-get install libpcre3-dev zlib1g-dev libncurses5-dev build-essential libxml2-dev libcurl4-openssl-dev libjpeg-dev libpng-dev libfreetype6-dev libtool autoconf
{% endhighlight %}

**Nginx 编译安装**

Nginx 编译起来也很简单。
{% highlight sh %}
./configure --user=coseylee --group=coseylee --prefix=/data/server/nginx --with-http_stub_status_module
{% endhighlight %}

**PHP 编译安装**

PHP也一样，只不过并没有使用 libmysql，而是使用 PHP内 置的 mysqlnd。
{% highlight sh %}
./configure --prefix=/data/server/php --with-config-file-path=/data/server/php --enable-mbstring --enable-ftp --with-gd --with-jpeg-dir=/usr --with-png-dir=/usr --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-pear --enable-sockets --with-freetype-dir=/usr --enable-gd-native-ttf --with-zlib --with-libxml-dir=/usr --with-xmlrpc --enable-zip --enable-fpm --enable-fpm --enable-xml --enable-sockets --with-gd --with-zlib --with-iconv --enable-zip --with-freetype-dir=/usr/lib/ --enable-soap --with-openssl --enable-pcntl --enable-cli --with-curl=/usr/lib
{% endhighlight %}

**MySQL 编译安装**

最大变化的就是 MySQL 5.5 变化很大。首先使用 cmake 而不是 autoconf 来 configure，所以要安装cmake。
{% highlight sh %}
sudo apt-get install cmake
{% endhighlight %}

当然配置项也发生了变化，这里我把我的贴出来，更详细的可以在附件中查到。
{% highlight sh %}
CFLAGS="-O3" CXX=gcc
CXXFLAGS="-O3 -felide-constructors -fno-exceptions -fno-rtti"

cmake 
-DCMAKE_INSTALL_PREFIX=/data/server/mysql 
-DMYSQL_DATADIR=/data/server/database 
-DEXTRA_CHARSETS=all 
-DDEFAULT_CHARSET=utf8 
-DDEFAULT_COLLATION=utf8_general_ci 
-DWITH_INNOBASE_STORAGE_ENGINE=1 
-DWITH_ARCHIVE_STORAGE_ENGINE=1 
-DWITH_BLACKHOLE_STORAGE_ENGINE=1 
-DWITH_EMBEDDED_SERVER=1  
-DENABLED_LOCAL_INFILE=1 
-DWITH_DEBUG=0
{% endhighlight %}

MySQL5.5 在编译的时候会用进度显示，这点真心不错。 

[![QQ截图20120823094400.png](/uploadfile/upload/c169f7b9d7b838065d5aac8b7c15df8c20120823105713.png)](/uploadfile/upload/c169f7b9d7b838065d5aac8b7c15df8c20120823105713.png)  

到这里升级记录就差不多了，最后推荐使用轻量级的 MySQL 管理工具 adminer，可以在[http://www.adminer.org/](http://www.adminer.org/)下载到。