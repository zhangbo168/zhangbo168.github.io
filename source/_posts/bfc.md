---
title: 弥补盒子塌陷（margin）改变BFC
date: 2018-06-06 20:59:02
tags: 前端知识
categories: css笔记
---

### 看下面代码（嵌套关系）

理想情况下是黑色盒子往下移动50px,但是我们发现他并没有变化
``` bash
        <style>
            .warpper{
                height: 200px;
                width: 200px;
                background: red;
            }
            .warpper .main{
                height: 100px;
                width: 100px;
                background:#000;
                margin-top:50px;
            }
        </style>
        <div class="warpper">
            <div class="main"></div>
        </div>
```
![](1.png)

怎么解决呢？通过改变父级BFC,黑色盒子往下移动了50px

``` bash
        <style>
            .warpper{
                display:inline-block;
                height: 200px;
                width: 200px;
                background: red;
            }
            .warpper .main{
                height: 100px;
                width: 100px;
                background:#000;
                margin:50px;
            }
        </style>
        <div class="warpper">
            <div class="main"></div>
        </div>
```
![](2.png)


那么 BFC 是什么呢？

BFC 即 Block Formatting Contexts (块级格式化上下文)，它属于上述定位方案的普通流。

具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。

通俗一点来讲，可以把 BFC 理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。

### 更多改变BFC的方案：
绝对定位元素：position (absolute、fixed)
display 为 inline-block、table-cells、flex
overflow 除了 visible 以外的值 (hidden、auto、scroll)
浮动元素：float 除 none 以外的值
