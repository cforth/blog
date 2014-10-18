---
layout: default
title: 树的遍历算法实现
excerpt: 实现树的深度优先遍历与广度优先遍历算法。
tags: [Coding]
---
{{ page.title }}
================
![tree](http://img.my.csdn.net/uploads/201410/18/1413638268_8968.jpg)

树是一种常用的数据结构，今天我花了点时间研究了树的深度遍历与广度遍历算法实现。二叉树的遍历算法很简单，但要写正确了还得花点心思。

```python
## 二叉树遍历

##        0
##     ___|___
##    |       |  
##    1       4  
##   _|_     _|_    
##  |   |   |   |
##  2   3   5   6


class BinaryTree:
    def __init__(self, data, lchild=None, rchild=None):
        self.data = data
        self.rchild = rchild
        self.lchild = lchild


node2 = BinaryTree(2)
node3 = BinaryTree(3)
node5 = BinaryTree(5)
node6 = BinaryTree(6)


node1 = BinaryTree(1, lchild=node2, rchild=node3)
node4 = BinaryTree(4, lchild=node5, rchild=node6)

node0 = BinaryTree(0, lchild=node1, rchild=node4)


## 深度优先遍历二叉树
def depth_first_search(root):
    stack = []
    stack.append(root)
    while len(stack) != 0 :
        node = stack[-1]
        print(node.data, end=' ')
        stack.pop()
        if node.rchild != None:
            stack.append(node.rchild)
        if node.lchild != None:
            stack.append(node.lchild)
    print('\n')


depth_first_search(node0)
## 0 1 2 3 4 5 6


## 广度优先遍历二叉树
def breadth_first_search(root):
    quene = []
    quene.append(root)
    while len(quene) != 0 :
        node = quene[0]
        print(node.data, end=' ')
        quene.pop(0)
        if node.lchild != None:
            quene.append(node.lchild)
        if node.rchild != None:
            quene.append(node.rchild)
    print('\n')

breadth_first_search(node0)
## 0 1 4 2 3 5 6 
```

实现完二叉树的遍历后，我又思考了下普通树的遍历算法。发现也很简单，写起来只要仔细一点就行了。

```python
## 普通树遍历

##          0
##     _____|_____
##    |     |     |
##    1     5     8
##   _|_   _|_    |
##  | | | |   |   |
##  2 3 4 6   7   9


class Tree:
    def __init__(self, data, child=None):
        self.data = data
        self.child = child


node2 = Tree(2)
node3 = Tree(3)
node4 = Tree(4)
node6 = Tree(6)
node7 = Tree(7)
node9 = Tree(9)

node1 = Tree(1, [node2, node3, node4])
node5 = Tree(5, [node6, node7])
node8 = Tree(8, [node9])

node0 = Tree(0, [node1, node5, node8])

## 深度优先遍历树
def depth_first_search_tree(root):
    stack = []
    stack.append(root)
    while len(stack) != 0 :
        node = stack[-1]
        print(node.data, end=' ')
        stack.pop()
        if node.child != None:
            length = len(node.child)
            for i in range(1, length+1):
                stack.append(node.child[-i])
    print('\n')

depth_first_search_tree(node0)
## 0 1 2 3 4 5 6 7 8 9 


## 广度优先遍历树
def breadth_first_search_tree(root):
    quene = []
    quene.append(root)
    while len(quene) != 0 :
        node = quene[0]
        print(node.data, end=' ')
        quene.pop(0)
        if node.child != None:
            for item in node.child:
                quene.append(item)
    print('\n')

breadth_first_search_tree(node0)
## 0 1 5 8 2 3 4 6 7 9 
```

这几个树遍历的算法，都是利用了堆栈或者队列这种数据结构，并没有使用递归算法。

{{ page.date | date: "%Y-%m-%d" }}
