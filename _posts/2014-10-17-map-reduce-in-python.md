---
layout: default
title: Map与Reduce的实现(Python)
excerpt: 自己花了几分钟实现了Python的map与reduce函数。
tags: [Coding]
---
{{ page.title }}
================

Python 3.4中有现成的map与reduce函数，支持函数式编程。今天我花了几分钟用Python源码实现了这两个函数，很简单。

map()函数接收两个参数，一个是函数，一个是序列，map将传入的函数依次作用到序列的每个元素，并把结果作为新的list返回。

```python
def my_map(function, the_list):
    return [function(each_item) for each_item in the_list]


def f(x):
    return x * x


foo = my_map(f, [1,2,3,4,5,6,7,8,9])

print(foo)

## [1, 4, 9, 16, 25, 36, 49, 64, 81]
``` 

reduce()把一个函数作用在一个序列上，这个函数必须接收两个参数，reduce把结果继续和序列的下一个元素做累积计算。

```python
def my_reduce(function, the_list):
    result = the_list[0]
    the_list = the_list[1:]
    for each_item in the_list:
        result = function(result, each_item)
    return result


def f(x, y):
    return x * y

def f2(str1, str2):
    return str1 + ':' +str2


foo = my_reduce(f, [1,2,3,4,5,6])

print(foo)

## 720

foo2 = my_reduce(f2, ['hello', 'ni', 'hao'])

print(foo2)

## hello:ni:hao
```

顺便提一下函数式编程中的惰性求值,这个在Python 3.4上已经实现了。目前的内置map()函数生成一个迭代器对象，通过list()函数生成结果列表。其实这个就是惰性求值！

{{ page.date | date: "%Y-%m-%d" }}

