---
layout: post
title: JavaScript自学第三天 - HarwordLiu
date: 2016-11-10 10:05:27 +0800
categories: JavaScript
   
---
# JavaScript 函数
函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。

	<!DOCTYPE html>
	<html>
	<head>
	<script>
	function myFunction()
		{
			alert("Hello World!");
		}
	</script>
	</head>

	<body>
	<button onclick="myFunction()">Try it</button>
	</body>
	</html>

## JavaScript 函数语法
函数就是包裹在花括号中的代码块，前面使用了关键词 `function`：

	function functionName()
	{
		执行代码
	}

当调用该函数时，会执行函数内的代码。
可以在某事件发生时直接调用函数（比如当用户点击按钮时），并且可由 `JavaScript` 在任何位置进行调用。
## 调用带参数的函数
在调用函数时，可以向其传递值，这些值被称为参数。
这些参数可以在函数中使用。可以发送任意多的参数，由逗号 `,` 分隔：

	myFunction(argument1,argument2)

声明函数时，把参数作为变量来声明：

	function myFunction(var1,var2)
	{
		代码
	}

变量和参数必须以一致的顺序出现。第一个变量就是第一个被传递的参数的给定的值，以此类推。

	<button onclick="myFunction('Harry Potter','Wizard')">Try it</button>

	<script>
	function myFunction(name,job)
	{
	alert("Welcome " + name + ", the " + job);
	}
	</script>

上面的函数在按钮被点击时会提示 "Welcome Harry Potter, the Wizard"。
函数很灵活，您可以使用不同的参数来调用该函数，这样就会给出不同的消息：

	<button onclick="myFunction('Harry Potter','Wizard')">Try it</button>
	<button onclick="myFunction('Bob','Builder')">Try it</button>

根据点击的不同的按钮，上面的例子会提示 "Welcome Harry Potter, the Wizard" 或 "Welcome Bob, the Builder"。

## 带有返回值的函数

有时，我们会希望函数将值返回调用它的地方。
通过使用 return 语句就可以实现。
在使用 return 语句时，函数会停止执行，并返回指定的值。

	function myFunction()
	{
	   	 var x=5;
   		 return x;
	}

上面的函数会返回值 5。

**注意：** 整个 `JavaScript` 并不会停止执行，仅仅是函数。`JavaScript` 将继续执行代码，从调用函数的地方。
函数调用将被返回值取代：

	var myVar=myFunction();

`myVar` 变量的值是 `5`，也就是函数 `myFunction()` 所返回的值。


即使不把它保存为变量，也可以使用返回值：

	document.getElementById("demo").innerHTML=myFunction();

`demo` 元素的 `innerHTML` 将成为 5，也就是函数 `myFunction()` 所返回的值。

可以使返回值基于传递到函数中的参数：

	function myFunction(a,b)
	{
		return a*b;
	}
	document.getElementById("demo").innerHTML=myFunction(4,3);

`demo` 元素的 innerHTML 将是：`12`

当然这里的`return`和iOS中的`return`基本相同，也可以用于提前结束函数，跳出函数：

```
function myFunction(a,b)
{
	if (a>b)
	{
		return;
	}
	x=a+b
}
```

如果 `a` 大于 `b`，则上面的代码将退出函数，并不会计算 `a` 和 `b` 的总和。

## 局部 JavaScript 变量

在 `JavaScript` 函数内部声明的变量（使用 `var`）是局部变量，所以只能在函数内部访问它。（该变量的作用域是局部的）。
您可以在不同的函数中使用名称相同的局部变量，因为只有声明过该变量的函数才能识别出该变量。
只要函数运行完毕，本地变量就会被删除。

## 全局 JavaScript 变量

在函数外声明的变量是全局变量，网页上的所有脚本和函数都能访问它。

## JavaScript 变量的生存期

`JavaScript` 变量的生命期从它们被声明的时间开始。
局部变量会在函数运行以后被删除。
全局变量会在页面关闭后被删除。

## 向未声明的 JavaScript 变量分配值

如果把值赋给尚未声明的变量，该变量将被自动作为全局变量声明。

这条语句：

	carname="Volvo";

将声明一个全局变量 `carname`，即使它在函数内执行。

# JavaScript 作用域

`作用域`可访问变量的集合。在 `JavaScript` 中, 对象和函数同样也是变量。

**在 `JavaScript` 中, 作用域为可访问变量，对象，函数的集合。**

`JavaScript` 函数作用域: 作用域在函数内修改。

## JavaScript 局部作用域

变量在函数内声明，变量为局部作用域。
局部变量：只能在函数内部访问。

```
// 此处不能调用 carName 变量

function myFunction() {
    var carName = "Volvo";

    // 函数内可调用 carName 变量

}
```
因为局部变量只作用于函数内，所以不同的函数可以使用相同名称的变量。
局部变量在函数开始执行时创建，函数执行完后局部变量会自动销毁。

## JavaScript 全局变量

变量在函数外定义，即为全局变量。
全局变量有 **全局作用域**: 网页中所有脚本和函数均可使用。 

```
var carName = " Volvo";

// 此处可调用 carName 变量

function myFunction() {

    // 函数内可调用 carName 变量 

}
```

如果变量在函数内没有声明（没有使用 `var` 关键字），该变量为全局变量。
以下实例中 `carName` 在函数内，但是为全局变量。

```
// 此处可调用 carName 变量

function myFunction() {
    carName = "Volvo";

    // 此处可调用 carName 变量

}
```

## JavaScript 变量生命周期

`JavaScript` 变量生命周期在它声明时初始化。
局部变量在函数执行完毕后销毁。
全局变量在页面关闭后销毁。

### 函数参数

函数参数只在函数内起作用，是局部变量。

## HTML 中的全局变量

在 `HTML` 中, 全局变量是 `window` 对象: 所有数据变量都属于 `window` 对象。

```
//此处可使用 window.carName

function myFunction() {
    carName = "Volvo";
}
```














