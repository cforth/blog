---
layout: default
title: Ruby的函数调用与super
excerpt: Ruby中允许method的重复声明，并且允许通过super关键字调用前次定义。
tags: [Coding]
---
{{ page.title }}
================
这几天在看《计算的本质：深入剖析程序和计算机》的第三章，通过非确定有限自动机NFA来组合成正则表达式实现。其中在实现NFA的自由移动功能时，一段Ruby代码很让我困扰。导致我在用Python语言重写这段代码时，发生了很严重的错误，找了一整天才找到出错的地方在哪。这段Ruby代码就是利用了super关键字：

```ruby
class NFA
    def current_states
        rulebook.follow_free_moves(super)
    end
end
```

NFA类的current_states方法已经在之前有了实现，但是这里又重复定义一次。由于Python中无法不通过继承来重复定义一个方法，所以我很疑惑。查了一些资料后，貌似这就是Ruby的一个很重要的特性“猴子补丁”。我不理解这段代码，特别用super关键字作为参数的用处。

研究之后才发现，这里的super关键字是调用了前一次`current_states`方法的返回值作为`follow_free_moves`方法的参数。这段代码的意义就在于，在没有修改之前的`current_states`方法的前提下，实现了`current_states`方法的新定义。并且将前一次定义的返回值作为了新定义中的一个参数来使用。这让我想到一个问题，如果你在别处重复几次实现了同一个方法，等到要修改这个方法定义时，需要顺着super的调用链去寻找每个定义。

Ruby这种打开类来做“猴子补丁”的方法，很容易引起Ruby初学者的困惑。它太强大太灵活了，会导致类的方法在不同的作用域内有不同的表现。在经过了这个坑之后，我还是老老实实的修改了Python代码中`current_states`的实现，这样即使出了问题，也能很快速的找到，不会像在Ruby中迷失在各个super关键字的调用链中。

{{ page.date | date: "%Y-%m-%d" }}
