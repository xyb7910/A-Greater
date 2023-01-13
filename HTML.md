# HTML
## HTML是什么？
HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: HyperText Markup Language
- HTML 不是一种编程语言，而是一种标记语言
- 标记语言是一套标记标签 (markup tag)
- HTML 使用标记标签来描述网页
- HTML 文档包含了HTML 标签及文本内容
- HTML文档也叫做 web 页面

您可以使用 HTML 来建立自己的 WEB 站点，HTML 运行在浏览器上，由浏览器来解析。
## 文档结构
HTML所有的标签为树形结构，例如：
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML学习</title>
</head>
<body>
    <h1>第一讲</h1>
</body>
</html>
```
`<html>标签`:
HTML `<html>` 元素 表示一个 HTML 文档的根（顶级元素），所以它也被称为根元素。所有其他元素必须是此元素的后代。

`<head>标签`:HTML head 元素 规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。

`<body>标签`：HTML body 元素表示文档的内容。document.body 属性提供了可以轻松访问文档的 body 元素的脚本。

`<title>`标签:HTML `<title>` 元素 定义文档的标题，显示在浏览器的标题栏或标签页上。它只应该包含文本，若是包含有标签，则它包含的任何标签都将被忽略。

`<meta>`:HTML `<meta>` 元素表示那些不能由其它 HTML 元相关（meta-related）元素（`<base>`、`<link>`, `<script>`、`<style>` 或 `<title>`）之一表示的任何元数据信息。

常见属性：

- charset：这个属性声明了文档的字符编码。如果使用了这个属性，其值必须是与 ASCII 大小写无关（ASCII case-insensitive）的”utf-8”。
- name：name 和 content 属性可以一起使用，以名 - 值对的方式给文档提供元数据，其中 name 作为元数据的名称，content 作为元数据的值。

## HTML标签
HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由尖括号包围的关键词，比如 `<html>`
- HTML 标签通常是成对出现的，比如 `<b>` 和 `</b>`
- 标签对中的第一个标签是开始标签，第二个标签是结束标签
- 开始和结束标签也被称为开放标签和闭合标签

## HTML语法
- 标签以及属性不区分大小写，推荐小写
- 空标签可以不闭合，比如：`input`，`meta`
- 属性值推荐使用**双引号**包裹
- 某些属性可以省略，比如：`required`，`readonly`
## 常用标签
这里只给出了常用的标签，如果想查阅更多的信息，请前往[MDN官网](https://developer.mozilla.org/zh-CN/)。
### 1.标题h1~h6
```html
<h1>字体排印学</h1>
<h2>历史</h2>
<p>活字的雏形或可追溯至公元前两千年前后美
索不达米亚文明的乌鲁克和拉尔萨，砖块上面不
均匀的印花被视作有可能是活字思想雏形。</p>
<h3>印刷体源流</h3>
<p>中国在唐代就已经出现雕版印刷术，公元868
年的《金刚经》是现存最古老的印刷品之一，使用
的技术即是木雕版印刷。</p>
<h2>应用</h2>
<p>...</p>
```

![](https://files.mdnice.com/user/34286/f282c3e8-bd6b-45da-b221-ca6861d0418b.png)

### 2.列表标签
```html
<h2>世界电影票房排行榜</h2>
<!-- ol为有序列表，会渲染一个有数字标识的链表-->
<ol>
  <li>阿凡达</li>
  <li>泰坦尼克号</li>
  <li>复仇者联盟</li>
</ol>

<h2>购物清单</h2>
<!-- ul为无序列表，渲染一个使用小黑点的列表-->
<ul>
  <li>🍇</li>
  <li>🍉</li>
  <li>🍎</li>
</ul>

<h2>霸王别姬</h2>
<!--HTML <dl> 元素 （或 HTML 描述列表元素）是一个包含术语定义以及描述的列表，通常用于展示词汇表或者元数据 (键 - 值对列表)。 -->
<dl>
  <dt>导演：</dt>
  <dd>陈凯歌</dd>
  <dt>主演：</dt>
  <dd>张国荣</dd>
  <dd>张丰毅</dd>
  <dd>巩俐</dd>
  <dt>上映日期：</dt>
  <dd>1993-01-01</dd>
</dl>
```

![](https://files.mdnice.com/user/34286/8fa3c995-b0df-44d0-93fa-ae3a42a5c3e4.png)

### 3.链接标签
```html
<!--网站链接，当前页-->
<a href="https://www.bytedance.com/">
  字节跳动官网
</a>
<!--网站链接，新建页-->
<a href="https://www.bytedance.com/" target="_blank">
  字节跳动官网
</a>
```
![](https://files.mdnice.com/user/34286/972da18b-7b60-416f-b6a3-4b1bfb053022.png)
```html
<!--图像链接-->
<img
  src="https://lf3-static.bytednsdoc.com/obj/eden-cn/ubqnuhbnuho/movable_type.jpg"
  alt="Metal movable type"
  width="400"
