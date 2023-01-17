# JS中的类，箭头函数，DOM及其集合

## JS中的类

使用 `class` 关键字来创建一个类，类体在一对大括号 `{}` 中，我们可以在大括号 `{}` 中定义类成员的位置.

每个类中包含了一个特殊的方法 `constructor()`，它是类的构造函数，这种方法用于创建和初始化一个由 `class` 创建的对象。

### 语法格式
```js
class ClassName {
  constructor(){
    ...
  }
}
```

举例：
创建一个类，类名是"Person"，类中初始化了两个属性:"name"和"url"。
```js
class Person {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
}
```

### 类的实例化
我们可以使用`new`关键字来创建对象：
```js
class Person {
  constructor(name, url) {
    this.name = name;
    this.url = url;
  }
}

let bob =new Person("个人学习","www.xyb7910.com");
```
创建对象时会自动调用构造函数方法`constructor()`。
### 类的方法

我们可以在一个类中添加任意多数量的方法。
具体格式如下：
```js
class ClassName {
  constructor() { ... }
  method_1() { ... }
  method_2() { ... }
  method_3() { ... }
}
```
举例：我们在`Person`类中定义一个`age`方法。
```js
class Person {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}
 
let bob = new Runoob("个人学习", 2023);
document.getElementById("demo").innerHTML=
"鲍勃" + Person.age() + " 岁了。";
```
我们还可以向类的方法传递参数：
```js
class Person {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age(x) {
    return x - this.year;
  }
}
 
let date = new Date();
let year = date.getFullYear();
 
let bob = new Person("鲍勃", 2020);
document.getElementById("demo").innerHTML=
"鲍勃" + Person.age(year) + " 岁了。";
```

## 类的继承
JS类的继承使用`extends`关键字。

`super()`方法用于调用父类的构造函数。

当创建一个类时，我们不需要重新编写新的数据成员和成员函数，只需指定新建的类继承了一个已有的类的成员即可。这个已有的类称为**基类（父类）**，新建的类称为**派生类（子类）**。

格式如下：以下的基类是`Animal`，派生类是`Dog`。
```js
// 基类
class Animal {
    // eat() 函数
    // sleep() 函数
};
 
 
//派生类
class Dog extends Animal {
    // bark() 函数
};
```
举例：创建一个`Person`类继承了`Site`类。
```js
class Site {
  constructor(name) {
    this.sitename = name;
  }
  present() {
    return '我喜欢' + this.sitename;
  }
}
 
class Person extends Site {
  constructor(name, age) {
    super(name);
    this.age = age;
  }
  show() {
    return this.present() + ', 它创建了 ' + this.age + ' 年。';
  }
}
 
let bob = new Person("鲍勃", 5);
document.getElementById("demo").innerHTML = bob.show();
```

### getter和setter

我们可以使用 `getter` 和 `setter` 来获取和设置值，`getter` 和 `setter` 都需要在**严格模式**下执行。

`getter` 和 `setter` 可以使得我们对属性的操作变的很灵活。

类中添加 `getter` 和 `setter` 使用的是 `get` 和 `set` 关键字。

举例：为`sitename`属性创建 `getter` 和 `setter`。
```js
class Person {
  constructor(name) {
    this.sitename = name;
  }
  get s_name() {
    return this.sitename;
  }
  set s_name(x) {
    this.sitename = x;
  }
}
 
let Bob = new Person("鲍勃");
 
document.getElementById("demo").innerHTML = Bob.s_name;
```

注意：

函数声明和类声明之间的一个重要区别在于, 函数声明会提升，类声明不会。

你首先需要声明你的类，然后再访问它，否则类似以下的代码将抛出 `ReferenceError`。

## JS中的静态方法
静态方法是使用 `static` 关键字修饰的方法，又叫类方法，**属于类的，但不属于对象**，在实例化对象之前可以通过 `类名.方法名`调用静态方法。

