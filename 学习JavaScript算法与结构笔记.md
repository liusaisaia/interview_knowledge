# 第一章JavaScript简介



## JavaScript基础

### 变量

变量保存的数据可以在需要的时候设置、更新或提取。赋给变量的上午值都有对应的类型。

JavaScript的类型有数、字符串、布尔值、函数和对象，还有undefined和null，以及数组、日期和正则表达式。

### 变量的作用域

作用域是指： 在编写算法函数中，我们能访问变量（在使用函数作用域时，也可以是一个函数）的地方。有局部变量和全局变量两种。

在JavaScript中应该少使用全局变量，代码的质量可以用全局变量和函数的数量来考量。

**原始数据类型**： null、undefined、字符串、数、布尔值和symbol。

**派生数据类型/对象**：JavaScript对象，包括函数、数组和正则表达式。



### JavaScript面向对象编程

**创建一个普通对象的两种方式**：

* ```javascript
  var obj = new Object();
  ```

* ```javascript
  var obj = {};
  ```

也可以创建一个完整的对象:

```javascript
obj = {
	name: {
		first: 'Gandalf',
		last: 'the Grey'
	},
	address: 'Middle Earth'
}
```

可以看到，声明JavaScript对象时，键值对中的键就是对象的属性，值就是对应属性的值。

在面向对象编程（oop）里，对象时类的实例。一个类定义了对象的特征。

类可以包含函数（通常称为方法）；



# 第二章ECMAScript和TypeScript概述

> 从2005年起，每年都会有一个新的版本发布，我们称之为ECMAScript。
>
> ECMA是一个将信息标准化的组织，JavaScript是该标准的一个实现。

### 使用Babel.js

Babel是一个JavaScript转译器，它将使用了ECMAScript语言特性的JavaScript代码转换成只只使用广泛支持的ES5特性的等价代码。

**使用Babel的两种方式**：

* 根据设置文档进行安装
* 直接在浏览器中试用

## ECMAScript 2015+的功能

### 用let是代替var声明变量

在ES5为止，我们可以在代码中任意为止声明变量，甚至重写已经声明的变量，例如：

```javascript
var network = 'Vue';
var network = 'React';
console.log(network); // React
```

上述代码中有相同名字的变量，这样可能会导致输出错误。

EA2015引入let关键字，可以把上述代码改成：

```javascript
let network = 'Vue';
let network = 'React'; // 报错不能重复声明变量
console.log(network); // Vue
```

同时，还引入的const关键字，它的行为和let是一样的，区别就在于，用const声明的变量都是只读的，都是常亮。

比如以下以下代码：

```
const PI = 1111;
PI = 2222; // 报错

```

### 声明展开和剩余参数

在ES5中我们可以用apply()函数吧数组转化为参数，ES2015有了展开运算符

```javascript
let params = [1, 2, 3];
console.log(sum(...params));
// 等同于
console.log(sum.apply(undefiend, params));
```

在函数中展开运算符也可以替代arguments，当做剩余的参数。

### 增强的对象属性

ES2015引入了数组解构的概念，可以一次初始化多个例子；

```
let [x, y] = ['a', 'b'];
// 等同于
let x = 'a';
let y = 'b';
```

数组解构可以用来进行值得交换

```javascript
[1,2] = [2,1]
```

还有一个属性的简写

```
let [x, y] = ['a', 'b'];
let obj = {x, y};
console.log(obj); // {x: 'a' , y: 'b'}

//等同于
let x = 'a';
let y = 'b';
let obj2 = {X:X, Y:Y};

```

简写方法名

```
const hello = {
	name: 'as',
	printHello() {
		console.log('Hello')
	}
}
// 等同于
var hello = {
	name: 'as',
	printHello: function printHello () {
		console.log('hello')
	}
}
```

