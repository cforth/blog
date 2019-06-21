---
layout: default
title: 每周记录第18期
excerpt: CryptoFactory支持密码验证。
tags: [Thinking]
---
{{ page.title }}
================

本周我为CryptoFactory中的加密解密类，增加了验证密码的功能。具体是加密时在文件头部增加一个标识，解密时首先验证这个标识是否正确，用来判断密码是否正确。

考虑到CryptoFactory还没有完成设计，所以暂时隐藏起来，转回Github私有库保存。

{{ page.date | date: "%Y-%m-%d" }}
