---
layout: default
title: 利用jekyll的tags实现文章分类
excerpt: 为我的博客实现了简单的文章分类显示功能。
tags: [Coding]
---
{{ page.title }}
================

今天，我利用jekyll自带的tags功能，实现了博客里文章的分类整理。

具体的实现方法是：

1. 为每篇Markdown格式的文章顶部增加一个tags数组。类似“tags: [IT]”。

2. 增加一个show_by_tag.html。把所有文章的tags数据保存在JSON中，通过jquery.query.js插件从URL中获取tags参数，来显示对应的每个tags的所有文章。

3. 具体的实现方法，请参考[**源代码**](https://github.com/cforth/blog/blob/gh-pages/show_by_tag.html)。

说起来很简单，我还是花了很长时间来实现和除错。

{{ page.date | date: "%Y-%m-%d" }}
