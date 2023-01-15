# CSS中的位置关系以及flex

## 位置关系
`position`属性用于指定一个元素在文档中的定位方式。

**定位类型**：

- 定位元素（positioned element）是其计算后位置属性为 relative, absolute, fixed 或 sticky 的一个元素（换句话说，除static以外的任何东西）。
- 相对定位元素（relatively positioned element）是计算后位置属性为 relative 的元素。
- 绝对定位元素（absolutely positioned element）是计算后位置属性为 absolute 或 fixed 的元素。
- 粘性定位元素（stickily positioned element）是计算后位置属性为 sticky 的元素。

**取值**：

- `static`：该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。此时 top, right, bottom, left 和 z-index 属性无效。
- `relative`：该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。top, right, bottom, left等调整元素相对于初始位置的偏移量。
- `absolute`：元素会被移出正常文档流，并不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。
- `fixed`：元素会被移出正常文档流，并不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。**元素的位置在屏幕滚动时不会改变**。
- `sticky`：元素根据正常文档流进行定位，然后相对它的最近滚动祖先（nearest scrolling ancestor）和 containing block (最近块级祖先 nearest block-level ancestor)，包括table-related元素，基于top, right, bottom, 和 left的值进行偏移。偏移值不会影响任何其他元素的位置。
```html
<h1>页面标题</h1>
<div class="container">
  <div class="box"></div>
  <p>段落内容段落内容 1</p>
  <p>段落内容段落内容 2</p>
  <p>段落内容段落内容 3</p>
  <p>段落内容段落内容 4</p>
</div>

<style>
  .container {
    background: lightblue;
  }

  .box {
    position: absolute;
    top: 0;
    left: 0;
    width: 100px;
    height: 100px;
    background: red;
  }
</style>
```