静态方法不能在对象上调用，只能在类中调用。
```js
class Person {
  constructor(name) {
    this.name = name;
  }
  static hello() {
    return "Hello!!";
  }
}
 
let Bob = new Person("菜鸟教程");
 
// 可以在类中调用 'hello()' 方法
document.getElementById("demo").innerHTML = Person.hello();
 
// 不能通过实例化后的对象调用静态方法
// document.getElementById("demo").innerHTML = Bob.hello();
// 以上代码会报错
```
如果你想在对象 `Bob` 中使用静态方法，可以作为一个参数传递给它。
```js
class Person {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let Bob = new Person("菜鸟教程");
document.getElementById("demo").innerHTML = Bob.hello(noob);
```

## JS中的箭头函数

格式如下：
```js
(参数1, 参数2, …, 参数N) => { 函数声明 }

(参数1, 参数2, …, 参数N) => 表达式(单一)
// 相当于：(参数1, 参数2, …, 参数N) =>{ return 表达式; }
```
当只有一个参数时，圆括号是可选的：
```js
(单一参数) => {函数声明}
单一参数 => {函数声明}
```
没有参数的函数应该写成一对圆括号:
```js
() => {函数声明}
```
举例：
```js
// ES5
var x = function(x, y) {
     return x * y;
}
 
// ES6
const x = (x, y) => x * y;
```

当我们使用箭头函数的时候，箭头函数会默认帮我们绑定外层 `this` 的值，所以在箭头函数中 `this` 的值和外层的 `this` 是一样的。

箭头函数是不能提升的，所以需要在使用之前定义。

## JS中的DOM
当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。

HTML DOM 模型被构造为对象的树：

