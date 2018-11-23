---
layout: default
title: 每周记录第11期
excerpt: 继续改进CryptoApp。
tags: [Thinking]
---
{{ page.title }}
================

本周继续改进了[CryptoApp](https://github.com/cforth/CryptoApp)，为其中的[TextLook](https://github.com/cforth/CryptoApp/blob/master/ImgLook.py)模块增加了文本换行选项。

下周希望能够对其中的[ImgLook](https://github.com/cforth/CryptoApp/blob/master/ImgLook.py)模块进行重构，为图片显示增加滚动条。需要将图片显示控件替换为我自己的[CFCanvas控件](https://github.com/cforth/codefarm/blob/master/idea-365/D034_CFCanvas/CFCanvas.py)才可以，要改动的地方非常多。可能直接重新写这个模块。

我还希望将这些工具一起集成在一个叫做CF资源管理器的GUI程序中，类似Windows的资源管理器一样，可以非常方便的对各种文件进行处理、加密解密或打开预览。

{{ page.date | date: "%Y-%m-%d" }}
