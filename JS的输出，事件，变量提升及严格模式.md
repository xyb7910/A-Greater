# JS的输出，事件，变量提升及严格模式
## JS中的输出

JS中没有任何的打印和输出函数。

可以通过下边的方式来显示数据：

1. 使用 `window.alert()` 弹出警告框。
```html
<div>
  <script>window.alert(5 + 6)</script>
</div>
```

![](https://files.mdnice.com/user/34286/cb479360-b5c4-4311-87c2-17bce033cc60.png)

2. 使用 `document.write()` 方法将内容写到 HTML 文档中。
```html
<h1>我的第一个 Web 页面</h1>

<p>我的第一个段落。</p>

<script>
document.write(Date());
</script>
```

![](https://files.mdnice.com/user/34286/9e7af51b-b8f3-44a3-b84c-f9053fb64495.png)

3. 使用 `nnerHTML`写入到 HTML 元素。

如果想要操作元素，可以使用 `document.getElementById(id)`方法。

使用 `id`属性来标识 HTML 元素，并 `innerHTML` 来获取或插入元素内容。
```html
<h1>我的第一个 Web 页面</h1>

<p id="demo">我的第一个段落</p>

<script>
document.getElementById("demo").innerHTML = "段落已修改。";
</script>
```

![](https://files.mdnice.com/user/34286/07757b08-2f87-4e7d-9fa0-e85e3068c173.png)


4. 使用 console.log() 写入到浏览器的控制台。
```html
<script>
a = 5;
b = 6;
c = a + b;
console.log(c);
</script>
```

![](https://files.mdnice.com/user/34286/0475d87b-8f9f-4ae7-9d52-a4df9909e775.png)

## JS中的事件
HTML事件是发生在HTML元素上的事情。

如若HTML使用了JS,JS可以触发这些事件。

**常见的HTML事件**

|        事件 | 描述                                 |
| ----------: | :----------------------------------- |
|    onchange | HTML 元素改变                        |
|     onclick | 用户点击 HTML 元素                   |
| onmouseover | 鼠标指针移动到指定的元素上时发生     |
|  onmouseout | 用户从一个 HTML 元素上移开鼠标时发生 |
|   onkeydown | 用户按下键盘按键                     |
|      onload | 浏览器已完成页面的加载               |

当事件发生时，JS可以执行一些代码。

例如：
按钮元素中添加了 onclick 属性 (并加上代码):
```html
<button onclick="getElementById('demo').innerHTML=Date()">现在的时间是?</button>
```

![](https://files.mdnice.com/user/34286/591634cc-0de6-4390-bfe9-3f42204b2e9a.png)

## JS中的变量提升

**声明提升**：函数声明和变量声明总是会被解释器悄悄地被"提升"到方法体的最顶部。

JS中，函数及变量的声明都将被提升到函数的最顶部。

JS中，变量可以在**使用后声明**，也就是变量可以**先使用再声明**。

以下两种情况执行结果相同。

```js
x = 5; // 变量 x 设置为 5

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x

var x; // 声明 x
```
```js
var x; // 声明 x
x = 5; // 变量 x 设置为 5

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x
```

![](https://files.mdnice.com/user/34286/9bcad6b0-6bbe-4974-8cbc-78c7b79feb2a.png)

JS中只有声明的变量会被提升，已经初始化的变量不会提升。

下面两种情况结果不同：
```js
var x = 5; // 初始化 x
var y = 7; // 初始化 y

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y
```

![](https://files.mdnice.com/user/34286/92a2dec7-cf18-4409-b8d7-278f1ae4d038.png)
```js
var x = 5; // 初始化 x

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y

var y = 7; // 初始化 y
```

![](https://files.mdnice.com/user/34286/367aadc6-23bf-48ca-b7d0-681555489c4d.png)

**为了避免因为变量提升而出现更多的 BUG，通常我们在每个作用域开始前声明这些变量，这也是正常的 JS 解析步骤，易于我们理解。**

## JS中的严格模式
在脚本或函数的头部添加 `use strict`; 表达式来声明。

`use strict`的目的是指定代码在严格条件下执行。

严格模式下你**不能使用未声明的变量**。

举例：
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>JS学习</title>
</head>
<body>

<h1>使用 "use strict":</h1>
<h3>不允许使用未定义的变量。</h3>
<p>浏览器按下 F12 开启调试模式，查看报错信息。</p>
<script>
"use strict";
x = 3.14;       // 报错 (x 未定义)
</script>

</body>
</html>
```

![](https://files.mdnice.com/user/34286/bb4cd684-d3b6-4699-93d0-aa1ad0771188.png)

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>JS学习</title>
</head>
<body>

<p>在函数内使用 "use strict" 只在函数内报错。
</p>
<p>浏览器按下 F12 开启调试模式，查看报错信息。</p>
<script>
x = 3.14;       // 不报错 
myFunction();
function myFunction() {
   "use strict";
    y = 3.14;   // 报错 (y 未定义)
}
</script>

</body>
</html>
```

![](https://files.mdnice.com/user/34286/6d086a8c-0a57-4e4f-9e57-848fb9fc66fe.png)

**严格模式的限制**
- 不允许使用未声明的变量
- 不允许删除变量或者对象
- 不允许删除函数
- 不允许变量重名
- 等等