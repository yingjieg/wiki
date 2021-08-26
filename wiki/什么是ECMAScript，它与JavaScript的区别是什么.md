# 什么是ECMAScript，它与JavaScript的区别是什么？

提起ES5， ES6（ES2015），大家一定不会陌生，现代前端开发中，越来越多的人都开始使用ES6或者TypeScript来开发自己的产品，但是说到ECMAScript与JavaScript的关系，相信很多人不是很清楚。

让我们来Google一下ECMAScript和JavaScript，结果众说纷纭，看看下面的一些解释，是不是更加混乱了。

> ECMAScript是标准
JavaScript是标准
ECMAScript是规范
JavaScript是ECMAScript标准的实现
ECMAScript是标准化的JavaScript
ECMAScript是一门语言
JavaScript是ECMAScript的一种语言变种
ECMAScript就是JavaScript

如果想要理解ECMAScript和JavaScript的关系，就要先从__ECMA国际__说起：

__“ECMA International” - ECMA国际，是一个专门为技术制定标准的组织。__

在1997年6月， 该公司发布了一个标准 - __ECMA-262__

ECMA-262作为一个标准，它为通用编程语言（ECMAScript）定义了相关的规范。
所以，ECMA-262是标准的名称，它的内容描述了**ECMAScript语言规范（ECMAScript Language Specification）**。

在ECMA-262中有以下描述:

> ECMAScript is an object‑oriented programming language for performing computations and manipulating
computational objects within a host environment.

ECMAScript是面向对象的编程语言

> ECMAScript was originally designed to be used as a scripting language, but has become widely used as a
general‑purpose programming language

起初，ECMAScript是作为网页脚本语言设计的，但是却逐渐演变成了广泛使用的通用型编程语言。

所以，我们得到了如下结论：

* ECMA-262是ECMA国际发的一个技术标准。
* ECMAScript是一种编程语言。
* ECMA-262中，为ECMAScript这门编程语言定义了规范。

现在回过头来看JavaScript，就简单了。
JavaScript是一门遵循了**ECMA-XXX标准**而设计的编程语言。

最后一个问题，那ES5，ES6，ES7...又是什么呢？
它们是ECMA-262标准的版本号。

| Name | Release date | Description |
| ------------- | ------------- | ------------- |
| ECMA-262 5th Edition | December 2009 | ECMAScript Language Specification. This is the fifth revision of the ECMAScript standard. |
| ECMA-262 6th Edition | June 2015 | ECMAScript 2015 Language Specification |
| ECMA-262 7th Edition | June 2016 | ECMAScript 2016 Language Specification |
| ECMA-262 8th Edition | June 2017 | ECMAScript 2017 Language Specification |

2015年ECMA国际决定每年发布一个版本，所以ES6被重命名为ES2015，用来体现发布的年份，所以ES6和ES2015是一个意思，以后每年的版本我们称为ES2016，ES2017，ES2018。
