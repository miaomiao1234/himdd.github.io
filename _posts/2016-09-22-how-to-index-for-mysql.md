---
layout: post
title:  "mysql索引建立规则"
date:   2016-09-22 21:26:24 +0800
categories: himdd update
---

## 问题
  [点击查看](http://stackoverflow.com/questions/2386852/mysql-low-cardinality-selectivity-columns-how-to-index)

## 索引建立准则：

- 能筛选出较少的行数的字段放前面。
- 如果区分度太小的字段可以不建立索引，如`status`只有两三种值。

## select
- 能筛选出较少的行数的条件放前面。
- mysql 会优化where顺序
