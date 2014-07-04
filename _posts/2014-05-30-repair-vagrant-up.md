---
layout: default
title: 修复Vagrant启动错误
excerpt: VBox升级后引起 vagrant up 报错。
---
{{ page.title }}
================

今天在执行‘vagrant up’命令启动Ubuntu虚拟机时，跳出一个报错：

Vagrant could not detect VirtualBox! Make sure VirtualBox is properly installed.
Vagrant uses the ‘VBoxManage’ binary that ships with VirtualBox, and requires this to be available on the PATH. If VirtualBox is installed, please find the ‘VBoxManage’ binary and add it to the PATH environmental variable.

貌似Vagrant找不到VBoxManage的启动路径，导致虚拟机启动失败。

我猜想，可能是VBox升级所导致的。根据错误提示，只要把VBoxManage的启动路径添加到环境变量$PATH中，就可以了。于是我尝试了输入下面的命令：

```
echo $PATH 
```

果然，VBoxManage启动路径不在$PATH中。

```
export PATH=/cygdrive/d/Program\ Files/Oracle/VirtualBox:$PATH
```

更新环境变量$PATH后，再次‘vagrant up’后，虚拟机顺利启动了。

但是每次重启bash，都要再次更新$PATH,很麻烦。我把这条命令写在了.bashrc中，就可以自动的执行了。

至此，Vagrant启动问题圆满解决了。

{{ page.date | date: "%Y-%m-%d" }}
