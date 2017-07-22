---
layout: default
title: CryptoApp简介
excerpt: 用Python3实现的简单的加密解密GUI程序。
tags: [Coding]
---
{{ page.title }}
================

[CryptoApp](https://github.com/cforth/CryptoApp)是一个简单的加密解密GUI程序，使用Python3实现。

为什么要开发CryptoApp?
-------------------

我需要加密一些文件，可能是一些文件夹。于是自己动手封装了Crypto库中的AES加密方式，将它变得更适合加密大文件。具体的做法是分块加密大文件，分次写入。封装好的库[CFCrypto](https://github.com/cforth/CryptoApp/blob/master/libs/CFCrypto.py)可以很方便的加密字符串、大文件、文件夹。后来我觉得用应该写个简单的GUI程序，可以方便加密解密操作，于是我就用Tkinter写了个，这就是CryptoAPP！

CryptoApp有什么功能？
-------------------

只有很简单的功能，它只用了AES-128加密方式，并且是ECB模式。加密强度对普通使用应该是够了，主要是简单方便的文件加密。它只有三个功能，加密字符串、加密文件、加密文件夹。加密文件夹是会将目录名和文件名一起加密的。

{{ page.date | date: "%Y-%m-%d" }}
