---
layout: default
title: Eclipse集成开发环境使用
excerpt: 在Eclipse中配置Java、Python开发环境非常方便，Git插件也很棒。
tags: [IT]
---
{{ page.title }}
================
这几天我在学习Java编程，开发Java当然离不开好的集成开发环境。我在Windows主机上开发，当然选择了最流行最大众的Eclipse。使用后才发现Eclipse真是个神器啊，不仅是开发Java，用来写Python、Ruby也都可以。并且它自带了Git插件，可以方便将代码Push到Github代码仓库。

一、下载Eclipse
--------------
在官网上下载最新版的Eclipse，网址在[**这里**](http://www.eclipse.org/downloads/)。因为我主要是用来开发Java程序，所以选择了Eclipse IDE for Java Developers。

二、安装Eclipse
--------------
其实根本就不要安装，直接解压到你想存放的目录里就可以了。

三、配置Java开发环境
--------------
首先你要下载JDK，因为没有JDK的话Eclipse是打不开的，Eclipse就是用Java开发的。在Oracle官网上下载，网址是[**这个**](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html),一定要下载对应的版本。我自己下载的是jdk-8u31-windows-i586.exe。最近这段时间在国内很难打开这个网页，不知道是不是被墙了。打不开的话直接搜索JDK也可以。

安装好JDK后，就能启动Eclipse了。启动速度有点慢，达不到秒开，可能加载的插件比较多。建立Java项目的话，我就不多说了。

四、配置Python开发环境
------------------
首先也是你必须安装好Python，直接在Python官网选择好python版本并下载Windows版，然后一路默认就安装好了。

Python插件不是Eclipse自带的，需要下载安装[**PyDev**](http://pydev.org/download.html)。安装方法也很简单，可以自己下载PyDev插件，并将解压后产生的features和plugins文件夹覆盖Eclipse安装目录内同名的目录。这样就算安装完成了，非常简单。

还有种安装PyDev的方法是利用Eclipse软件Help菜单内的Install New Sofrware来安装，但是鉴于国内的网络环境，很难在线安装成功。

安装好PyDev后就是配置Python解释器，打开Window --> Preferences菜单，在里面找到PyDev的Python Interpreter。新建一个解释器位置，把它指向你安装的Python目录内的python.exe就可以了。

五、配置Git插件
-----------------
最后来讲一下Git插件的配置，分两种情况。

如果在主机上没有配置过SSH Key，需要先生成一个：Window --> Preferences菜单内SSH2 -> Key Management -> Gernerate RSA Key 生成 SSH 的 public key。

如果在主机上配置过SSH Key，则可以在C:\Documents and Settings\Administrator\.ssh目录内找到。通过Eclipse中的SSH2 -> General来添加这个.ssh目录。

有了SSH Key，在GitHub中通过：edit your profile -> ssh key -> Add SSH Key 添加SSH Key, 把上面生成的 public key 拷贝到这里，保存。

在Window --> Show View菜单中找到Git插件并打开窗口，就可以很方便的Clone Github上的代码仓库到你的本地主机上了。

{{ page.date | date: "%Y-%m-%d" }}