---
title: 主流浏览器及其内核
date: 2018-06-04 16:35:06 
tags: 前端素养
categories: 前端素养
---

一般说的浏览器内核是指浏览器最重要的核心部分，RenderingEngine，翻译成中文大概意思就是“解释引擎”，我们一般称为浏览器内核。由于不同的内核各自有一套自己的渲染网页和解释页面代码的机制，所以就会有一些问题存在。

首先，都有哪些浏览器呢？

谷歌浏览器：Google Chrome。

火狐浏览器：Mozilla Firefox。

欧鹏浏览器：OPera。

苹果浏览器：Safari。

IE浏览器：Windows Internet Explorer。

国内一些整合的浏览器：搜狗高速浏览器、傲游浏览器、猎豹安全浏览器、QQ浏览器、360极速浏览器、世界之窗浏览器极速版、百度浏览器 等。

 

其次，它们的内核又是什么呢？

谷歌浏览器：Google Chrome，谷歌浏览器之前一直使用苹果的webkit内核，但是现在它与苹果内核分道扬镳，自己开创了新的blink内核，这个内核也在被欧朋（opera浏览器）共同采用和开发；

火狐浏览器：Mozilla Firefox ，内核是Gecko；

opera浏览器：内核是blink；

Safari浏览器：使用的是苹果公司自己的内核:webkit。

IE浏览器是微软出品的浏览器，IE4以上版本都是Trident内核。由于垄断性，IE在很长一段时间内没有更新，导致两个后果：一是IE与W3C标准脱节，二是Trident内核大量的bug问题没得到及时解决。所以这就给了其他浏览器机会，比如firefox等。也正是这些原因，使Web前端开发人员大费折，特别是IE6正处在新旧交替的关键地方（已经逐渐被舍弃）.

 

一些国内的浏览器他们的内核： 
搜狗浏览器：兼容模式（IE：Trident）和高速模式（webkit） 
傲游浏览器：兼容模式（IE：Trident）和高速模式（webkit） 
QQ浏览器：普通模式（IE：Trident）和极速模式（webkit） 
360极速浏览器：基于谷歌（Chromium）和IE内核 
360安全浏览器：IE内核
