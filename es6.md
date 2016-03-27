# ES6新特性

## 块级作用域

### 严格模式

严格模式在语法上与正常的JavaScript有一些不同

* 严格模式会将JavaScript陷阱直接变成明显的错误
* 严格模式修复了一些引擎难以修复的错误
* 同样的代码有些时候严格模式会比非严格模式下更快
* 严格模式禁用了一些可能会在未来版本中定义的语法

严格模式可以应用到整个script标签或某个别函数中，只需要把

`'use strict';`放在所有语句或者函数语句开始之前。

### let

`let`允许把变量的作用域限制在块级域中。

与`var`不同的是：var声明的变量要么是全局的，要么是函数级的，而无法是块级的。

**let在循环中**

可以使用let关键字绑定变量在循环的范围而不是使用一个全局变量

	'use strict';
	for(let i = 0; i<10; i++){
		console.log(i);	// 0,1,2,3,4...9
	}
	console.log(i);		//i is not defined
	
上面报错，因为变量i是let的，不存在于for语句的作用域中。let创建块级作用域变量的，使用var创建一个全局变量。

### const

`const`声明创建一个`常量`，可以全局或局部的函数声明。

一个常量不可以被重新赋值，不能被重复声明，也就是说在相同作用域内不能同名。

### 块级作用域

JavaScript使用`var`声明变量，用`function`来划分作用域。可是大括号`{}`却限定不了var的作用域。

用var声明的变量具有变量提升（declaration hoisting）的效果

## 类

### 类声明和类表达式

ES6中类实际上就是个`函数`，而且正如函数的定义方式有`函数声明`和`函数表达式`两种一样，类的定义方式也有两种，分别是：`类声明`和`类表达式`。

类声明就是定义类的一种方式，使用`class`关键字后跟一个类名，就可以定义一个类

	"use strict";
	class Polygon{
		constructor(height,width){
			this.height = height;
			this.width = width;
		}
	}

类声明和函数声明不同的一点是，函数声明存在`变量提升`现象，而类声明不存在。也就是说，你必须先声明一个类，然后才能使用它，否则代码会抛出`ReferenceError`异常。

`类表达式`是定义类的另一种方式，就像函数表达式一样，在类表达式中，类名是可有可无的。如果定义类类名，则该类名只有在类体内部才能放问到。

	"use strict;"
	//匿名类表达式
	var Polygon = class{
		constructor(height,width){
			this.height = height;
			this.width = width;
		}
	};
	
	//命名类表达式
	var Polygon = class Polygon{
		constructor(height,width){
			this.height = height;
			this.width = width;
		}
	};

### 构造函数

`class`根据`constructor`方法来创建和初始化对象

constructor是类的默认方法，通过new命令生成对象实例是，自动调用该方法。一个类只能有一个constructor方法，如果没有显示定义，一个空的constructor方法会默认添加

### 静态方法

`static`关键字定义类一个类的静态方法，通过类名直接访问。

### 使用extends关键字创建子类

`extends`关键字可以用来创建继承于某个类的子类

	'use strict';
	class Animal{
		....
	}
	
	class Dog extends Animal{
		....
	}
	
## 集合

### map基本用法

map对象是一个简单的键/值映射。任何值（包括对象和原始值）都可以用作一个键或一个值

	var m = new Map();
	
m.set(key,value);
m.get(key);

map接受数组作为参数，数组的每个成员就是一个键值对

	var map = new Map([["name","zhangsan"],["title","author"]]);
	
**map的键实际上是跟内存地址绑定的，只用内存地址不一样，就视为两个键**

### 实例的属性和操作方法

* size 返回map结构的成员总数，即键值对的数目
* set(key,value) 设置key所对应的键值，返回整个map结构。如果key已经有值则键值会被更新，否则就新生成该键
* get(key)	读取key对应的键值，如果找不到key，返回undefined
* has(key)	返回布尔值，key是否在map数据结构中
* delete(key)	删除某个key，返回true或者false
* clear()	清除所有成员，没有返回值

### map遍历方法

map原生提供类三个遍历器生成函数和一个遍历方法

`keys()`,`values()`,`entries()`,`forEach`

	var myMap = new Map();
	myMap.set(0,"zero");
	myMap.set(1,"one");
	for (var keyas of myMap.keys()) {
		console.log(keyas);
	}
	for (var value of myMap.values()) {
		console.log(value);
	}
	for (var item of myMap.entries()) {
		console.log(item[0] + " = "+ item[1]);
	}
	myMap.forEach(function(value,key){
		console.log(key + " = " + value);
	},myMap)
	


	

	
