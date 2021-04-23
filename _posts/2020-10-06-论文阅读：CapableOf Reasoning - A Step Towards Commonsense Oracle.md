---
layout:     post
title:      阅读 CapableOf Reasoning - A Step Towards Commonsense Oracle
subtitle:   阅读 CapableOf Reasoning - A Step Towards Commonsense Oracle所做的笔记。
date:       2020-09-28
author:     南三号
header-img: img/KG-3.jpg
catalog: true
tags:
    - 知识图谱
    - 机器学习	
    - 常识
---

# 论文阅读

> ### 论文：[CapableOf Reasoning - A Step Towards Commonsense Oracle](https://dl.acm.org/doi/abs/10.1145/3397271.3401251)
>
> 主要内容：对知识图谱常识性知识（Commonsense knowledge）的研究，构建了一个可以判断某个实体是否具有某种能力的模型。

常识性知识作为更加基础、更为一般化的知识，很容易被人类理解并掌握，但对于机器而言却并非如此。在知识图谱中，一般性的知识是从大量的语料中获得的，这些语料作为人类的知识成果，包含了各种各样的知识，却少有显性涉及一些常识性的知识，因为这些默认的知识作为背景，隐性的潜藏在语料的背后，机器很难对其发掘，这也导致知识图谱“很有知识”但“缺乏常识”。

本篇论文对于`某个实体有某种能力`这类常识进行研究。例如`plants cannot sing`和`singers can sing`

#### 构建两个数据集

这些数据集都是由一条条`某个实体有某种能力`这种命题所组成。

只对14个能力进行判断，分别是： fly, sleepdie, eat, burn, walk, grow, run, work, breathe, swim, think, read, sing

1. 基于图关系的数据集：依据实体`s`和能力`t`在图中的关系链还有逆关系等进行推理

2. 基于Web搜索引擎的数据集：

   - web检索的统计数据：把实体`s`和能力`t`嵌入到预先定义的匹配模板中，在搜索引擎中搜索，记录检索结果的条数作为统计量，再通过公式转化为特征值。

     三类查询模板：

     | Category          | Template Details                                             |
     | ----------------- | :----------------------------------------------------------- |
     | direct filling    | [𝑠] [𝑡], [𝑠] can [𝑡], [𝑠] cannot [𝑡], [𝑠] cant [𝑡], [𝑠] dont [𝑡] |
     | composed question | when [𝑠] [𝑡], when [𝑠] can [𝑡], why [𝑠] [𝑡], why [𝑠] can [𝑡], how [𝑠] [𝑡], how do [𝑠] [𝑡], how [𝑠] can [𝑡], should [𝑠] [𝑡], some [𝑠] [𝑡], some [𝑠] can [𝑡] |
     | other templates   | [𝑠] [𝑡] game, find a [𝑠] [𝑡], training [𝑠] [𝑡]               |

   - web检索的数据内容：通过预先定义的模板对检索结果的内容进行匹配，要得到内容的Result Type，Title Text，URL String。然后通过公式转化为特征值。

     三种模式匹配：

     | Content     | Pattern Details                                              |
     | ----------- | ------------------------------------------------------------ |
     | Result Type | [VIDEO], [PDF], [DOC]                                        |
     | Title Text  | !, can, can’t, cannot, game, cant, do, does, don’t, found a * can’t, found one * can’t<br />?, why, how, what, which, how * do *?,how * can *?, why * can’t *?, why * can *?, can *?, do *?<br />could, if, should, would |
     | URL String  | can, cannot, cant, why, how, which, do, game                 |

#### 构建分类器

是基于多个分类器（LR，RF，CNB，5-NN，MLP）的结果进行Hard Voting和Soft Voting得到最终的结果。

具体使用到的分类模型有：logistic regression (LR)，ran- dom forest (RF)，Complement Naïve Bayes (CNB)，5-Nearest Neighbor (5-NN)，and Multi-Layer Perception (MLP) neural network with four hidden layers

#### 数据标注

对数据集中的命题进行标注，即标注为真或者标注为假

采用了两种标注方法：

1. 从知识库ConceptNet中提取关于能力的三元组，然后将capableOf标注为true，将notCapableOf标注为false。标注完得到数据集GT-1
2. 人工标注得到数据集GT-2

#### 存在的不足

某些查询模板在放入实体和能力后，由于自然语言的模棱两可，可能会有一个消极的影响。

#### 一些概念

**Offline learning AND Online learning**

- 离线学习（offline learning）：即我们手中有全部的训练数据
- 在线学习（online learning）：数据可能是以流式的形式, 我们一次只能看到部分的数据, 我们只能根据目前看到的这部分的数据进行训练

**Hard Voting AND Soft Voting**

- Hard Voting：根据少数服从多数来定最终结果
- Soft Voting：将所有模型预测样本为某一类别的概率的平均值作为标准，概率最高的对应的类型为最终的预测结果

[**L1 normalization AND L2 normalization**](https://www.zhihu.com/question/26485586)











