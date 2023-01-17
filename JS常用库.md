# JS常用库

## jQuery
### 使用方式
在`<head>`元素中添加：

`<script src="https://cdn.acwing.com/static/jquery/js/jquery-3.3.1.min.js"></script>`

### 选择器
`$(selector)`，例如：
```
$('div');
$('.big-div');
$('div > p')
```
`selector`类似于CSS选择器。

### 事件
`$(selector).on(event, func)`绑定事件，例如：
```js
$('div').on('click', function (e) {
    console.log("click div");
})
```
`$(selector).off(event, func)`删除事件，例如：
```js
$('div').on('click', function (e) {
    console.log("click div");

    $('div').off('click');
});
```
当存在多个相同类型的事件触发函数时，可以通过`click.name`来区分，例如：
```js
$('div').on('click.first', function (e) {
    console.log("click div");

    $('div').off('click.first');
});
```
在事件触发的函数中的`return false`等价于同时执行：

- `e.stopPropagation()`：阻止事件向上传递

- `e.preventDefault()`：阻止事件的默认行为
### 元素的隐藏、展现
- `$A.hide()`：隐藏，可以添加参数，表示消失时间
- `$A.show()`：展现，可以添加参数，表示出现时间
- `$A.fadeOut()`：慢慢消失，可以添加参数，表示消失时间
- `$A.fadeIn()`：慢慢出现，可以添加参数，表示出现时间
### 元素的添加、删除
- `$('<div class="mydiv"><span>Hello World</span></div>')`：构造一个`jQuery`对象
- `$A.append($B)`：将$B添加到$A的末尾
- `$A.prepend($B)`：将$B添加到$A的开头
- `$A.remove()`：删除元素$A
- `$A.empty()`：清空元素$A的所有儿子
### 对类的操作
- `$A.addClass(class_name)`：添加某个类
- `$A.removeClass(class_name)`：删除某个类
- `$A.hasClass(class_name)`：判断某个类是否存在
### 对CSS的操作
- `$("div").css("background-color")`：获取某个CSS的属性
- `$("div").css("background-color","yellow")`：设置某个CSS的属性
- 同时设置多个CSS的属性：
```
$('div').css({
    width: "200px",
    height: "200px",
    "background-color": "orange",
});
```
### 对标签属性的操作
- `$('div').attr('id')`：获取属性
- `$('div').attr('id', 'ID')`：设置属性

### 对HTML内容、文本的操作
不需要背每个标签该用哪种，用到的时候Google或者百度即可。

- `$A.html()`：获取、修改HTML内容
- `$A.text()`：获取、修改文本信息
- `$A.val()`：获取、修改文本的值

### 查找
- `$(selector).parent(filter)`：查找父元素
- `$(selector).parents(filter)`：查找所有祖先元素
- `$(selector).children(filter)`：在所有子元素中查找
- `$(selector).find(filter)`：在所有后代元素中查找
### ajax
GET方法：
```js
$.ajax({
    url: url,
    type: "GET",
    data: {
    },
    dataType: "json",
    success: function (resp) {

    },
});
```
POST方法：
```js
$.ajax({
    url: url,
    type: "POST",
    data: {
    },
    dataType: "json",
    success: function (resp) {

    },
});
```

## setTimeout与setInterval

### setTimeout(func, delay)
`delay`毫秒后，执行函数`func()`。

### clearTimeout()
关闭定时器，例如：
```js
let timeout_id = setTimeout(() => {
    console.log("Hello World!")
}, 2000);  // 2秒后在控制台输出"Hello World"

clearTimeout(timeout_id);  // 清除定时器
```
### setInterval(func, delay)
每隔`delay`毫秒，执行一次函数`func()`。
第一次在第`delay`毫秒后执行。

### clearInterval()
关闭周期执行的函数，例如：
```js
let interval_id = setInterval(() => {
    console.log("Hello World!")
}, 2000);  // 每隔2秒，输出一次"Hello World"

clearInterval(interval_id);  // 清除周期执行的函数
```
## requestAnimationFrame
### requestAnimationFrame(func)
该函数会在下次浏览器刷新页面之前执行一次，通常会用递归写法使其每秒执行60次`func`函数。调用时会传入一个参数，表示函数执行的时间戳，单位为毫秒。

例如：
```js
let step = (timestamp) => {  // 每帧将div的宽度增加1像素
    let div = document.querySelector('div');
    div.style.width = div.clientWidth + 1 + 'px';
    requestAnimationFrame(step);
};

requestAnimationFrame(step);
```
与`setTimeout`和`setInterval`的区别：

- `requestAnimationFrame`渲染动画的效果更好，性能更加。
该函数可以保证每两次调用之间的时间间隔相同，但`setTimeout`与`setInterval`不能保证这点。`setTmeout`两次调用之间的间隔包含回调函数的执行时间；`setInterval`只能保证按固定时间间隔将回调函数压入栈中，但具体的执行时间间隔仍然受回调函数的执行时间影响。
- 当页面在后台时，因为页面不再渲染，因此`requestAnimationFrame`不再执行。但`setTimeout`与`setInterval`函数会继续执行。