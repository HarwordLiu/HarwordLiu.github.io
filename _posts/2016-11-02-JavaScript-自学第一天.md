---
layout: post
title: JavaScript自学第一天 - HarwordLiu
date: 2016-11-02 21:32:24.000000000 +08:00
---
# [JavaScript](https://zh.wikipedia.org/zh-hans/JavaScript) 简介
`JavaScript`是`Web`的编程语言。

所有现代的`HTML`页面都使用`JavaScript`。

更可广泛用于服务器、PC、笔记本电脑、平板电脑和智能手机等设备。

博主主业iOS开发, 不过就目前移动端的趋势, 

仿佛`JavaScript`已经主宰了三端的开发。

混合开发的优势实在是太明显了。所以该学的要学啊!

学习`JavaScript`要有`HTML`和`CSS`的基础

因为大部分实例都是通过web来演示的

## JavaScript 是脚本语言
`JavaScript` 是一种轻量级的编程语言。

`JavaScript` 是可插入 HTML 页面的编程代码。

`JavaScript` 插入 HTML 页面后，可由所有的现代浏览器执行。

`JavaScript` 很容易学习。(瞎比说的 ...)

## JavaScript 能干什么?
>直接写入HTML输出流
>
>对交互事件作出相应反应
>
>改变HTML内容
>
>改变HTML中的图片
>
>验证输入
>
>...

## JavaScript != Java
`JavaScript` 与 `Java` 是两种完全不同的语言，无论在概念上还是设计上。

`Java`（由 Sun 发明）是更复杂的编程语言。

`ECMA-262` 是 `JavaScript` 标准的官方名称。

`JavaScript` 由 `Brendan Eich` 发明。
它于 1995 年出现在 `Netscape` 中（该浏览器已停止更新），并于 1997 年被 `ECMA`（一个标准协会）采纳。

# JavaScript 用法
`HTML` 中的脚本必须位于 `<script>` 与 `</script>` 标签之间。
脚本可被放置在 `HTML` 页面的 `<body>` 和 `<head>` 部分中。


## \<script>标签
如需在 `HTML` 页面中插入 `JavaScript`，请使用 `<script>` 标签。
`<script>` 和 `</script>` 会告诉 `JavaScript` 在何处开始和结束。
`<script>` 和 `</script>` 之间的代码行包含了 `JavaScript`:

	<script>
	alert("我的第一个 JavaScript");
	</script>
	


##\<body> 中的 JavaScript



	<!DOCTYPE html>
	<html>
	<body>
	.
	.
	<script>
	document.write("<h1>这是一个标题</h1>");
	document.write("<p>这是一个段落</p>");
	</script>
	.
	.
	</body>
	</html>



##在 \<head> 或者 \<body> 的JavaScript	
可以在 HTML 文档中放入不限数量的脚本。
脚本可位于 HTML 的 <body> 或 <head> 部分中，或者同时存在于两个部分中。
通常的做法是把函数放入 <head> 部分中，或者放在页面底部。这样就可以把它们安置到同一处位置，不会干扰页面的内容。

**\<head>**

	<!DOCTYPE html>
	<html>
	<head>
	<script>
	function myFunction()
	{
	document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
	}
	</script>
	</head>
	<body>
	<h1>我的 Web 页面</h1>
	<p id="demo">一个段落</p>
	<button type="button" onclick="myFunction()">尝试一下</button>
	</body>
	</html>
	
**\<body>**
	
	<!DOCTYPE html>
	<html>
	<body>
	<h1>我的 Web 页面</h1>
	<p id="demo">一个段落</p>
	<button type="button" onclick="myFunction()">尝试一下</button>
	<script>
	function myFunction()
	{
	document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
	}
	</script>
	</body>
	</html>
	


##加载外部的 JavaScript
可以把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码。
外部 `JavaScript` 文件的文件扩展名是 .js。
如需使用外部文件，请在 `<script>` 标签的 `src` 属性中设置该 .js 文件：

	<!DOCTYPE html>
	<html>
	<body>
	<script src="myScript.js"></script>
	</body>
	</html>


