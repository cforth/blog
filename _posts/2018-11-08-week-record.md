---
layout: default
title: 每周记录第9期
excerpt: 改进CFCryoto的加密解密模式。
tags: [Thinking]
---
{{ page.title }}
================

在每周记录第2期里，我说尝试将CFCrypto的加密解密改成使用AES的CBC模式。后来几周我都没有完成这个事情，本周我完成了改进。

实施起来并不困难，CBC模式的安全性更高，但是加密解密速度没有原来使用ECB模式快了。目前我放在了[CFX](https://github.com/cforth/codefarm/blob/master/idea-365/D020_CFCrypto/CFX.py)这个项目里面了，这是[测试用例](https://github.com/cforth/codefarm/blob/master/idea-365/D020_CFCrypto/test_cfx.py)。考虑到数据的兼容性问题，暂时不把CryptoApp的加密解密模式改成CBC模式。

下周的目标是，继续改进CryptoApp的窗口界面，使之使用起来更加方便。

{{ page.date | date: "%Y-%m-%d" }}
