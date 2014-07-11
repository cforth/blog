---
layout: default
title: MySQL安装小记（windows版）
excerpt: 这两天安装和使用了MySQL数据库，主要目的是做一些简单的数据操作。
tags: [IT]
---
{{ page.title }}
================

这两天安装和使用了MySQL数据库，主要目的是做一些简单的数据操作。

安装的话，在MySQL官网上下载最新的5.6版。我只安装了Server端和Workbench客户端。本地环境是Windows XP，在安装完成后可以通过Windows服务来启动和停止mysqld服务。安装过程都很顺利，没有问题。

对于建立新的数据库，建立表格，经过摸索也很顺利的做完了。记录下用到的命令:

/* 建立新表 */
CREATE TABLE mytable.20131011(      /* 以日期建立新表 */
        ID INT(100) NOT NULL ,              /* INT格式 */
        NAME VARCHAR(100),          /* 字符串格式 */
        ADDRESS VARCHAR(100),   /* 字符串格式*/
        INDEX ( ID)                 /* 以ID列做INDEX */
);

/* 从外部CSV文件导入数据表中，默认使用gbk字符集，需改进！！ */
load data infile '/temp/20131010.csv'
into table mytable.20131010 character set gbk
fields terminated by ','  optionally enclosed by '"' escaped by '"' 
lines terminated by '\r\n';

/* 将两张表合并，注意有显示数目限制，需改进！！ */
select a.*, b.t1 from mysql1.mytable1 a left join mysql1.mytable2 b on a.id = B.id limit 500

P.S.目前还不知道如何将表合并后存入新表，会继续学习！

{{ page.date | date: "%Y-%m-%d" }}
