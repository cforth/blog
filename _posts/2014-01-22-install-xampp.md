---
layout: default
title: windows系统XAMPP安装
---
{{ page.title }}
----------------

[**XAMPP**](http://www.apachefriends.org/zh_cn/xampp-windows.html)是一个把Apache网页服务器与PHP、Perl及MySQL集合在一起的安装包，允许用户可以在自己的电脑上轻易的建立网页服务器。

我是在windows系统上安装了XAMPP，用作动态网站的开发学习。安装非常简单，没有什么好多说的。要注意的是：所有网络文档都放在 htdocs 主文件夹中（.\xampp\htdocs）。如果您将 test.html 文件放在这里，您可以通过 http://localhost/test.html 来访问它。php 或 cgi 文件也同样放在这里。其他的 WWW 子文件夹可以在 htdocs 目录下创建。例如将 test.html 放在 .\xampp\htdocs\new 路径下，您就可以在浏览器的地址栏中输入 http://localhost/new/test.html 来访问这个文件。

还有因为我在windows上开发，所以安装了VIM的windows版。下面是我的配置文件_VIMRC：

```
set encoding=utf-8
set fileencodings=utf-8,chinese,latin-1
if has("win32")
set fileencoding=chinese
else
set fileencoding=utf-8
endif
"解决菜单乱码
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim
"解决consle输出乱码
language messages zh_CN.utf-8
```

这样的配置可以让VIM用起来更加舒服(对于我自己)。

{{ page.date | date: "%Y-%m-%d" }}
