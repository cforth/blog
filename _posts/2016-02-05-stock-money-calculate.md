---
layout: default
title: 股票补仓问题计算
excerpt: 使用python计算出每次股票下跌后需要补仓多少资金。
tags: [Coding]
---
{{ page.title }}
================

设股票市值为x,跌停次数是n次，需补仓f(n)，才能满足一次涨停就全部回本。通过python中的计算，发现满足以下规律：

```bash
n=1, f(1) = 0.1 * x
n=2, f(2) = 1.1 * x
n>2, f(n) = f(n-1) * 2
```

使用python3实现了这个股票补仓的计算，并且保存到表格中。还利用matplotlib库把曲线图画了出来，代码如下：

```python
# coding: utf-8
import csv
import matplotlib.pyplot as plt

market_value = 1
money = 0
sum_money = 1
money_list = []
plt_list = []
drop = 0

for n in range(1, 21):
    money = (sum_money - 0.99 * market_value) * 10
    market_value = 0.9 * market_value + money
    sum_money = sum_money + money

    drop= 1 - 0.9**n
    plt_list.append(round(money, 2))
    money_list.append((n, round(drop, 2), round(money, 2), round(sum_money,2), round(market_value,2), round(market_value*1.1,2)))

headers = ['跌停次数','总跌幅','本次补仓','总成本','补仓后的市值', '补仓后涨停时的市值']

with open('stock.csv', 'w') as f:
    f_csv = csv.writer(f,lineterminator='\n')
    f_csv.writerow(headers)
    f_csv.writerows(money_list)


plt.plot(plt_list)
plt.xlabel('days')
plt.ylabel('money')
plt.show()
```

通过补仓曲线发现，补仓资金是一个指数级的放大过程。所以在股市连续下跌中，传统的越跌越买的补仓方法不一定是好的，及时止损才正确。

![stock_money](http://img3.douban.com/view/photo/photo/public/p2316690140.jpg)

{{ page.date | date: "%Y-%m-%d" }}
