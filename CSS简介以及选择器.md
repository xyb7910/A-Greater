# CSS简介以及选择器
## 什么是CSS？
- CSS 指层叠样式表 (Cascading Style Sheets)
- 样式定义如何显示 HTML 元素
- 样式通常存储在样式表中
- 把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题
- 外部样式表可以极大提高工作效率
- 外部样式表通常存储在 CSS 文件中
- 多个样式定义可层叠为一个

## CSS的工作原理

![](https://files.mdnice.com/user/34286/656eaff0-a353-412d-9292-859fc815de22.png)

## CSS的位置
```html
<!-- 外链 -->
<link rel="stylesheet" href="/assets/style.css">

<!-- 嵌入 -->
<style>
  li {margin:0; list-style:none; }
  p {margin:lem 0;}
</style>

<!-- 内联 -->
<p style="margin:len 0">Example Content</p>
```

## CSS选择器
目的：
- 找出页面中的元素，以便给他们设置样式
- 使用多种方式选择元素

分类：
1. 通配符选择器
- *：选择所有标签
```html
<h1>This is heading</h1>
<p>this is some paragraph.</p>

<style>
* {
  color: red;
  font-size: 20px;
}
</style>
```

![](https://files.mdnice.com/user/34286/e07ff396-54b7-49e0-9835-32978edb5069.png)

2. 标签选择器
```html
<h1>This is heading</h1>
<p>this is some paragraph.</p>

<style>
h1 {
  color: orange;
}
p {
  color: gray;
  font-size: 20px;
}
</style>
```

![](https://files.mdnice.com/user/34286/7912aeaa-b19f-4255-88fd-cf18ea5d09fd.png)

3. id选择器
```html
<h1 id="logo">
  <img src="https://assets.codepen.io/59477/h5-logo.svg" alt="HTML5 logo" width="48" />
  HTML5 文档
<h1>

<style>
  #logo {
    font-size: 60px;
    font-weight: 200;
  }
</style>
```

![](https://files.mdnice.com/user/34286/78bb6753-5754-4eb9-bd7b-cd94db22ca4a.png)

4. 类选择器
```html
<h2>Todo List</h2>
<ul>
  <li class="done">Learn HTML</li>
  <li class="done">Learn CSS</li>
  <li>Learn JavaScript</li>
</ul>
<style>
.done {
  color: gray;
  text-decoration: line-through;
}
</style>
```


![](https://files.mdnice.com/user/34286/7ae337f7-8614-47da-a9ec-af9af5c9b292.png)

5. 属性选择器
- [attribute]：选择具有某个属性的所有标签
- [attribute=value]：选择attribute值为value的所有标签
```html
<label>用户名：</label>
<input value="zhao" disabled />

<label>密码：</label>
<input value="123456" type="password" />

<style>
  [disabled] {
    background: #eee;
    color: #999;
  }
</style>
```

![](https://files.mdnice.com/user/34286/b5128fcf-bb40-41f5-822a-a8cc67892efa.png)
```html
<p>
  <label>密码：</label>
  <input type="password" value="123456" />
</p>

<style>
  input[type="password"] {
    border-color: red;
    color: red;
  }
</style>
```

![](https://files.mdnice.com/user/34286/9a532396-0f57-4f6e-bce2-b1bf9c578538.png)

```html
<p><a href="#top">回到顶部</a></p>
<p><a href="a.jpg">查看图片</a></p>

<style>
  a[href^="#"] {
    color: #f54767;
    background: 0 center/1em url(https://assets.codepen.io/59477/arrow-up.png) no-repeat;
    padding-left: 1.1em;
  }
 
  a[href$=".jpg"] {
    color: deepskyblue;
    background: 0 center/1em url(https://assets.codepen.io/59477/image3.png) no-repeat;
    padding-left: 1.2em;
  }
</style>
```

![](https://files.mdnice.com/user/34286/5c5d54fd-957a-4724-8b7b-409060148bdc.png)

## CSS中的伪类
- 不基于标签和属性定位元素
- 分类：状态伪类和结构性伪类

**链接伪类选择器**：

- :link：链接访问前的样式
- :visited：链接访问后的样式
- :hover：鼠标悬停时的样式
- :active：鼠标点击后长按时的样式
- :focus：聚焦后的样式

**目标伪类选择器**：

- :target：当url指向该元素时生效。
```html
<a href="http://example.com">
  example.com
</a>

<label>
  用户名：
  <input type="text">
</label>

<style>
a:link {
  color: black;
}

a:visited {
  color: gray;
}

a:hover {
  color: orange;
}

a:active {
  color: red;
}

:focus {
  outline: 2px solid orange;
}
</style>
```

![](https://files.mdnice.com/user/34286/ed9830b6-49b7-49be-87f0-c7b05f958871.png)
**位置伪类选择器**：

- :nth-child(n)：选择是其父标签第n个子元素的所有元素。
```html
<ol>
  <li>阿凡达</li>
  <li>泰坦尼克号</li>
  <li>星球大战：原力觉醒</li>
  <li>复仇者联盟 3</li>
  <li>侏罗纪世界</li>
</ol>

<style>
li {
  list-style-position: inside;
  border-bottom: 1px solid;
  padding: 0.5em
}

li:first-child {
  color: coral
}

li:last-child {
  border-bottom: none;
}
</style>
```

![](https://files.mdnice.com/user/34286/d7bb0b1d-c9a1-4ee6-ac43-a4d958091fb7.png)

```html
<label>
  用户名：
  <input class="error" value="aa">
</label>
<span class="error">
  最少3个字符
</span>

<style>
  .error {
    color: red;
  }
  
  input.error {
    border-color: red;
  }
</style>
```


![](https://files.mdnice.com/user/34286/468fb463-b576-4363-9c51-88c43199e7dc.png)

**伪元素选择器**：

将特定内容当做一个元素，选择这些元素的选择器被称为伪元素选择器。

- ::first-letter：选择第一个字母
- ::first-line：选择第一行
- ::selection：选择已被选中的内容
- ::after：可以在元素后插入内容
- ::before：可以在元素前插入内容

## CSS中的组合选择器
|       名称 | 语法 |             说明              | 示例        |
| ---------: | :--: | :---------------------------: | :---------- |
|   直接组合 |  AB  |        满足A同时满足B         | input:focus |
|   后代组合 | A B  |    选中B，如果它是A的子孙     | nav a       |
|   亲子组合 | A>B  |    选中B，如果它B的子元素     | section>p   |
|   兄弟组合 | A~B  | 选中B，如果它在A后并且与A同级 | h2~p        |
| 相邻选择器 | A+B  |   选中B，如果它紧跟在A后边    | h2+p        |
```html
<article>
  <h1>拉森火山国家公园</h1>
  <p>拉森火山国家公园是位于...</p>
  <section>
    <h2>气候</h2>
    <p>因为拉森火山国家公园...</p>
    <p>高于这个高度，气候非常寒冷...</p>
  </section>
</article>

<style>
  article p {
    color: black;
  }

  article > p {
    color: blue;
  }

  h2 + p {
    color: red; 
  }
</style>
```

![](https://files.mdnice.com/user/34286/32c12c84-6139-4fed-ab70-e8663e445d60.png)
## 样式渲染的优先级
- 权重大小，越具体的选择器权重越大：!important > 行内样式 > ID选择器 > 类与伪类选择器 > 标签选择器 > 通用选择器
- 权重相同时，后面的样式会覆盖前面的样式
- 继承自父元素的权重最低

## 声明

- 本文所记述内容为作者个人学习的记载，不得以任何形式转发或者引用。

- 本文原文档已上传至作者GitHub，可自行查阅。