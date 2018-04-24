---
layout:     post
title:      getElementsByName返回的数组和数组的差别
subtitle:   本文是笔者参加面试没有回答好的问题。
date:       2017-09-28
author:     南三号
header-img: img/post-bg-swift2.jpg
catalog: true
tags:
    - JavaScript
---

**getElementsByName**返回的是一个“伪数组”，或者叫做集合，它可以遍历但不能够使用数组的push等方法。
但是相应的会有多的添加的一些操作这些节点对象的方法。
如想对get到的结构进行数组相关的操作，就必须要将其转换成数组。

```javascript
var elems = document.getElementsByTagName(some tag),
elearr = Array.prototype.slice.call(elems);
```
之后就可以操作`elearr`这个真正的数组了。