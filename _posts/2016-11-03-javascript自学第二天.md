---
layout: post
title: JavaScript自学第二天
date: 2016-11-03 13:02:36 +0800
categories: JavaScript
   
---
# JavaScript 语句
`JavaScript` 语句向浏览器发出的命令。语句的作用是告诉浏览器该做什么。
下面的 `JavaScript` 语句向 `id="demo"` 的 `HTML` 元素输出文本 `"你好 Dolly" `

	document.getElementById("demo").innerHTML = "你好 Dolly";

## 分号 ;
分号用于分隔 `JavaScript` 语句。
通常我们在每条可执行的语句结尾添加分号。
使用分号的另一用处是在一行中编写多条语句。

	a = 5; b = 6; c = a + b;

也可能看到不带有分号的案例。 在 `JavaScript` 中，用分号来结束语句是可选的。

## JavaScript 代码
`JavaScript` 代码是 `JavaScript` 语句的序列。
浏览器按照编写顺序依次执行每条语句。
下例向网页输出一个标题和两个段落：

	document.getElementById("demo").innerHTML="你好 Dolly";
	document.getElementById("myDIV").innerHTML="你最近怎么样?";

## JavaScript 代码块
`JavaScript` 可以分批地组合起来。
代码块以左花括号开始，以右花括号结束。
代码块的作用是一并地执行语句序列。
本例向网页输出一个标题和两个段落：

	function myFunction()
	{
		document.getElementById("demo").innerHTML="你好Dolly";
		document.getElementById("myDIV").innerHTML="你最近怎么样?";
	}	

## JavaScript 语句标识符
`JavaScript` 语句通常以一个 **语句标识符** 为开始，并执行该语句。
语句标识符是保留关键字不能作为变量名使用。
下表列出了 `JavaScript` 语句标识符 (关键字) ：

语句|描述
----|-----
break|用于跳出循环。
catch|语句块，在 try 语句块执行出错时执行 catch 语句块。
continue|跳过循环中的一个迭代。
do ... while|执行一个语句块，在条件语句为 true 时继续执行该语句块。
for|在条件语句为 true 时，可以将代码块执行指定的次数。
for ... in|用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作）。
function|定义一个函数
if ... else|用于基于不同的条件来执行不同的动作。
return|退出函数
switch|用于基于不同的条件来执行不同的动作。
throw|抛出（生成）错误 。
try|实现错误处理，与 catch 一同使用。
var|声明一个变量。
while|当条件语句为 true 时，执行语句块。

## JavaScript 对大小写敏感。
`JavaScript` 对大小写是敏感的。
当编写 `JavaScript` 语句时，请留意是否关闭大小写切换键。
函数 `getElementById` 与 `getElementbyID` 是不同的。
同样，变量 `myVariable` 与 `MyVariable` 也是不同的。

## 对代码行进行折行
可以在文本字符串中使用反斜杠对代码行进行换行。下面的例子会正确地显示：

	document.write("你好 \
	世界!");

不过，不能像这样折行：
	
	document.write \ 
	("你好世界!");

```*~Tips~*```
`JavaScript` 是脚本语言。浏览器会在读取代码时，逐行地执行脚本代码。而对于传统编程来说，会在执行前对所有代码进行编译。

# JavaScript 变量
与代数一样，`JavaScript` 变量可用于存放值（比如 x=5）和表达式（比如 z=x+y）。
变量可以使用短名称（比如 x 和 y），也可以使用描述性更好的名称（比如 age, sum, totalvolume）。

>1. 变量必须以字母开头
>2. 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做）
>3. 变量名称对大小写敏感（y 和 Y 是不同的变量）
>4. `JavaScript` 语句和 `JavaScript` 变量都对大小写敏感。

## 声明（创建） JavaScript 变量
在 `JavaScript` 中创建变量通常称为"声明"变量。
我们使用 var 关键词来声明变量：
	
	var carname;

变量声明之后，该变量是空的（它没有值）。
如需向变量赋值，请使用等号：

	carname="Volvo";

也可以在声明变量时对其赋值：

	var carname="Volvo";

在下面的例子中，我们创建了名为 `carname` 的变量，并向其赋值 "Volvo"，然后把它放入 id="demo" 的 HTML 段落中：

	<p id="demo"></p>
	var carname="Volvo";
	document.getElementById("demo").innerHTML=carname;

可以在一条语句中声明很多变量。该语句以 var 开头，并使用逗号分隔变量即可：

	var lastname="Doe", age=30, job="carpenter";

声明也可横跨多行：

	var lastname="Doe",
	age=30,
	job="carpenter";

## Value = undefined
在计算机程序中，经常会声明无值的变量。未使用值来声明的变量，其值实际上是 undefined。在执行过以下语句后，变量 `carname` 的值将是 undefined：

	var carname;

## 重新声明 JavaScript 变量
如果重新声明 JavaScript 变量，该变量的值不会丢失：
在以下两条语句执行后，变量 carname 的值依然是 "Volvo"：

	var carname="Volvo"; 
	var carname;

# JavaScript 数据类型

字符串`String`、数字`Number`、布尔`Boolean`、数组`Array`、对象`Object`、空`Null`、未定义`Undefined`。

