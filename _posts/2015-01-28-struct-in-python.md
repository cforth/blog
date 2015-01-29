---
layout: default
title: Python中实现结构体类
excerpt: 通过装饰器函数和元编程黑魔法，实现出Ruby中的Struct类。
tags: [Coding]
---
{{ page.title }}
================
Ruby中有一个很方便的Struct类，用来实现结构体。这样就不用费力的去定义一个完整的类来仅仅用作访问属性。

```ruby
class Dog < Struct.new(:name, :age)
end

fred = Dog.new("fred", 5)
printf "name:%s age:%d", fred.name, fred.age
##name:fred age:5
```

Python3.4中也可以这么干，但写法很累赘。其中包含`self.name = name` 这种很烦人的写法。

```python
class Dog(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age

fred = Dog("fred", 5)
print('name:{name} age:{age}'.format(name=fred.name, age=fred.age))
##name:fred age:5
```

想到我大Python是无所不能的，有没有一种简化结构体类属性定义的方法呢?答案肯定是有的。在补习了一些Python黑魔法技术后，我想到利用装饰器函数和元编程技术来实现。

```python
def struct(*name):
    """ 装饰器函数
        用途：用于在类定义中，自动设置self.value = value
    """
    def decorator(func):
        def wrapper(*args, **kw):
            for i in range(len(name)):
                setattr(args[0], name[i], args[i+1])
            return func(*args, **kw)
        return wrapper
    return decorator
    
class Dog(object):
    @struct('name','age')   #黑魔法所在!
    def __init__(self, *all_value):
        pass

fred = Dog("fred", 5)
print('name:{name} age:{age}'.format(name=fred.name, age=fred.age))
##name:fred age:5
```

要注意的是，这种写法会造成代码结构的不清晰。

{{ page.date | date: "%Y-%m-%d" }}
