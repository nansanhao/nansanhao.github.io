---
layout:     post
title:      Javascript单体内置对象
subtitle:   本文是笔者学习Javascript的一些笔记。
date:       2018-04-10
author:     南三号
header-img: img/post-bg-js-version.jpg
catalog: true
tags:
    - Javascript
---

## JavaScript除Object，String，Array之外还有两个单体内置对象

- Global对象：不属于任何其他对象的方法，都是属于它的方法。终极兜底对象。
  - 方法：
    - isNaN( )
    - isFinite( ）
    - parseInt( )
    - parseFloat( )
    - URI编码方法
      - encodeURI( )
      - encodeURIComponet( )
    - eval( )
      - 像是一个完整的ECMASctript解析器
    - Window对象：在全局作用域声名的所有变量和函数，都成为Window对象的属性。是用来访问Global对象而存在的。
- Math对象