#JavaScript 输出
JavaScript 没有任何打印或者输出的函数。

JavaScript 可以通过不同的方式来输出数据：

>1. 使用 window.alert() 弹出警告框。
>2. 使用 document.write() 方法将内容写到 HTML 文档中。
>3. 使用 innerHTML 写入到 HTML 元素。
>4. 使用 console.log() 写入到浏览器的控制台。


#JavaScript 语法
JavaScript 是一个程序语言。语法规则定义了语言结构。

JavaScript 是一个脚本语言。它是一个轻量级，但功能强大的编程语言。

##JavaScript 字面量
**数字（Number）字面量** 可以是整数或者是小数，或者是科学计数(e)。

	3.14
	1001
	123e5
	
**字符串（String）字面量** 可以使用单引号或双引号:

	"John Doe"
	'John Doe'
	
**表达式字面量** 用于计算：

	5 + 6
	5 * 10

**数组（Array）字面量** 定义一个数组：

	[40, 100, 1, 5, 25, 10]

**对象（Object）字面量** 定义一个对象：

	{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

**函数（Function）字面量** 定义一个函数：

	function myFunction(a, b) { return a * b;}


##JavaScript 变量
JavaScript 使用关键字 var 来定义变量， 使用等号来为变量赋值：

	var x, length;
	x = 5;
	length = 6;

>变量可以通过变量名访问。

>在[指令式语言](https://zh.wikipedia.org/wiki/%E6%8C%87%E4%BB%A4%E5%BC%8F%E7%B7%A8%E7%A8%8B)中，变量通常是可变的。字面量是一个恒定的值。
	
##JavaScript 操作符

类型|实例|描述
----|-----|-----
赋值，算术和位运算符|=  +  -  *  /|在 JS 运算符中描述
条件，比较及逻辑运算符|== === != < > >= <= && \|\| !|在 JS 比较运算符中描述

##JavaScript 语句
在 HTML 中，JavaScript 语句向浏览器发出的命令。
语句是用分号分隔`;`
##JavaScript 关键词
JavaScript 语句通常于关键词为开头。 var 关键词告诉浏览器创建一个新的变量：

	var x = 5 + 6;
	var y = x * 10;


##JavaScript 关键字
和其他任何编程语言一样，JavaScript 保留了一些关键字为自己所用。
JavaScript 同样保留了一些关键字，这些关键字在当前的语言版本中并没有使用，但在以后 JavaScript 扩展中会用到。
JavaScript 关键字必须以字母、下划线（_）或美元符（$）开始。
后续的字符可以是字母、数字、下划线或美元符（数字是不允许作为首字符出现的，以便 JavaScript 可以轻易区分开关键字和数字）。


##JavaScript 注释
使用`//`进行注释

##JavaScript 数据类型
JavaScript 有多种数据类型：数字，字符串，数组，对象等等：

	var length = 16;                                  // Number 通过数字字面量赋值 
	var points = x * 10;                              // Number 通过表达式字面量赋值
	var lastName = "Johnson";                         // String 通过字符串字面量赋值
	var cars = ["Saab", "Volvo", "BMW"];              // Array  通过数组字面量赋值
	var person = {firstName:"John", lastName:"Doe"};  // Object 通过对象字面量赋值


##JavaScript 函数
JavaScript 语句可以写在函数内，函数可以重复引用：

**引用一个函数** = 调用函数(执行函数内的语句)。

	function myFunction(a, b) {
		return a * b;                                // 返回 a 乘于 b 的结果
	}


##JavaScript 对大小写敏感。
JavaScript 对大小写是敏感的。
当编写 JavaScript 语句时，请留意是否关闭大小写切换键。
函数 getElementById 与 getElementbyID 是不同的。
同样，变量 myVariable 与 MyVariable 也是不同的。


##JavaScript 字符集
JavaScript 使用 Unicode 字符集。
Unicode 覆盖了所有的字符，包含标点等字符。


##总结
第一篇笔记就先到这里





