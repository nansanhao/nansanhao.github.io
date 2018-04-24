---
layout:     post
title:      Javascript的垃圾回收机制
subtitle:   本文是笔者学习Javascript的一些笔记。
date:       2018-04-10
author:     南三号
header-img: img/post-bg-js-version.jpg
catalog: true
tags:
    - Javascript
---

## JavaScript的垃圾回收机制

## 将没有必要存在的变量所占用的内存回收

- 标记清除（最常用）

  - 进入环境
  - 离开环境
  - 标记方式：
    - 反转某个特殊的位
    - 建立标记状态表
- 引用计数

    - 存在的问题：循环引用
    - IE中DOM和BOM中的对象是使用c++以COM对象实现的，就采用的是引用计数。可以通过手工切断原生js对象与DOM对象的连接。（在IE９中已经得到解决）
    - 性能问题：垃圾回收机制是周期运行的。在什么时候执行将是一个十分重要的问题，IE７之后采用设定临界值动态修正的方法。
    - 解除引用：设值为NULL。

