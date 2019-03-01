---
title: js基础知识___变量
date: 2018-01-31 22:19:47
tags:
    - javascript
---

## js基础 - 变量 ##
*大家对js一定不会陌生，入门很简单（普通入门），很多人通过网络资源、书籍、课堂等很多途径学习js，但是有些js基础的只是往往被大家遗漏，本章就从js变量类型来说一说js
### 变量类型*
    
   js变量类型分为基本类型（或者叫值类型）和引用类型。值类型包括Number、Boolean、String、undefined、 null、Symbol (ES6 新增)。  引用类型包括Object 、Array、Function、Date、RegExp，值类型存放在栈内存中，引用类型的数据是存放在堆内存中。

值类型的数据在复制的时候会在栈内存中新建一个新的存储区域用来存储新的变量，和之前的值没有任何关系。比如如下例子：

```
var a = 'a'
var b = a
b = 'b'
console.log(a) // 'a'
```
当b的值改变的时候，a的值不会跟着改变。这个很简单，大家也都能理解。

下面说一下引用类型，定义一个对象的时候会在栈内存中存储了一个指针，该指针指向堆内存中该对象的存储地址，当复制这个对象赋值给另一个对象的时候，只是把该对象的指针地址赋值给了另一个对象变量，他们都指向同一个对象，所以当一个值改变的时候，另一个值会跟着改变，看下面的例子就会明白：

```
var obj1 = {name:'obj1'}
var obj2 = obj1
obj2.name = 'obj2'
console.log(obj1.name) // 'obj2'
```
大家可以执行一下上面的代码，打印obj1.name的时候输出'obj2',这就是因为对象是引用类型的变量。

### JavaScript内置函数和对象

js中内置了一些函数和对象，很多语言都会有内置的方法，直接可以调用开发。
根据ECMAscript（javascript语法标准）提供的内置函数包括Object、Array、Boolean、Number、String、Function、Date、Regexp和Error。内置对象包括Math和JSON。

> 注意：javascript基础语法提供的内置函数和方法只有这些，像Window、Navigator那是浏览器提供给我们的。还有一点前面的集中都是内置函数而不是内置对象，最后的Math和JSON是内置对象，这个在我们以后的章节讲原型链的时候就明白了，这里先记住就OK了。

## 几个常见问题

### 何时使用使用==何时使用===

这个问题大家应该都不陌生，在开发或者面试中会经常碰见的问题。那么答案到底是什么呢？
首先看到这个问题的时候先不要去想到底那些情况使用==那些情况使用===，我们应该首先去想这个问题背后涉及到那些知识点。很显然，这里考的就是强制类型转换，在使用==得时候会强制类型转换，而使用===的时候不会发生强制类型转换。强制类型转换大家应该都知道。下面我们总结一下：
在if()条件判断中0、""、NaN、null、undefined、false都会转为false，判断对象的一个属性存在可以使用如下语法：

```
var obj = {}
if(obj.name == null){...} // 相当于obj.name === null || obj.name === undefined
/* 该方法只适用于判断对象的属性，不能用于直接判断变量是否存在 */
if(someVal){...} // 这里浏览器会报错
```

标准答案是：只有在判断一个对象的属性是否存在的时候使用==，其他都使用===。

### typeof能否准确判断变量类型

这里首先想到的是对typeof和变量类型的理解，由于typeof只能区分基本类型的变量，所以不能准确的判断变量类型。

```
Undefined  -- Undefined  
Boolean    -- Boolean
Number     -- Number     
String     -- String


----------
Object     -- Object
Function   -- Function
Array      -- Object
null       -- Object

```

所以答案是typeof只能判断值类型的变量，不能判断引用类型的变量，要想准确判断变量的类型，可以在以后的原型的章节中介绍


    