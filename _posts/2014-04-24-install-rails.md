---
layout: default
title: Rails开发环境部署
---
{{ page.title }}
----------------


[**Rails**](http://guides.rubyonrails.org/)开发环境的部署，对新手来说有几个大坑的。我花了几个下午才把Rails安装成功，下面就是Rails开发环境部署的过程：

1. 我的主机系统是Windows，并且安装好了Cygwin，可以在Windows系统上享受到linux命令行的好处。

2. 安装好Vagrant，并且通过Vagrant安装好了Ubuntu12.04 LTS。

3. 修改Vagrant虚拟机的配置文件Vagrantfile。注意将Rails Server需要的3000端口映射到主机上的3000端口。

4. 通过vagrant up启动虚拟机，通过vagrant ssh进入Ubuntu虚拟机，安装VIM等一系列必须要的工具。修改软件源为国内，更新软件源，更新软件包。

5. 修改.vimrc与.bashrc为自己习惯的配置。

6. 必须要卸载掉旧的Ruby软件包，安装最新的RVM和Ruby。参考[**这篇教程**](http://zuyunfei.com/2013/04/01/install-ruby-on-ubuntu/)。（1号坑）

7. 修改gem安装源为淘宝，通过gem安装rails。（2号坑）

8. 安装nodejs来提供JavaScript runtime。（3号坑）

9. Rails安装成功后，一定要通过下面三条命令来选择最新的ruby版本。
    source ~/.rvm/scripts/rvm
    rvm reload
    rvm use default

10. Rails开发环境就部署好了，只需要关闭虚拟机后执行vagrant package 来打包虚拟机就能再其他机器上快速部署Rails了。在安装过程中注意三个大坑，不来会把自己害惨的。

{{ page.date | date: "%Y-%m-%d" }}
