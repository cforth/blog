---
layout: default
title: 在Python中调用DLL库
excerpt: 在Windows上使用Python调用C语言写的动态链接库。
tags: [Coding]
---
{{ page.title }}
================

一、从VS2008中导出dll文件 
-------------------

VS2008中，File > New Project > Win32 > Win32 Console Application. 输入项目名称：dlltest。点击【OK】，【Next】，选择dll单选按钮，完成。创建dlltest.c，代码如下(包含自动生成的代码):

~~~c
#include "stdafx.h"

extern "C" _declspec(dllexport) int
multiply(int num1, int num2)
{
	return num1 * num2;
}
~~~

 编译一下，到工程的DEBUG目录，就可以找到dlltest.dll。

二、在Python3中调用
--------------------

把dll文件放入Python3代码所在的文件夹内，调用dll文件，代码如下：

~~~python
from ctypes import *
import os

libtest = cdll.LoadLibrary('dlltest.dll')
print(libtest.multiply(2, 2))  # 输出为4
~~~

{{ page.date | date: "%Y-%m-%d" }}