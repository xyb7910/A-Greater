# JS中this关键字，变量定义的区别和JSON

## JS中的this关键字

JS中的this不是固定不变的，它会随着执行环境的改变而改变。
- 在方法中，this 表示该方法所属的对象。、

```js
var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```
this表示person对象。fullName 方法所属的对象就是 person。
- 如果单独使用，this 表示全局对象（不区分严格模式和普通模式）。
- 在函数中，this 表示全局对象。

在函数中，函数所属者默认绑定在this上，
```js
function myFunction() {
  return this;
}
```

- 在函数中，在严格模式下，this 是未定义的(undefined)。

严格模式下函数是没有绑定到 this 上，这时候 this 是 undefined。
```js
"use strict";
function myFunction() {
  return this;
}
```
- 在事件中，this 表示接收事件的元素。

在 HTML 事件句柄中，this 指向了接收事件的 HTML 元素。
```html
<button onclick="this.style.display='none'">
点我后我就消失了
</button>
```
- 类似 call() 和 apply() 方法可以将 this 引用到任何对象。

这两个方法异常强大，他们允许切换函数执行的上下文环境（context），即 this 绑定的对象。

当我们使用 person2 作为参数来调用 person1.fullName 方法时, this 将指向 person2, 即便它是 person1 的方法。
```js
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
person1.fullName.call(person2);  // 返回 "John Doe"
```

## JS中的var，let和const
`let` 声明的变量只在 `let` 命令所在的代码块内有效。

`const` 声明一个只读的常量，一旦声明，常量的值就不能改变。

使用 `var` 关键字声明的变量不具备块级作用域的特性，它在 `{}` 外依然能被访问到,但是使用 `let` 关键字来实现块级作用域。

`let` 声明的变量只在 `let` 命令所在的代码块 `{}` 内有效，在 `{}` 之外不能访问。
```js
{ 
    var x = 2; 
}
// 这里可以使用 x 变量

{ 
    let x = 2;
}
// 这里不能使用 x 变量
```

`const`用于声明一个或多个常量，声明时必须进行初始化，且初始化后值不可再修改。
```js
const PI = 3.141592653589793;
PI = 3.14;      // 报错
PI = PI + 10;   // 报错
```

## JS中的变量重置
- 使用 var 关键字声明的变量在任何地方都可以修改：
```js
var x = 2;
 
// x 为 2
 
var x = 3;
 
// 现在 x 为 3
```
- 在相同的作用域或块级作用域中，不能使用 let 关键字来重置 var 关键字声明的变量:
```js
var x = 2;       // 合法
let x = 3;       // 不合法

{
    var x = 4;   // 合法
    let x = 5   // 不合法
}
```
- 在相同的作用域或块级作用域中，不能使用 let 关键字来重置 let 关键字声明的变量:
```js
let x = 2;       // 合法
let x = 3;       // 不合法

{
    let x = 4;   // 合法
    let x = 5;   // 不合法
}
```
- 在相同的作用域或块级作用域中，不能使用 var 关键字来重置 let 关键字声明的变量:
```js
let x = 2;       // 合法
var x = 3;       // 不合法

{
    let x = 4;   // 合法
    var x = 5;   // 不合法
}
```
- let 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值的:
```js
let x = 2;       // 合法

{
    let x = 3;   // 合法
}

{
    let x = 4;   // 合法
}
```

## JS中的JSON

### JSON概念
- JSON 是用于存储和传输数据的格式。

- JSON 通常用于服务端向网页传递数据。

**JSON 使用 JavaScript 语法，但是 JSON 格式仅仅是一个文本。
文本可以被任何编程语言读取及作为数据格式传递。**

JSON的语法规则：
- 数据为 键/值 对。
- 数据由逗号分隔。
- 大括号保存对象
- 方括号保存数组

对于JSON数据，一个名称对应一个值,`键/值`对包括字段名称（在双引号中），后面一个冒号，然后是值：`"name":"Runoob"`。

JSON对象保存在大括号内，就像JS中的对象可以保存多个 `键/值` 对：`{"name":"Runoob", "url":"www.runoob.com"}`。

JSON数组保存在中括号内。

### JSON字符串转化为JS对象

通常我们从服务器中读取 JSON 数据，并在网页中显示数据。

首先，创建 JavaScript 字符串，字符串为 JSON 格式的数据：
```js
var text = '{ "sites" : [' +
'{ "name":"Runoob" , "url":"www.runoob.com" },' +
'{ "name":"Google" , "url":"www.google.com" },' +
'{ "name":"Taobao" , "url":"www.taobao.com" } ]}';
```

然后，使用 JavaScript 内置函数 `JSON.parse()` 将字符串转换为 JavaScript 对象:
```js
var obj = JSON.parse(text);
```
最后，在你的页面中使用新的 JavaScript 对象：
```js
var text = '{ "sites" : [' +
    '{ "name":"Runoob" , "url":"www.runoob.com" },' +
    '{ "name":"Google" , "url":"www.google.com" },' +
    '{ "name":"Taobao" , "url":"www.taobao.com" } ]}';
    
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;
```

### 常用函数

|             函数 | 描述                                           |
| ---------------: | :--------------------------------------------- |
|     JSON.parse() | 用于将一个 JSON 字符串转换为 JavaScript 对象。 |
| JSON.stringify() | 用于将 JavaScript 值转换为 JSON 字符串。       |