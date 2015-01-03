---
layout: default
title: 学习编写网页爬虫
excerpt: 使用Python语言写了个网页爬虫，可以自动获取股票关注数据。
tags: [Coding]
---
{{ page.title }}
================

最近这段时间，我对网页爬虫很感兴趣。自学了Python编程的基础知识，然后找了份网页爬虫的教程，一头栽了进去。

通过使用Python自带的urllib标准库，我写了个专门获取股票关注数据的网页爬虫。这个网页爬虫说白了其实就是一个小程序，能自动按照一定规则去下载一些网页链接。通过正则表达式匹配需要获取的内容，最后在把格式化后的内容存入文件中。

[**这里**](https://github.com/cforth/web-spider/blob/master/tkinter_spider.py)是这个小爬虫的源代码，比较简单的一个小程序，方便我日常使用。

{{ page.date | date: "%Y-%m-%d" }}