## JavaScript 拥有动态类型
`JavaScript`是一种[动态语言](https://zh.wikipedia.org/wiki/%E5%8A%A8%E6%80%81%E8%AF%AD%E8%A8%80)，`JavaScript` 拥有动态类型。这意味着相同的变量可用作不同的类型：

	var x;               // x 为 undefined
	var x = 5;           // 现在 x 为数字
	var x = "John";      // 现在 x 为字符串

## JavaScript 字符串
字符串是存储字符（比如 "Bill Gates"）的变量。
字符串可以是引号中的任意文本。您可以使用单引号或双引号：

	var carname="Volvo XC60";
	var carname='Volvo XC60';
	
您可以在字符串中使用引号，只要不匹配包围字符串的引号即可：

	var answer="It's alright";
	var answer="He is called 'Johnny'";
	var answer='He is called "Johnny"';

## JavaScript 数字
JavaScript 只有一种数字类型。数字可以带小数点，也可以不带：

	var x1=34.00;      //使用小数点来写
	var x2=34;         //不使用小数点来写

极大或极小的数字可以通过科学（指数）计数法来书写：

	var y=123e5;      // 12300000
	var z=123e-5;     // 0.00123
	
## JavaScript 布尔
布尔（逻辑）只能有两个值：`true` 或 `false`。

	var x=true;
	var y=false;

## JavaScript 数组
下面的代码创建名为 `cars` 的数组：

	var cars=new Array();
	cars[0]="Saab";
	cars[1]="Volvo";
	cars[2]="BMW";

或者 `condensed array`:

	var cars=new Array("Saab","Volvo","BMW");

或者 `literal array`:

	var cars=["Saab","Volvo","BMW"];

数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。
## JavaScript 对象
对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

	var person={firstname:"John", lastname:"Doe", id:5566};

上面例子中的对象 `person` 有三个属性：`firstname`、`lastname` 以及 `id`。
空格和折行无关紧要。声明可横跨多行：

	var person={
		firstname : "John",
		lastname  : "Doe",
		id        :  5566
	};

对象属性有两种寻址方式：

	name=person.lastname;
	name=person["lastname"];

## Undefined 和 Null
说到`Null`，在iOS跟后端交互的时候，简直是个噩梦。

`Undefined` 这个值表示变量不含有值。
可以通过将变量的值设置为 `null` 来清空变量。

	cars=null;
	person=null;

## 声明变量类型
当声明新变量时，可以使用关键词 `new` 来声明其类型：

	var carname=new String;
	var x=      new Number;
	var y=      new Boolean;
	var cars=   new Array;
	var person= new Object;

`JavaScript` 变量均为对象。当您声明一个变量时，就创建了一个新的对象。
万物皆对象☺️

# JavaScript 对象
`JavaScript` 对象是拥有属性和方法的数据。
## 真实生活中的对象，属性和方法
真实生活中，一辆汽车是一个对象。
对象有它的属性，如重量和颜色等，方法有启动停止等:

对象|属性|对象
---|---|---
![car](https://harwordliu.com/assets/blogImages/2016-11-03-car.jpg)|car.name = Fiat  car.model = 500 car.weight = 850kg car.color = white|car.start() car.drive() car.brake() car.stop()

所有汽车都有这些属性，但是每款车的属性都不尽相同。
所有汽车都拥有这些方法，但是它们被执行的时间都不尽相同。

## JavaScript 对象
在 `JavaScript`中，几乎所有的事物都是对象。
以下代码为变量 `car` 设置值为 "Fiat" :

	var car = "Fiat";

对象也是一个变量，但对象可以包含多个值（多个变量）。

	var car = {name:"Fiat", model:500, color:"white", weight:850};

在以上实例中，4 个值`"Fiat", 500, "white", 850`赋予变量 `car`。
在以上实例中，4 个变量`type, model, color, weight`赋予变量 `car`。

`JavaScript` 对象是变量的容器。

## 对象定义
你可以使用字符来定义和创建 `JavaScript` 对象:

	var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
	
定义 JavaScript 对象可以跨越多行，空格跟换行不是必须的：

	var person = {
    	firstName:"John",
    	lastName:"Doe",
    	age:50,
    	eyeColor:"blue"
	};

## 对象属性
可以说 `JavaScript` 对象是变量的容器。
但是，我们通常认为 `JavaScript` 对象是键值对的容器。
键值对通常写法为 `name` : `value` (键与值以冒号分割)。
键值对在 `JavaScript` 对象通常称为 对象属性。

## 访问对象属性

可以通过两种方式访问对象属性:

	person.lastName;
	person["lastName"];

## 对象方法
对象的方法定义了一个函数，并作为对象的属性存储。
对象方法通过添加 () 调用 (作为一个函数)。
该实例访问了 person 对象的 fullName() 方法:

	name = person.fullName();

如果你要访问 person 对象的 fullName 属性，它将作为一个定义函数的字符串返回：

	name = person.fullName;

## 访问对象方法
可以使用以下语法创建对象方法：

	methodName : function() { code lines }

可以使用以下语法访问对象方法：

	objectName.methodName()

通常 `fullName()` 是作为 `person` 对象的一个方法， `fullName`是作为一个属性。
有多种方式可以创建，使用和修改 `JavaScript` 对象。
同样也有多种方式用来创建，使用和修改属性和方法。

##总结
本篇笔记依然都是基础篇，详细知识点博主在日后的文章中会展开深入学习。





















