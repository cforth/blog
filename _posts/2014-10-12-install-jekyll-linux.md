---
layout: default
title: 本地搭建Jekyll环境(Linux系统)
excerpt: 在Linux系统上搭建Jekyll环境，版本问题有点折腾。
tags: [Coding]
---
{{ page.title }}
================
![Jekyll On linux](http://img.my.csdn.net/uploads/201410/11/1413025328_7898.png)

前一篇日志记录了在Windows系统上搭建Jekyll开发环境的过程，今天在Ubuntu上折腾了下。系统环境是Windows + Cygwin + Vagrant + Ubuntu 12.04虚拟机。

一、设置Ubuntu的时区和语言环境
----------------
1. 为新安装的Ubuntu虚拟机设置ROOT密码。

2. 修改系统时间为CST时间。打开 /etc/default/rcs 文件，找到UTC=YES, 改为UTC=NO 

3. sudo cp /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime

4. 修改locale为中文环境。打开 /etc/default/locale 将`en_US`修改为`zh_CN.utf8`

二、安装Python
------------------
1. 首先需安装CURL工具。

2. 安装pyenv，通过pyenv安装Python 2.7.3版本和3.4.2版本 。系统默认的Python版本设置为2.7.3，在单独的文件夹内可以设置不同的Python默认版本。

3. 利用pyenv控制Python版本。

三、安装Ruby
-----------------
1. 首先需安装RVM工具。

2. 更换Gem源为淘宝源，参考[**这里**](http://ruby.taobao.org/)。

3. 利用RVM安装最新的Ruby版本2.1.3。设置为默认Ruby版本为2.1.3。

四、安装Jekyll
-----------------
在bash上输入以下代码：

```
gem install jekyll      #注意要在ruby 2.1.3环境上安装jekyll
easy_install Pyaments   #jekyll上的语法高亮插件，注意要在python 2.3.1环境上安装
apt-get install nodejs  #jekyll需要的JS库
``` 

至此在Ubuntu上的Jekyll本地开发环境就已经搭建好了。

{{ page.date | date: "%Y-%m-%d" }}

