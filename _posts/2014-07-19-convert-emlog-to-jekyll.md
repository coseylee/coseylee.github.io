---
layout: post
title: 将 emlog 转换到 Jekyll (Markdown)
categories:
- 技术生活
tag:
- Jekyll
---

之前在 SAE 移植的 emlog 上写博客，这两天搬家到 GitHub Pages，需要将原来的博文搬过来。

找了一圈没找到直接从 emlog 转换到 Jekyll 的工具。
后来就采用了折中的办法，就是先将 emlog 转换到 wordpress，再从 wordpress 转到 Jekyll。


**emlog to wordpress**

1. 下载 emlog 数据库，导入到本地。
2. 全新安装 wordpress。
3. 使用 emtowp 这个小工具，设置好数据库连接参数，直接转换数据库，非常方便。

**wordpress to jekyll**

1. 将 wordpress 导出至 XML 文件。
2. 下载 [exitwp](https://github.com/thomasf/exitwp)，并将 WP 的 XML 放入 exitwp 的 wordpress-xml 目录里。
3. 执行 `python exitwp.py`，不下载远程图片的话，分分钟转换完成。
4. 回到 exitwp 目录，里面的 build 就是转换好的 Markdown 文件。

exitwp 能将分类和标签完整转换过来，接下来就是对个别的博文样式做下微调就OK了。