![](https://files.mdnice.com/user/34286/ce9a3639-ebc3-4b34-8603-11c47a166795.png)

```html
<nav>
  <a href="#">首页</a>
  <a href="#">导航1</a>
  <a href="#">导航2</a>
</nav>
<main>
  <section>1</section>
  <section>2</section>
  <section>3</section>
  <section>4</section>
  <section>5</section>
</main>
<a href="#" class="go-top">返回顶部</a>

<style>
  nav {
    position: fixed;
    line-height: 3;
    background: rgba(0, 0, 0, 0.3);
    width: 100%;
  }
  
  .go-top {
    position: fixed;
    right: 1em;
    bottom: 1em;
    color: #fff;
  }

  nav a {
    padding: 0 1em;
    color: rgba(255, 255, 255, 0.7);
  }

  nav a:hover {
    color: #fff;
  }

  body {
    margin: 0;
    font-size: 14px;
  }

  a {
    color: #fff;
    text-decoration: none;
  }

  section {
    height: 100vh;
    color: #fff;
    text-align: center;
    font-size: 5em;
    line-height: 100vh;
  }

  section:nth-child(1) {
    background: #F44336;
  }

  section:nth-child(2) {
    background: #3F51B5;
  }

  section:nth-child(3) {
    background: #FFC107;
  }

  section:nth-child(4) {
    background: #607D8B;
  }

  section:nth-child(5) {
    background: #4CAF50;
  }
</style>
```

![](https://files.mdnice.com/user/34286/208e3383-88a7-40bc-9322-370e9c3deb3c.png)


## 浮动float
`float`

指定一个元素应沿其容器的左侧或右侧放置，允许文本和内联元素环绕它。该元素从网页的正常流动(文档流)中移除，尽管仍然保持部分的流动性（与绝对定位相反）。

由于float意味着使用块布局，它在某些情况下修改display 值的计算值：

- display为inline或inline-block时，使用float后会统一变成block。

**取值**：

- left：表明元素必须浮动在其所在的块容器左侧的关键字。
- right：表明元素必须浮动在其所在的块容器右侧的关键字。

`clear`

有时，你可能想要强制元素移至任何浮动元素下方。比如说，你可能希望某个段落与浮动元素保持相邻的位置，但又希望这个段落从头开始强制独占一行。此时可以使用clear。

**取值**：

- left：清除左侧浮动。
- right：清除右侧浮动。
- both：清除左右两侧浮动
## Flex Box

- 一种新的排版上下文
- 它可以控制子级盒子的
  - 摆放流向(👆，👉，👈，👇)
  - 摆放顺序
  - 盒子的宽度和高度
  - 水平和垂直方向的对齐
  - 是否允许折行
```html
<div class="container">
  <div class="a">A</div>
  <div class="b">B</div>
  <div class="c">C</div>
</div>
<style>
  .container {
    display: flex;
    border: 2px solid #966;
  }

  .a, .b, .c {
    text-align: center;
    padding: 1em;
  }

  .a {
    background: #fcc;
  }

  .b {
    background: #cfc;
  }

  .c {
    background: #ccf;
  }
</style>
```

![](https://files.mdnice.com/user/34286/111e79fc-6b75-41df-a248-f1e0c4887c6d.png)

常见属性：

**flex-direction**：指定了内部元素是如何在 flex 容器中布局的，定义了主轴的方向(正方向或反方向)。

取值：

- row：flex容器的主轴被定义为与文本方向相同。 主轴起点和主轴终点与内容方向相同。
- row-reverse：表现和row相同，但是置换了主轴起点和主轴终点。
- column：flex容器的主轴和块轴相同。主轴起点与主轴终点和书写模式的前后点相同
- column-reverse：表现和column相同，但是置换了主轴起点和主轴终点

![](https://files.mdnice.com/user/34286/dccf1776-fb8b-4c89-9fe5-118a0ac436dd.png)

![](https://files.mdnice.com/user/34286/9005cfc7-fe2c-4a37-8cb2-7ae4b6398d64.png)

**flex-wrap**：指定 flex 元素单行显示还是多行显示。如果允许换行，这个属性允许你控制行的堆叠方向。

取值：

- nowrap：默认值。不换行。
- wrap：换行，第一行在上方。
- wrap-reverse：换行，第一行在下方。

**flex-flow**：是 flex-direction 和 flex-wrap 的简写。默认值为：row nowrap。

**justify-content**：定义了浏览器之间，如何分配顺着弹性容器主轴(或者网格行轴) 的元素之间及其周围的空间。

取值：

- flex-start：默认值。左对齐。
- flex-end：右对齐。
- space-between：左右两段对齐。
- space-around：在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素到行首的距离和每行最后一个元素到行尾的距离将会是相邻元素之间距离的一半。
- space-evenly：flex项都沿着主轴均匀分布在指定的对齐容器中。相邻flex项之间的间距，主轴起始位置到第一个flex项的间距，主轴结束位置到最后一个flex项的间距，都完全一样。

![](https://files.mdnice.com/user/34286/120b41f7-5656-4b2a-8fbe-e6a06678b170.png)

**align-items**：将所有直接子节点上的align-self值设置为一个组。 align-self属性设置项目在其包含块中在交叉轴方向上的对齐方式。

取值：

- flex-start：元素向主轴起点对齐。
- flex-end：元素向主轴终点对齐。
- center：元素在侧轴居中。
- stretch：弹性元素被在侧轴方向被拉伸到与容器相同的高度或宽度。

![](https://files.mdnice.com/user/34286/2f30cf55-5df9-434f-afe1-aef7f37d5a68.png)

**align-content**：设置了浏览器如何沿着弹性盒子布局的纵轴和网格布局的主轴在内容项之间和周围分配空间。

取值：

- flex-start：所有行从垂直轴起点开始填充。第一行的垂直轴起点边和容器的垂直轴起点边对齐。接下来的每一行紧跟前一行。
- flex-end：所有行从垂直轴末尾开始填充。最后一行的垂直轴终点和容器的垂直轴终点对齐。同时所有后续行与前一个对齐。
- center：所有行朝向容器的中心填充。每行互相紧挨，相对于容器居中对齐。容器的垂直轴起点边和第一行的距离相等于容器的垂直轴终点边和最后一行的距离。
- stretch：拉伸所有行来填满剩余空间。剩余空间平均地分配给每一行。

**order**：
定义flex项目的顺序，值越小越靠前。

![](https://files.mdnice.com/user/34286/96904ff0-d984-41a3-90a4-c64c735fb237.png)

Flexibility

- 可以设置子项的弹性：当容器有剩余空间时，会伸展；容器空间不足时，会收缩。
- flex-grow有剩余空间时的伸展能力
- flex-shrink容器空间不足使得收缩能力
- flex-basis没有伸展或者收缩时的基础长度

**flex-grow**：
设置 flex 项主尺寸 的 flex 增长系数。

负值无效，默认为 0。
```html
<div class="container">
  <div class="a">A</div>
  <div class="b">B</div>
  <div class="c">C</div>
</div>

<style>
  .container {
    display: flex;
  }

  .a, .b, .c {
    width: 100px;
  }

  .a {
    flex-grow: 2;
  }

  .b {
    flex-grow: 1;
  }
</style>
```

![](https://files.mdnice.com/user/34286/7cf724ef-8f10-4c2d-9fdc-291d3f573334.png)

**flex-shrink**：指定了 flex 元素的收缩规则。flex 元素仅在默认宽度之和大于容器的时候才会发生收缩，其收缩的大小是依据 flex-shrink 的值。

负值无效，默认为1。
```html
<div class="container">
  <div class="a">A</div>
  <div class="b">B</div>
  <div class="c">C</div>
</div>

<style>
  .container {
    display: flex;
  }

  .a, .b, .c {
    width: 400px;
  }

  .a {
    flex-shrink: 0;
  }
</style>
```

![](https://files.mdnice.com/user/34286/2eb26a77-8d04-4be6-beaa-7b8efb2f7d6a.png)

**flex-basis**：指定了 flex 元素在主轴方向上的初始大小。

取值：

- width 值可以是 `<length>`; 该值也可以是一个相对于其父弹性盒容器主轴尺寸的百分数 。负值是不被允许的。默认为 auto。

**flex**：
flex-grow、flex-shrink、flex-basis的缩写。
|           flex | flex                                       |
| -------------: | :----------------------------------------- |
|         flex:1 | flex-grow:1                                |
|     flex:100px | flex-basis:100px                           |
|       flex:2 1 | flex-grow:2,flex-shrink:1                  |
|   flex:1 100px | flex-grow:1,flex-basis:100px               |
| flex:2 0 100px | flex-grow:2,flex-shrink:0,flex-basis:100px |
|      flex:auto | flex:1 1 auto                              |
|      flex:none | flex:0 0 auto                              |

**常用取值**：
- auto：flex: 1 1 auto
- none：flex: 0 0 auto

## 声明

- 本文所记述内容为作者个人学习的记载，不得以任何形式转发或者引用。

- 本文原文档已上传至作者GitHub，可自行查阅。