---
layout: default
title: Vagrant安装步骤
excerpt: Vagrant是个好用的开发环境部署工具。
---
{{ page.title }}
----------------


[**Vagrant**](http://www.vagrantup.com/)是一款构建虚拟开发环境的工具。很多情况下，在桌面系统上开发的Web应用，最后要部署到Linux生成环境上去。因为各自的本地开发环境不同，部署到最终的运行环境中可能会存在问题。

Vagrant能封装一个Linux开发环境，打包后再发放给团队成员使用。成员可以在自己喜欢的系统上开发程序，代码却能在统一的Linux环境里运行。

1，安装[**VirtualBox**](https://www.virtualbox.org/wiki/Downloads)。

2，安装[**Vagrant**](http://www.vagrantup.com/)。

3，下载官方封装好的[**基础镜像**](http://www.vagrantbox.es/)。

4，添加镜像到 Vagrant。假设镜像存放路径是~/box/precise64.box(Windows系统可以使用Cygwin):
  {% highlight bash %}
  $ vagrant box add mybox ~/box/precise64.box
  {% endhighlight %}

5，切换到开发目录(比如 ~/work)，用mybox镜像初始化目录:
  {% highlight bash %}
  $ cd ~/work  # 切换目录
  $ vagrant init mybox  # 初始化
  $ vagrant up  # 启动环境
  {% endhighlight %}

6，启动完成后，用SSH登陆虚拟机:
  {% highlight bash %}
  $ vagrant ssh  # SSH 登录
  $ cd /vagrant  # 切换到开发目录，也就是宿主机上的 ~/work
  {% endhighlight %}

7，配置Vagrantfile文件可以进行个性化的定制。在虚拟机中可以部署基本的开发环境，注意跟新软件源。~/work目录其实就是宿主机与虚拟机之间的共享目录。

8，在配置好虚拟机环境后，可以关闭虚拟机，对虚拟机进行打包后分发:
  {% highlight bash %}
  $ vagrant package
  {% endhighlight %}

这样子就可以在任何机子上利用Vagrant搭建好基础的Linux开发环境了。

{{ page.date | date: "%Y-%m-%d" }}
