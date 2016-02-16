---
layout: default
title: 引力波数据的分析
excerpt: 使用python的gwpy库分析引力波数据。
tags: [Coding]
---
{{ page.title }}
================

前几天LIGO公布，人类历史上第一次监测到了引力波。并且网络上说利用python的gwpy库可以分析引力波数据，但教程中并没有使用监测到引力波时的数据。我对此很感兴趣，因为不是专业人员，所以只想安装下gwpy库来显示下这次历史性的引力波数据图形。

我根据网上的[教程](http://www.codingpy.com/article/gwpy-ligo-analyze-gravitational-waves-data/)尝试安装好了gwpy库，花了几个小时时间，其中大坑特别多。给我的教训就是千万不要在windows系统上去安装，一定要在linux环境。我是在虚拟机里面的Debian上才安装好的，有几个库要用到LIGO网站上的源码包。

具体安装的步骤等我整理后再放上来了，我是把GW20150914这个引力波数据先下载到了本地，并且去掉了第一列的时间。

~~~python
#!/usr/bin/python

from numpy import asarray
from gwpy.timeseries import TimeSeries

data = open('GW150914.txt').read()

ts = TimeSeries(asarray(data.splitlines(), dtype=float),
                epoch=968654552, sample_rate=16384, unit='strain')

plot = ts.plot()
plot.set_title('LIGO Livingston Observatory data for GW150914')
plot.set_ylabel('Gravitational-wave strain amplitude')
plot.show()
~~~

![引力波](http://ww3.sinaimg.cn/large/6f76d05ajw1f11d26q0mgj20xc0gojw8.jpg)

{{ page.date | date: "%Y-%m-%d" }}
