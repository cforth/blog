---
layout: default
title: 排序算法
excerpt: 各种排序算法，使用Python实现。
tags: [Coding]
---
{{ page.title }}
================
前段时间研究了下几种常见的排序算法，并用Python3代码实现。

一 选择排序
---------------
选择排序很简单，步骤如下：

1. 从左至右遍历，找到最小(大)的元素，然后与第一个元素交换。
2. 从剩余未排序元素中继续寻找最小（大）元素，然后与第二个元素进行交换。
3. 以此类推，直到所有元素均排序完毕。

```python
## Selection Sort Algorithm

def selection_sort(the_list):
    length = len(the_list)
    for i in range(length):
        min_index = i
        for n in range(i, length, 1):
            if the_list[n] < the_list[min_index]:
                min_index = n
        the_list[i], the_list[min_index] = the_list[min_index], the_list[i]
    return the_list


## test
test_list = [1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 5, 7, 7]
selection_sort(test_list)
print(test_list)
```

二 插入排序
---------------
插入排序的基本操作就是将一个数据插入到已经排好序的有序数据中，从而得到一个新的、个数加一的有序数据，算法适用于少量数据的排序，时间复杂度为O(n^2)。是稳定的排序方法。具体的步骤为：

1. 从第一个元素开始，该元素可以认为已经被排序
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描
3. 如果该元素小于前面的元素（已排序），则依次与前面元素进行比较如果小于则交换，直到找到大于该元素的就则停止；
4. 如果该元素大于前面的元素（已排序），则重复步骤2
5. 重复步骤2~4 直到所有元素都排好序 。

```python
## Insertion Sort Algorithm

def insertion_sort(the_list):
    length = len(the_list)
    for i in range(length):
        for n in range(i, 0, -1):
            if the_list[n] < the_list[n-1]:
                the_list[n], the_list[n-1] = the_list[n-1], the_list[n]
            else:
                break
    return the_list


## test
test_list = [0, 1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 0, 5, 7, 7]
insertion_sort(test_list)
print(test_list)
```

三 希尔排序
------------------------
希尔排序(Shell Sort)是插入排序的一种。是针对直接插入排序算法的改进。该方法又称缩小增量排序，因DL．Shell于1959年提出而得名。

```python
## Shell Sort Algorithm

def shell_sort(the_list):
    n = len(the_list)
    h = 1
    while h < n//3:
        h = h * 3 + 1
    while h >= 1:
        for i in range(1, n, 1):
            if i < h:
                break
            for j in range(i, h-1, -h):
                if the_list[j] < the_list[j-h]:
                    the_list[j-h], the_list[j] = the_list[j], the_list[j-h]
                else:
                    break
        h = h //3
    return the_list


## test
test_list = [0, 1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 0, 5, 7, 7]
shell_sort(test_list)
print(test_list)
```

四 合并排序
-------------------
合并排序是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。合并排序法是将两个（或两个以上）有序表合并成一个新的有序表，即把待排序序列分为若干个子序列，每个子序列是有序的。然后再把有序子序列合并为整体有序序列。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为2-路归并。合并排序也叫归并排序。

```python
## Merge Sort Algorithm

class MergeSort(object):
    def __init__(self, array):
        self._array = array
        self._aux = [None] * len(array)
        
    def __merge(self, lo, mid, hi):
        i = lo
        j = mid + 1
        for k in range(lo, hi+1):
            self._aux[k] = self._array[k]        
        for k in range(lo, hi+1, 1):
            if i > mid:
                self._array[k] = self._aux[j]
                j += 1
            elif j > hi:
                self._array[k] = self._aux[i]
                i += 1
            elif self._aux[i] < self._aux[j]:
                self._array[k] = self._aux[i]
                i += 1
            else:
                self._array[k] = self._aux[j]
                j += 1

    def __sort(self, lo, hi):
        if lo >= hi:
            return
        mid = lo + ((hi - lo) // 2)
        self.__sort(lo, mid)
        self.__sort(mid+1, hi)
        self.__merge(lo, mid, hi)

    def sort(self):
        self.__sort(0, len(self._array)-1)

    @property
    def array(self):
        return self._array


## test
arr = [0, 1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 0, 5, 7, 7]
test_sort = MergeSort(arr)
test_sort.sort()
print(test_sort.array)
```

五 快速排序
----------------------
快速排序（Quicksort）是对冒泡排序的一种改进。由C. A. R. Hoare在1962年提出。它的基本思想是：通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列。

```python
## Quick Sort Algorithm

def partition(array, lo, hi):
    i = lo
    j = hi + 1
    while(True):
        i += 1
        while array[i] < array[lo]:
            if i == hi:
                break
            i += 1
        j -= 1
        while array[j] > array[lo]:
            if j == lo:
                break
            j -= 1
        if i >= j:
            break
        array[i], array[j] = array[j], array[i]

    array[lo], array[j] = array[j], array[lo]
    return j


def sort(array, lo, hi):
    if lo >= hi:
        return
    index = partition(array, lo, hi)
    sort(array, lo, index - 1)
    sort(array, index + 1, hi)


def quick_sort(array):
    sort(array, 0, len(array) - 1)


## test
arr = [0, 1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 0, 5, 7, 7]
quick_sort(arr)
print(arr)
```

六 堆排序
--------------------
堆排序(Heapsort)是指利用堆积树（堆）这种数据结构所设计的一种排序算法，可以利用数组的特点快速定位指定索引的元素。堆分为大根堆和小根堆，是完全二叉树。大根堆的要求是每个节点的值都不大于其父节点的值，即A[PARENT[i]] >= A[i]。在数组的非降序排序中，需要使用的就是大根堆，因为根据大根堆的要求可知，最大的值一定在堆顶。

```python
## Heap Sort Algorithm

def sink(pq, k, end_num):
    while 2*k < end_num:
        j = 2 * k
        if pq[j] < pq[j+1]:
            j += 1
        if pq[k] > pq[j]:
            break
        pq[k], pq[j] = pq[j], pq[k]
        k = j


def heap_sort(pq):
    end_num = len(arr) - 1
    for k in range(end_num//2, 0, -1):
        sink(pq, k, end_num)
        

    while end_num > 1:
        pq[1], pq[end_num] = pq[end_num], pq[1]
        end_num -= 1
        sink(pq, 1, end_num)
        
        

## test
arr = [0, 1, 3, 1, 4, 2, 4, 2, 3, 2, 4, 7, 6, 6, 7, 5, 0, 5, 7, 7]
arr.insert(0, None)
heap_sort(arr)
arr.pop(0)
print(arr)
```


以上都是比较常见的排序算法，利用Python写出来，可以像伪代码一样好理解。

{{ page.date | date: "%Y-%m-%d" }}
