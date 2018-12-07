---
layout: default
title: 每周记录第12期
excerpt: 这两周我在改进ImgLook。
tags: [Thinking]
---
{{ page.title }}
================

这两周，我在业余时间思考了如何改进ImgLook的方法。ImgLook目前最大的问题是，无法在图片放大后，通过滚动条查看全图。原因在于显示图片的控件是tkinter.Label，是不支持滚动条的。

但是，我在CFCanvas类中已经解决了这个问题。于是我想把CFCanvas代替Label作为ImgLook的控件，需要改写很多代码。通过很费劲的改进，应该是可以完成的。

目前，我已经测试成功了，将CFCanvas类成功的应用在了ImgLook上。并且也解决了GIF动图显示的问题，可以将GIFHandle类并入CFCanvas类中了。现在正在做进一步的优化和测试代码，希望下周正式发布新的ImgLook模块。

{{ page.date | date: "%Y-%m-%d" }}
