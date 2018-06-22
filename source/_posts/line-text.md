---
title: 单行/多行文本溢出  用点展示
date: 2018-06-02 16:35:06 
tags: 前端知识
categories: css笔记
---

单行文本：white-space:nowrap;(禁止换行,强制一行显示)
       overflow:hidden; (超出部分隐藏)
       text-overflow:ellipsis;(文本溢出以...显示)

多行文本：  display: -webkit-box;
           -webkit-box-orient: vertical;
           -webkit-line-clamp: 2; //这里是在第二行有省略号
           overflow: hidden;      