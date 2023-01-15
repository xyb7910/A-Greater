# CSS中继承，属性值以及样式布局

## CSS中的继承

### 理解继承
某些属性会自动继承其父元素的计算值，除非显式指定一个值。
```html
<p>This is a <em>test</em> of <strong>inherit</strong></p>

<style>
  body {
    font-size: 20px;
  }
  p {
    color: blue;
  }
  em {
    color: red;
  }
</style>
```

![](https://files.mdnice.com/user/34286/b71d1ec4-37d4-465a-a63a-037ca112d33d.png)

### 控制继承
CSS为控制继承提供了五个特殊的通用属性。
- inherit：设置该属性会使子元素属性和父元素相同。实际上，就是“开启继承”。

- initial：将应用于选定元素的属性值设置为该属性的初始值。

- revert (en-US)：将应用于选定元素的属性值重置为浏览器的默认样式，而不是应用于该属性的默认值。在许多情况下，此值的作用类似于 unset。

- revert-layer (en-US)：将应用于选定元素的属性值重置为在上一个层叠层中建立的值。

- unset：将属性重置为自然值，也就是如果属性是自然继承那么就是 inherit，否则和 initial 一样

```html
<ul>
    <li>Default <a href="#">link</a> color</li>
    <li class="my-class-1">Inherit the <a href="#">link</a> color</li>
    <li class="my-class-2">Reset the <a href="#">link</a> color</li>
    <li class="my-class-3">Unset the <a href="#">link</a> color</li>
</ul>
```
```css
body {
    color: green;
}
          
.my-class-1 a {
    color: inherit;
}
          
.my-class-2 a {
    color: initial;
}
          
.my-class-3 a {
    color: unset;
}
```

![](https://files.mdnice.com/user/34286/db92ed20-e286-4ce3-80f4-f7ec234e2c24.png)

### 初始值
CSS属性的初始值是其默认值，初始值的使用取决于属性是否被继承：
- 对于继承属性，初始值只能被用于没有指定值得根元素上
- 对于非继承属性，初始值可以被用于任何没有指定得元素上

扩充：
- 继承属性：当元素的一个继承属性（inherited property）没有指定值时，则取父元素的同属性的计算值 computed value (en-US)。只有文档根元素取该属性的概述中给定的初始值（initial value）（这里的意思应该是在该属性本身的定义中的默认值）。
- 非继承属性：当元素的一个非继承属性(没有指定值时，则取属性的初始值 initial value（该值在该属性的概述里被指定）。

显示继承
```css
* {
  box-sizing: inherit
}
html {
  box-sizing: border-box;
}
.some-widget {
  box-sizing:content-box;
}
```
## CSS的求值
### 计算值
计算值是指这个属性在由父类转向子类的继承中的值。它通过指定值计算出来：

- 处理特殊的值 inherit，initial， unset和 revert (en-US)。
- 进行计算，以达到属性摘要中“计算值”行中描述的值。

计算值所需要的计算通常包括将**相对值**转换成**绝对值** (如 em 单位或百分比)。例如，如一个元素的属性值为 font-size:16px 和 padding-top:2em, 则 padding-top 的计算值为 32px (字体大小的 2 倍).

然而，对于有些属性 (这些元素的百分比与需要布局确定后才能知道的值有关，如 width, margin-right, text-indent, 和 top)，它们的“百分比值”会转换成“百分比的计算值”。另外，line-height 属性值如是没有单位的数字，则该值就是其计算值。这些计算值中的相对值会在 **应用值** 确定后转换成绝对值。
### 指定值
指定值 (specified value) 会通过下面 3 种途径取得：

1. 在当前文档的样式表中给这个属性赋的值，会被优先使用。例如：把 color 属性的值设为green ，那么对应元素内的文字就会变成绿色。
2. 如果在当前文档的样式表中没有给这个属性赋值，那么它会尝试从父元素那继承一个值。例如：在一个 `<div>` 内部放置一个段落 (`<p>`)，这个 `<div>` 的 font 属性值为 "Arial"，而 `<p>` 的 font 属性没有被赋值，那么它的字体就会继承为 Arial
3. 如果上面的两种途径都不可行，则把 CSS 规范中针对这个元素的这个属性的初始值作为指定值。
### 应用值
应用值完成所有计算后最终使用的值，可以由`window.getComputedStyle (en-US)` 获取。

计算出 CSS 属性的最终值有三个步骤。
1. 指定值 specified value 取自样式层叠 (选取样式表里权重最高的规则), 继承 (如果属性可以继承则取父元素的值)，或者默认值。
2. 按规范算出 计算值 computed value (en-US) (例如， span 指定 position: absolute 后display 变为 block)。
3. 计算布局 (尺寸比如 auto 或 百分数 换算为像素值 )，结果即 应用值 used value。

这些步骤是在内部完成的，脚本只能使用 `window.getComputedStyle (en-US)` 获得最终的应用值。

举例：

没有明确的宽度。指定的宽度：auto (默认). 计算的宽度：auto. 应用的宽度：998px (举例而言)。

明确的宽度：50%. 指定的宽度：50%. 计算的宽度：50%. 应用的宽度：447px 明确的宽度：inherit. 指定的宽度：50%. 计算的宽度：50%. 应用的宽度：221px .

### 实际值
实际值（actual value）是应用值（used value）被应用后的近似值。例如，一个用户代理可能只能渲染一个整数像素值的边框（实际值），并且该值可能被强制近似于边框的计算宽度值。


![](https://files.mdnice.com/user/34286/9542d5e6-23b0-4280-a30c-0f1ebd2ebbad.png)

## CSS中元素展现格式
**display**
- block：
  - 独占一行
  - width、height、margin、padding均可控制
  - width默认100%。
- inline：
  - 可以共占一行
  - width与height无效，水平方向的margin与padding有效，竖直方向的margin与padding无效
  - width默认为本身内容宽度
- inline-block
  - 可以共占一行
  - width、height、margin、padding均可控制
  - width默认为本身内容宽度
  

**white-space**

用来设置如何处理元素中的 空白 (en-US)。

**text-overflow**

确定如何向用户发出未显示的溢出内容信号。它可以被剪切，显示一个省略号或显示一个自定义字符串。

常见属性：`clip`，`ellipsis`等

**overflow**

定义当一个元素的内容太大而无法适应 块级格式化上下文 时候该做什么。它是 overflow-x 和overflow-y的 简写属性 。

常见属性：`visible`，`hidden`，`scroll`，`auto`等。

![](https://files.mdnice.com/user/34286/25650e78-2215-4018-b691-d613c0f5d7ab.png)


![](https://files.mdnice.com/user/34286/4b31a22b-ccb3-453e-be43-70508d81eb0e.png)

![](https://files.mdnice.com/user/34286/b538eeb8-07f6-4083-bd34-baad77571c4f.png)

## CSS中的布局
### 内边距与外边距
**margin**

给定元素设置所有四个（上下左右）方向的外边距属性。

取值可以是长度，百分数，auto；其中百分数相对于容器的宽度。

- 可以接受1~4个值（上、右、下、左的顺序）
- 可以分别指明四个方向：margin-top、margin-right、margin-bottom、margin-left
- 可取值
  - length：固定值
  - percentage：相对于包含块的宽度，以百分比值为外边距。
  - auto：让浏览器自己选择一个合适的外边距。有时，在一些特殊情况下，该值可以使元素居中。
- 外边距重叠
  - 块的上外边距(margin-top)和下外边距(margin-bottom)有时合并(折叠)为单个边距，其大小为单个边距的最大值(或如果它们相等，则仅为其中一个)，这种行为称为边距折叠。
  - 父元素与后代元素：父元素没有上边框和padding时，后代元素的margin-top会溢出，溢出后父元素的margin-top会与后代元素取最大值。

技巧：使用margin：auto实现水平居中
```html
<div></div>

<style>
  div {
    width: 200px;
    height: 200px;
    background: coral;
    margin-left: auto;
    margin-right: auto;
  }
</style>
```

![](https://files.mdnice.com/user/34286/18ed2c12-79cb-4156-9a5b-01bc10e482ee.png)

**padding**

控制元素所有四条边的内边距区域。

取值可以是长度，百分数，auto；其中auto由浏览器根据它的属性来去确定，百分数是相对于容器的content box宽度。
- 可以接受1~4个值（上、右、下、左的顺序）
- 可以分别指明四个方向：padding-top、padding-right、padding-bottom、padding-left
- 可取值
  - length：固定值
  - percentage：相对于包含块的宽度，以百分比值为内边距。


![](https://files.mdnice.com/user/34286/c938d869-073c-4d88-bfcd-4ad1e28921e0.png)

### 边框

**border-style**：用来设定元素所有边框的样式。

**border-width**：可以设置盒子模型的边框宽度。

**border-color**：用于设置元素四个边框颜色的快捷属性： border-top-color, border-right-color, border-bottom-color, border-left-color

**border-radius**：设置元素的外边框圆角。当使用一个半径时确定一个圆形，当使用两个半径时确定一个椭圆。这个(椭)圆与边框的交集形成圆角效果。

**border-collapse**：用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。
```html
<div class="a"></div>
<div class="b"></div>

<style>
  .a {
    background: lightblue;
    height: 100px;
    margin-bottom: 100px;
  }

  .b {
    background: coral;
    height: 100px;
    margin-top: 100px;
  }
</style>
```


![](https://files.mdnice.com/user/34286/7744c995-4174-4d93-b92f-a802f44675dc.png)

### 盒子模型
CSS 中的 box-sizing 属性定义了 user agent 应该如何计算一个元素的总宽度和总高度。

content-box：是默认值，设置border和padding均会增加元素的宽高。
border-box：设置border和padding不会改变元素的宽高，而是挤占内容区域。

```html
<p class="a">
  This is the behavior of width and height as specified by CSS2.1. The
  specified width and height (and respective min/max properties) apply to
  the width and height respectively of the content box of the element.
</p>
<p class="b">
  Length and percentages values for width and height (and respective min/max
  properties) on this element determine the border box of the element.
</p>

<style>
  html {
    font-size: 24px;
  }

  .a {
    width: 100%;
    padding: 1em;
    border: 3px solid #ccc;
  }

  .b {
    box-sizing: border-box;
    width: 100%;
    padding: 1em;
    border: 3px solid #ccc;
  }
</style>
```

![](https://files.mdnice.com/user/34286/8ccef2ef-9260-4d46-8ba2-045653a2e330.png)

## CSS中的常规流

### 行级排版上下文
- Inline Formatting Context(IFC)
- **只包含行级盒子**的容器会创建一个IFC
- IFC内的排版规则
  - 盒子在一行内水平摆放
  - 一行放不下时，换行展示
  - text-align决定一行内盒子的水平对齐
  - vertical-align决定一个盒子在行内的垂直对齐
  - 避开浮动元素（float）
```html
<div>
  This is a paragraph of text with long word Honorificabilitudinitatibus. Here is an image
  <img src="https://assets.codepen.io/59477/cat.png" alt="cat">
  And <em>Inline Block</em>
</div>

<style>
  div {
    width: 10em;
    //overflow-wrap: break-word;
    background: #411;
  }

  em {
    display: inline-block;
    width: 3em;
    background: #33c;
  }
</style>
```

![](https://files.mdnice.com/user/34286/13ef314a-28b0-413e-9ed3-7a8e582464ca.png)

### 块级排版上下文
- Block Formatting Context(BFC)
- 某些容器会创建一个BFC
  - 根元素
  - 浮动，绝对定位，inline-block
  - Flex子项和Grid子项
  - overflow值不是visible的块盒
  - display：flow-root
- BFC内的排版规则
  - 盒子从上到下摆放
  - 垂直margin合并
  - BFC内的盒子margin不会与外面合并
  - BFC不会和浮动元素重叠

```html
<span>
  This is a text and
  <div>block</div>
  and other text.
</span>

<style>
  span {
    line-height: 3;
    border: 2px solid red;
    background: coral;
  }

  div {
    line-height: 1.5;
    background: lime;
  }
</style>
```

![](https://files.mdnice.com/user/34286/bfff0aff-f980-4e25-b811-50684671e22b.png)
## 声明

- 本文所记述内容为作者个人学习的记载，不得以任何形式转发或者引用。

- 本文原文档已上传至作者GitHub，可自行查阅。