/>
<!--音频链接-->
<audio music.ogg
  src="/assets/"
  controls
></audio>
<!--视频链接-->
<video
  src="/assets/video.mp4"
  controls
></video>
```
![](https://files.mdnice.com/user/34286/84fd70bc-aa48-48f9-8a42-8de57b0be4e5.png)

### 4.输入框
```html
<input placeholder="请输入用户名">

<input type="range">

<input type="number" min="1" max="10">

<input type="date" min="2018-02-10">

<textarea>Hey</textarea>
```

![](https://files.mdnice.com/user/34286/3314ee26-71fe-4485-9345-14b75184f6c9.png)
```html
<p>
  <label><input type="checkbox" />🍎</label>
  <label><input type="checkbox" checked />🍏</label>
</p>

<p>
  <label><input type="radio" name="sport" />⚽</label>
  <label><input type="radio" name="sport" />🏀</label>
</p>

<p>
  <select>
    <option>🥑</option>
    <option>🥩</option>
    <option>🥓</option>
  </select>
</p>

<input list="countries" />
<datalist id="countries">
  <option>Greece</option>
  <option>United Kingdom</option>
  <option>United States</option>
</datalist>
```

![](https://files.mdnice.com/user/34286/ea5312a0-1538-43e4-89b7-8c4aa1c42991.png)

### 5.引用标签
```html
<blockquote cite="http://t.cn/RfjKO0F">
  <p>天才并不是自生自长在深林荒野里的怪物， 是由可以使天才生长的民众产生、长育出来的，所以没有 这种民众，就没有天才。</p>
</blockquote>

<p>我最喜欢的一本书是<cite>小王子</cite>。</p>

<p>在<cite>第一章</cite>，我们讲过<q>字符串是不可变量</q>。</p>

<p><code>const</code>声明创建一个只读的常量。</p>

<pre><code>
const add = (a, b) => a + b;
const multiply = (a, b) => a * b;
</code></pre>

<p>在投资之前，<strong>一定要做风险评估</strong>。</p>

<p>Cats <em>are</em> cute animals.</p>
```

![](https://files.mdnice.com/user/34286/c58b25ed-9011-4313-b83b-e6c7414e249f.png)

## 页面布局划分

![](https://files.mdnice.com/user/34286/9e3e236f-efc8-49a4-8281-f4f589b44d2f.png)
`<header>`:HTML `<header>` 元素用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。

`<nav>`:HTML `<nav>`元素表示页面的一部分，其目的是在当前文档或其他文档中提供导航链接。导航部分的常见示例是菜单，目录和索引。

`<section>`:HTML `<section>`元素表示一个包含在 HTML 文档中的独立部分，它没有更具体的语义元素来表示，一般来说会有包含一个标题。

`<figure>`:HTML `<figure>` 元素代表一段独立的内容，经常与说明（caption）`<figcaption>` 配合使用，并且作为一个独立的引用单元。当它属于主内容流（main flow）时，它的位置独立于主体。这个标签经常是在主文中引用的图片，插图，表格，代码段等等，当这部分转移到附录中或者其他页面时不会影响到主体。

`<figcaption>`:HTML `<figcaption>` 元素 是与其相关联的图片的说明/标题，用于描述其父节点 `<figure>` 元素里的其他数据。这意味着 `<figcaption>` 在`<figure>` 块里是第一个或最后一个。同时 HTML Figcaption 元素是可选的；如果没有该元素，这个父节点的图片只是会没有说明/标题。

`<article>`:HTML `<article>`元素表示文档、页面、应用或网站中的独立结构，其意在成为可独立分配的或可复用的结构，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。

`<aside>`:HTML `<aside>` 元素表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分并且可以被单独的拆分出来而不会使整体受影响。其通常表现为侧边栏或者标注框（call-out boxes）。

`<footer>`:HTML `<footer>`元素表示最近一个章节内容或者根节点（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。

## 特殊符号
| HTML源代码 | 显示结果 | 描述                   |
| ---------: | :------: | :--------------------- |
|     `&lt;` |    <     | 小于号或显示标记       |
|     `&gt;` |    >     | 大于号或显示标记       |
|    `&amp;` |    &     | 可用于显示其它特殊字符 |
|   `&quot;` |    “     | 引号                   |
|    `&reg;` |    ®     | 已注册                 |
|   `&copy;` |    ©     | 版权                   |
|  `&trade;` |    ™     | 商标                   |
|   `&nbsp;` |          | 不断行的空白           |

## 声明

本文所记述内容为作者个人学习的记载，不得以任何形式转发或者引用。

本文原文档已上传至作者GitHub，可自行查阅。