---
layout:     post
title:      阅读 Mining Verb-Oriented Commonsense Knowledge
subtitle:   阅读 Mining Verb-Oriented Commonsense Knowledge所做的笔记。
date:       2020-10-20
author:     南三号
header-img: img/KG-3.jpg
catalog: true
tags:
    - 知识图谱
    - 机器学习	
    - 常识
---

# 论文阅读

> ### 论文：[Mining Verb-Oriented Commonsense Knowledge](https://ieeexplore.ieee.org/abstract/document/9101187)
>
> 主要内容：对动词常识的挖掘。取得了面向动词的18k常识。

[最小描述长度（Minimum Description Length](https://baike.baidu.com/item/%E6%9C%80%E5%B0%8F%E6%8F%8F%E8%BF%B0%E9%95%BF%E5%BA%A6)

`召回`指从全量信息集合中触发尽可能多正确的结果

- 召回率（Recall）= 系统检索到的相关内容 / 系统所有相关的内容总数
- 准确率（Precision）= 系统检索到的相关内容 / 系统所有检索到的内容总数

目的：想要得到关于动词的常识

方法：通过抽象动词的主语和宾语得到

抽象过程中，使用到两个部分

- 过滤“过度抽象的三元组”的过滤器
  - 使用到MDL来寻找合适的抽象程度
- 动词常识的生成器
  - 使用NLM来对生成的三元组进行可信度的测量

![](https://nansanhao.github.io\img-blog\verb-commonsense-1.png)





​	

