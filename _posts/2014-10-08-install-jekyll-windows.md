---
layout: default
title: 本地搭建Jekyll环境(Windows系统)
excerpt: 在Windows系统上搭建Jekyll环境，方便开发博客。
tags: [Coding]
---
{{ page.title }}
================
一直在使用Github的Pages服务建设自己的博客，对Jekyll只有简单的了解，并没有再本地搭建Jekyll环境。今天我在Windows系统上搭建好了环境，步骤如下。

一、安装Ruby
----------------
由于jekyll是用ruby语言写的一个静态网页生成工具，所以要搭建jekyll本地环境就需要先配置好ruby环境。

1. 去官网[**下载Ruby**](https://www.ruby-lang.org/zh_cn/downloads/)，可以是安装包类型，也可以是解压版的。

2. 如果是安装版，则默认会给你配置系统环境变量，如果是解压版的，则需要自己配置系统环境变量。推荐下载RubyInstaller。

3. 下载DevKit，解压到相应文件夹，我是解压到了D:\devkit下。打开cmd，切换到D:\devkit下，执行以下命令。

~~~bash
D:\devkit> ruby dk.rb init
D:\devkit> ruby dk.rb install
~~~

二、安装Jekyll
------------------
打开cmd，执行：

~~~bash
C:\>gem install jekyll
~~~

安装语法高亮插件，需事先安装好Python2.7。通过jekyll new命令创建的站点中使用了语法高亮插件pygments，但pygments需要单独另外安装，所以导致部署站点时出现错误，虽然网站启动了，但是并没有成功生产静态页面，导致浏览页面时都是空的。

~~~bash
D:\Python27\Scripts> easy_install Pygments
~~~

三、测试Jekyll
-----------------
执行 jekyll new 网站名 ,jekyll会在当前目录下新建一个以网站名为名的文件夹，里面的是自动生成的一个简单的网站内容。

最后切换到新建的网站目录下，执行 jekyll serve 来启动网站，默认生成的静态网页等相关资源会放入_site文件夹。配置文件是_config.yml，网站的端口是4000，通过http://localhost:4000 来访问即可。


{{ page.date | date: "%Y-%m-%d" }}
