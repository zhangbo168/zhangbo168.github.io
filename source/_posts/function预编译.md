---
title: 浅谈JavaScript预编译原理
date: 2018-06-11 16:38:06 
tags: 前端知识
categories: javascript笔记
---

这两天又把js的基础重新复习了一下，很多不懂得还是得回归基础,大家都知道js是解释性语言，就是编译一行执行一行，但是在执行的之前，系统会做一些工作:

1,语法分析；

2,预编译；

3,解释执行。

语法分析很简单，就是引擎会简单的检查一下你的代码有没有什么低级的错误，解释执行就是执行代码，执行代码之前会进行预编译，预编译简单理解就是在内存中开辟一些空间，存放一些变量与函数。下面我详细说一下：

### 预编译可以简单的分成全局预编译和函数体预编译，函数体预编译可以从四个规则入手;

#### 1,创建AO对象;AO{  }

#### 2,找形参和变量声明，将变量和形参名作为AO的属性名，并赋值为undefined

#### 3,将实参和形参统一；

#### 4,在函数里找函数声明  ，赋值函数体。

记住以上四条规则，下面通过一个简单的案列说明一下：

```bash
    function test(){
        console.log(a);
        console.log(b);
        var b = 234;//变量声明
        console.log(b);
        a = 123;//变量声明
        console.log(a);
        function a(){}//函数声明
        var a;
        b = 257;
        var b = function (){}//变量声明
        console.log(a);
        console.log(b);
        function c(y){//函数声明
        var y = 1;
        };             
    }
        test(1)
```

让我们看看引擎对这段代码做了什么吧
1,创建AO对象;Activation Object AO{  }
2,找形参和变量声明，将变量和形参名作为AO的属性名，并赋值为undefined
```bash
    AO{
        b:undefined;
        a:undefined;
    
    }
```
3,将实参和形参统一；
4,在函数里找函数声明  ，赋值函数体。所以此时的a会被函数体替代
```bash
AO{
    a:function a(){}
    b:undefined
    c:function c(y){
    var y = 1;
    }
}
```
当页面预处理完之后便会开始执行,根据编译一句执行一句的原则,此时console.log(a)的值自然为:function a(){},console.log(b)的值为:undefined.
随后b被赋值为234,所以第二个console.log(b)的值为:234,以此类推,第二个console.log(a)的值为:123,
b经历了第三次赋值257后,又被function(){}赋值,所以最后console.log(b)的值为:function(){},console.log(a)的值为:123.

### 全局预编译比函数体预编译少了第三条：

#### 1,创建GO对象;即global objetct GO{  }

#### 2,找形参和变量声明，将变量和形参名作为AO的属性名，并赋值为undefined

#### 4,在函数里找函数声明  ，赋值函数体。

下面也通过一个简单的列子解释一下：

```bash
    function test(){
        console.log(b);//undefined
        if(a){
            var b = 100;
        }
        console.log(b)//undefined
        c = 456;
        console.log(c);//456
    }
    var a;
    console.log(a)////undefined
    test();  
    a = 10;
    console.log(a)//10
    console.log(c)//456
```
    
首先定义创建GO对象,随后将变量和形参作为属性名,并赋值为undefined,如下:
    ```bash
        GO{
            a:undefined;
            c:undefined;
          }
    ```
然后在函数生命里赋值函数体,但此时没有函数体,所以不用赋值,
下面就是开始执行语句,所以一第个console.log(a)为undefined;第二个为10,c为456(注意此时c没有命名,直接提升为全局变量)
当执行到test()的时候会主动预编译function test()里面的内容,此时会创建AO对象.