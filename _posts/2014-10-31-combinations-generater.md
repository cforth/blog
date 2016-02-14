---
layout: default
title: 排列组合生成算法
excerpt: 组合数学之排列组合生成算法，使用Python实现。
tags: [Coding]
---
{{ page.title }}
================
这几天在研究组合数学，对一个经典的排列问题产生了兴趣，问题是这样的：

“有5个不同颜色的小球在一个盒子里面，取出一个小球，记下颜色再把该小球放入盒子，共取3次，请问总共有多少种排列情况？”

这个问题的答案应该是只要上过高中都能写出来的，它的答案其实就是**5的3次方等于125**。现在对于这个问题我想加深一点，列出所有的排列情况，也就是全部125种排列。这个加深后的问题也非常容易用Python代码实现。我实现了这个combinations_generater函数，可以打印出全部的排列情况。并且这个函数是个通用函数，也就是说它接受一个列表和抽取次数参数，能正确的打印出全部的排列。

~~~python
## 排列组合生成算法
## Python3.4

def combinations_generater(elements, length):
    """对有N个元素的列表，取X次（可取重复的元素）。生成全部的组合情况。
       参数： elements ：有N个元素的列表。
             length ：取元素的次数，也就是生成的组合的长度。
       结果： 一个组合生成器，使用for循环进行迭代，给出所有组合。
    """
    result = [None for n in range(length)]
    base = len(elements)  
    for num in range(base ** length):
        for index in range(length):
            result[index] = elements[num % base]
            num = num // base
        yield result

##test
print('From list(0,1,2,3,5) to choose 2 elements:')
for n in combinations_generater_no_repeat(['红','黄','蓝','黑','白'], 3):
    print(n)
~~~

在写出了这个生成排列的函数后，我又考虑了另外一种情况：

“有5个不同颜色的小球在一个盒子里面，取出一个小球，记下颜色不把该小球放入盒子，共取3次，也就是不能重复抽取，请问总共有多少种组合情况？”

注意这个问题中，不重复抽取小球，并且不计小球的排列顺序了，所以这是一个组合问题。也有现成的数学组合公式来计算，但我还是写出了能生成所有组合的函数。

~~~python 
def combinations_generater_no_repeat(elements, length):
    """对有N个元素的列表，取X次（不可重复取元素）。生成全部的组合情况。
       参数： elements ：有N个元素的列表。
             length ：取元素的次数，也就是生成的组合的长度，不能大于元素列表的长度。
       结果： 一个组合生成器，使用for循环进行迭代，给出所有组合。
    """
    result_set = set()
    base = len(elements)  
    for num in range(base ** length):
        index_set = set()
        for i in range(length):
            index_set.add(num % base)        #这一步是为了去除重复组合
            num = num // base
        result = tuple([elements[i] for i in index_set])
        if (len(result) == length) & (result not in result_set):
            result_set.add(result)
            yield list(result)
 
## test 
print('From list(0,1,2,3,5) to choose 2 elements, allowed to repeat:')
for n in combinations_generater(['红','黄','蓝','黑','白'], 3):
    print(n)
~~~

{{ page.date | date: "%Y-%m-%d" }}
