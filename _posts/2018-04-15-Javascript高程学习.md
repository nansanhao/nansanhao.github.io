---
layout:     post
title:      Javascript高程学习
subtitle:   本文是笔者学习Javascript的一些笔记。
date:       2018-04-15
author:     南三号
header-img: img/post-bg-js-version.jpg
catalog: true
tags:
    - Javascript
---

- 定义函数的方式：
  - 函数声明
  - 函数表达式（匿名函数）
- 函数声明提升
  - 函数声明总是在执行代码之前
- 函数表达式定义：先赋值再用
- 注意，JavaScript 只在一个线程上运行，不代表 JavaScript 引擎只有一个线程。事实上，JavaScript 引擎有多个线程，单个脚本只能在一个线程上运行（称为主线程），其他线程都是在后台配合。 
- 为了利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程，但是子线程完全受主线程控制，且不得操作 DOM。所以，这个新标准并没有改变 JavaScript 单线程的本质。  
- 事件循环机制：不停地检查，一遍又一遍，只要同步任务执行完了，引擎就会去检查那些挂起来的异步任务，是不是可以进入主线程了 
- 标签内不能出现标签的结束标签，否则浏览器会认为是结束的标签。如果要使用应添加转移字符`/`,例如`<\/script>`
- 延迟脚本会在加载到`<\html>`标签后进行下载，并且不一定会按照顺序加载，所以最好包含一个延迟脚本。
- 多个异步脚本的加载顺序并不会按照出现的先后顺序加载，所以必须保持多个异步脚本的互不依赖。
- noscript标签：当浏览器不支持JavaScript时显示标签内的内容。
- `undefined`值派生自`null`，所以null==undefined返回值为true
- NaN：not a number
- js函数参数数量不一定和函数定义的数量相同。
- 函数没有重载。

































































