![](https://files.mdnice.com/user/34286/399db3d2-831d-4460-97e2-f8678d843813.png)

通过JS，我们可以创建动态的HTML
- JS能够改变页面中的所有 HTML 元素
- JS能够改变页面中的所有 HTML 属性
- JS能够改变页面中的所有 CSS 样式
- JS能够对页面中的所有事件做出反应

我们要想通过JS来操作HTML元素，可以通过以下三种方法来查找HTML元素
- 通过 id 找到 HTML 元素
```js
var x=document.getElementById("intro");
```
如果找到该元素，则该方法将以对象（在 x 中）的形式返回该元素。

如果未找到该元素，则 x 将包含 null。
- 通过标签名找到 HTML 元素
查找 `id="main"` 的元素，然后查找 `id="main"` 元素中的所有 `<p>` 元素：
```js
var x=document.getElementById("main");
var y=x.getElementsByTagName("p");
```
- 通过类名找到 HTML 元素
查找 `class="intro"` 的元素：
```js
var x=document.getElementsByClassName("intro");
```

### 改变HTML中的内容

最简单的方法，我们可以通过使用`innerHTML`。

具体格式如下
```js
document.getElementById(id).innerHTML=新的 HTML
```
举例：改变 `<p>`元素的内容
```html
<html>
<body>

<p id="p1">Hello World!</p>

<script>
document.getElementById("p1").innerHTML="新文本!";
</script>

</body>
</html>
```
改变 `<h1>` 元素的内容：
```html
<!DOCTYPE html>
<html>
<body>

<h1 id="header">Old Header</h1>

<script>
var element=document.getElementById("header");
element.innerHTML="新标题";
</script>

</body>
</html>
```

### 改变HTML属性

具体格式如下
```js
document.getElementById(id).attribute=新属性值
```
举例：改变了 `<img>` 元素的 `src` 属性
```html
<!DOCTYPE html>
<html>
<body>

<img id="image" src="smiley.gif">

<script>
document.getElementById("image").src="landscape.jpg";
</script>

</body>
</html>
```

### 改变HTML样式
具体格式如下
```js
document.getElementById(id).style.property=新样式
```
举例：改变 `<p>` 元素的样式
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
 
<p id="p1">Hello World!</p>
<p id="p2">Hello World!</p>
<script>
document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
</script>
<p>以上段落通过脚本修改。</p>
 
</body>
</html>
```

### addEventListener() 方法
具体格式如下
```js
element.addEventListener(event, function, useCapture);
```
- 第一个参数是事件的类型 (如 "click" 或 "mousedown").

- 第二个参数是事件触发后调用的函数。

- 第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的。

**注意：不要使用 "on" 前缀。 例如，使用 "click" ,而不是使用 "onclick"。**

在用户点击按钮时触发监听事件：
```js
document.getElementById("myBtn").addEventListener("click", displayDate);
```
- addEventListener() 方法用于向指定元素添加事件句柄。

当用户点击元素时弹出 "Hello World!" :
```js
element.addEventListener("click", function(){ alert("Hello World!"); });
```
- addEventListener() 方法添加的事件句柄不会覆盖已存在的事件句柄。


- 你可以向一个元素添加多个事件句柄。
```js
element.addEventListener("click", myFunction);
element.addEventListener("click", mySecondFunction);
```

- 你可以向同个元素添加多个同类型的事件句柄，如：两个 "click" 事件。

- 你可以向任何 DOM 对象添加事件监听，不仅仅是 HTML 元素。如： window 对象。

- addEventListener() 方法可以更简单的控制事件（冒泡与捕获）。

事件传递有两种方式：**冒泡与捕获**。

事件传递定义了元素事件触发的顺序。 如果你将 `<p>` 元素插入到 `<div>` 元素中，用户点击 `<p>` 元素, 哪个元素的 "click" 事件先被触发呢？

在 **冒泡** 中，内部元素的事件会先被触发，然后再触发外部元素，即： `<p>` 元素的点击事件先触发，然后会触发 `<div>` 元素的点击事件。

在 **捕获** 中，外部元素的事件会先被触发，然后才会触发内部元素的事件，即： `<div>` 元素的点击事件先触发 ，然后再触发 `<p>` 元素的点击事件。

默认值为 false, 即冒泡传递，当值为 true 时, 事件使用捕获传递。
- 当你使用 addEventListener() 方法时, JavaScript 从 HTML 标记中分离开来，可读性更强， 在没有控制HTML标记时也可以添加事件监听。

- 你可以使用 removeEventListener() 方法来移除事件的监听。

移除由 addEventListener() 方法添加的事件句柄:
```js
element.removeEventListener("mousemove", myFunction);
```
## Collection对象和NodeList对象
### HTMLCollection对象
`getElementsByTagName()` 方法返回 HTMLCollection 对象。

HTMLCollection 对象类似包含 HTML 元素的一个数组。

举例：获取文档所有的 <p> 元素：
```js
var x = document.getElementsByTagName("p");
```
集合中的元素可以通过**索引**(以 0 为起始位置)来访问。

访问第二个 `<p>` 元素可以是以下代码:
```js
y = x[1];
```
Collection对象具有length属性:

  length 属性定义了集合中元素的数量。
```js
var myCollection = document.getElementsByTagName("p");
document.getElementById("demo").innerHTML = myCollection.length;
```
### HTML中的节点链表

  `NodeList` 对象是一个从文档中获取的节点列表 (集合) 。

所有浏览器的 `childNodes` 属性返回的是 `NodeList` 对象。

大部分浏览器的 `querySelectorAll()` 返回 `NodeList` 对象。

举例：
  选取了文档中所有的 `<p>` 节点。
```js
var myNodeList = document.querySelectorAll("p");
```
`NodeList`中的元素可以通过**索引**(以 0 为起始位置)来访问。

访问第二个 `<p>` 元素可以是以下代码:
```js
y = myNodeList[1];
```
NodeList对象具有length属性：

length属性定义了节点列表中元素的数量。
```js
var myNodelist = document.querySelectorAll("p");
document.getElementById("demo").innerHTML = myNodelist.length;
```
### Collection与NodeList的区别
- HTMLCollection 是 HTML 元素的集合。

- NodeList 是一个文档节点的集合。

- NodeList 与 HTMLCollection 有很多类似的地方。

- NodeList 与 HTMLCollection 都与数组对象有点类似，可以使用索引 (0, 1, 2, 3, 4, ...) 来获取元素。

- NodeList 与 HTMLCollection 都有 length 属性。

- HTMLCollection 元素可以通过 name，id 或索引来获取。

- NodeList 只能通过索引来获取。

- 只有 NodeList 对象有包含属性节点和文本节点。