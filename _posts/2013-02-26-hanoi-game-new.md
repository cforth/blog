---
layout: default
title: 汉诺塔游戏终极版
excerpt: 使用一个脚本来输出汉诺塔自动运行的步骤，再通过管道提供给汉诺塔游戏，实现了自动完成汉诺塔。
tags: [Coding]
---
{{ page.title }}
================

今天，我完成了汉诺塔游戏终极版。使用一个脚本来输出汉诺塔自动运行的步骤，再通过管道提供给汉诺塔游戏，实现了自动完成汉诺塔。

在去年我用C语言写完汉诺塔游戏时，一直有个未完成的心愿。我希望能让汉诺塔自动运行，自己享受电脑程序来帮我玩汉诺塔的乐趣。当时因为编程能力有限，一直没有完成就搁浅了。现在，我利用lisp语言写了个小脚本来自动输出移塔步骤。

我再次凭着初学者大无畏的精神，任是把lisp代码写成了像大过程式，十分之拙劣，但是也确实好用。

项目地址如下：https://github.com/cforth/codefarm/tree/master/hanoi_game

下载hanoi_auto.c:
  编译执行，首先接受汉诺塔游戏的层数，再接受移塔步骤，操作方法见hanoi_new说明。


下载hanoi_alg.scm:
  使用scheme编写，主要是接受汉诺塔游戏的层数，输出移塔步骤，通过管道给hanoi_auto.exe。


hanoi_auto与hanoi_alg配合使用，可自动完成汉诺塔游戏。
操作步骤如下：

~~~bash
./hanoi_alg.scm | ./hanoi_auto.exe
5                  //输入要完成的hanoi层数
~~~

{{ page.date | date: "%Y-%m-%d" }}
