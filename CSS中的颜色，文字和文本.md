# CSS中的颜色，文字和文本

## 颜色
**预定义的颜色值**：

black、white、red、green、blue、lightblue等

**16进制表示法**：

使用6位16进制数表示颜色，例如：#ADD8E6
其中第1-2位表示红色，第3-4位表示绿色，第5-6位表示蓝色

简写方式：#ABC，等价于#AABBCC

**RGB表示法**：

rgb(173, 216, 230)

其中第一个数表示红色，第二个数表示绿色，第三个数表示蓝色

**RGBA表示法**：

rgba(173, 216, 230, 0.5)。

前三个数同上，第四个数表示透明度

**HSL**：
- Hue：色相(H)色彩的基本属性，如红色，黄色等，取值范围为0~360
- Saturation：饱和度(S)是指色彩的鲜艳程度，越高越鲜艳，取值范围为0~100%
- Lightness：亮度(L)指颜色的明亮程度；越高颜色越亮；取值范围为0~100%

**alpha透明度**：

表示色彩的透明度，取值范围为0~1，可以与RGB和HSL组合使用构成RGBA和HSLA，使用16进制表示时，会多出两位

## 字体
**font-size**：

CSS 属性指定字体的大小。因为该属性的值会被用于计算em和ex长度单位，定义该值可能改变其他元素的大小。
- 关键词：small,mediun,large
- 长度：px,em (换算px/16=em)
- 百分数：相对于父元素的字体大小
```html
<section>
  <h2>A web font example</h2>
  <p class="note">Notes: Web fonts ...</p>
  <p>With this in mind, let's build...</p>
</section>

<style>
  section {
    font-size: 20px;
  }

  section h2{
    font-size: 2em;
  }

  section .note {
    font-size: 80%;
    color: orange;
  }
</style>
```

![](https://files.mdnice.com/user/34286/42c7e25b-ec1f-4827-b82a-a320a008c74e.png)


**font-style**:

 CSS 属性允许你选择 font-family 字体下的 italic 或 oblique 样式。
```html
<p class="normal">Normal Text</p>
<p class="italic">Italic Text</p>

<style>
  p {
    font-size: 36px;
    font-family: "Helvetica Neue", sans-serif;
  }

  .normal {
    font-style: normal;
  }

  .italic {
    font-style: italic
  }
</style>
```

![](https://files.mdnice.com/user/34286/dd58aac2-f82f-4b04-9788-9cafccca11b9.png)

**font-weight**:

CSS 属性指定了字体的粗细程度。 一些字体只提供 normal 和 bold 两种值。
```html
<ul>
  <li class="w1">锦瑟无端五十弦（100）</li>
  <li class="w2">锦瑟无端五十弦（200）</li>
  <li class="w3">锦瑟无端五十弦（300）</li>
  <li class="w4">锦瑟无端五十弦（400-normal）</li>
  <li class="w5">锦瑟无端五十弦（500）</li>
  <li class="w6">锦瑟无端五十弦（600）</li>
  <li class="w7">锦瑟无端五十弦（700-bold）</li>
  <li class="w8">锦瑟无端五十弦（800）</li>
  <li class="w9">锦瑟无端五十弦（900）</li>
</ul>

<style>
  .w1 { font-weight: 100 }
  .w2 { font-weight: 200 }
  .w3 { font-weight: 300 }
  .w4 { font-weight: 400 }
  .w5 { font-weight: 500 }
  .w6 { font-weight: 600 }
  .w7 { font-weight: 700 }
  .w8 { font-weight: 800 }
  .w9 { font-weight: 900 }
</style>
```

![](https://files.mdnice.com/user/34286/ec9ccd6f-8b76-4018-8f86-af1cf209f835.png)

**font-family**:

CSS 属性 font-family 允许您通过给定一个有先后顺序的，由字体名或者字体族名组成的列表来为选定的元素设置字体。

属性值用逗号隔开。浏览器会选择列表中第一个该计算机上有安装的字体，或者是通过 @font-face 指定的可以直接下载的字体。

**建议：字体列表最后写上通用字体族，英文字体放在中文字体的前边**

```html
<h1>卡尔斯巴德洞窟（Carlsbad Caverns）</h1>
<p>卡尔斯巴德洞窟（Carlsbad Caverns）是美国的
一座国家公园，位于新墨西哥州东南部。游客可以通过天
然入口徒步进入，也可以通过电梯直接到达230米的洞穴
深处。</p>

<style>
  h1 {
    font-family: Optima, Georgia, serif;
  }
  body {
    font-family: Helvetica, sans-serif;
  }
</style>
```

![](https://files.mdnice.com/user/34286/aaebb4a4-8ef6-459d-b1c3-f4de449f1f3a.png)
```html
<h1>Web fonts are awesome!</h1>

<style>
  @font-face {
    font-family: "Megrim";
    src: url(https://fonts.gstatic.com/s/megrim/v11/46kulbz5WjvLqJZVam_hVUdI1w.woff2) format('woff2');
  }

  h1 {
    font-family: Megrim, Cursive;
  }
</style>
```

![](https://files.mdnice.com/user/34286/19ebaa7d-71a2-466a-b6e5-08c73db638a4.png)
```html
<style>
  @font-face {
    font-family: f1;
    src: url("//s2.ssl.qhimg.com/static/ff00cb8151eeecd2.woff2") format("woff2");
  }

  @font-face {
    font-family: f2;
    src: url("//s3.ssl.qhimg.com/static/a59a90c9e8f21898.woff2") format("woff2");
  }

  @font-face {
    font-family: f3;
    src: url("//s2.ssl.qhimg.com/static/58324737c4cb53a5.woff2") format("woff2");
  }

  h1 {
    font-size: 50px;
  }
</style>

<h1 style="font-family: f1, serif">落霞与孤鹜齐飞，秋水共长天一色。</h1>
<h1 style="font-family: f2, serif">落霞与孤鹜齐飞，秋水共长天一色。</h1>
<h1 style="font-family: f3, serif">落霞与孤鹜齐飞，秋水共长天一色。</h1>
```

![](https://files.mdnice.com/user/34286/ff454acc-e663-42a5-847b-c2c4678bccc6.png)

## 文本
**text-align**:

CSS属性定义行内内容（例如文字）如何相对它的块父元素对齐。text-align 并不控制块元素自己的对齐，只控制它的行内内容的对齐。

![](https://files.mdnice.com/user/34286/ce7af6a8-7476-44dd-8499-8b42d8c2a484.png)

![](https://files.mdnice.com/user/34286/dd90939e-e9ce-4a4f-bbb3-ab80901c7d42.png)

![](https://files.mdnice.com/user/34286/54d6aecf-53d9-4a8b-a575-e2635f96f2f2.png)

![](https://files.mdnice.com/user/34286/128bfa05-8960-4789-9322-25d14d0e0467.png)


**line-height**:

CSS 属性用于设置多行元素的空间量，如多行文本的间距。对于块级元素，它指定元素行盒（line boxes）的最小高度。对于非替代的 inline 元素，它用于计算行盒（line box）的高度。

行高的计算可以从一个的下边距到另一个下边距，也可以从一个的上边距到另外一个的上边距。

- 补充知识点：长度单位

| 单位 | 描述                     |
| ---: | :----------------------- |
|   px | 设备上的像素点           |
|    % | 相对于父元素的百分比     |
|   em | 相对于当前元素的字体大小 |
|  rem | 相对于根元素的字体大小   |
|   vw | 相对于视窗宽度的百分比   |
|   vh | 相对于视窗高度的百分比   |


```html
<section>
  <h1>Font families recap</h1>
  <p>As we looked at in fundamental text and font styling, the fonts applied to your HTML can be controlled using the font-family property. This takes one or more font family names. </p>
</section>

<style>
  h1 {
    font-size: 30px;
    line-height: 45px;
  }

  p {
    font-size: 20px;
    line-height: 1.6;
  }
</style>
```

![](https://files.mdnice.com/user/34286/8f4c48a7-efc6-4c0e-ac60-fd5e51b9ed14.png)


**letter-spacing**:

CSS 的 letter-spacing 属性用于设置文本字符的间距。

![](https://files.mdnice.com/user/34286/3b0d939c-36d5-43f9-8931-0ff13767ad64.png)

![](https://files.mdnice.com/user/34286/b104ea2a-a4a4-4db3-ac4e-874bbe31f3c8.png)

**text-indent**：

能定义一个块元素首行文本内容之前的缩进量。

![](https://files.mdnice.com/user/34286/13819d89-a3ef-459f-9ef0-877a0a27e42e.png)

![](https://files.mdnice.com/user/34286/ec8d4fd6-7e7d-40e6-8384-6e6c12f128cb.png)

**text-decoration**：

这个 CSS 属性是用于设置文本的修饰线外观的（下划线、上划线、贯穿线/删除线 或 闪烁）它是 text-decoration-line, text-decoration-color, text-decoration-style, 和新出现的 text-decoration-thickness 属性的缩写。

![](https://files.mdnice.com/user/34286/bf956061-8653-4933-be32-36b246ec7dce.png)

![](https://files.mdnice.com/user/34286/05acf4af-1329-453b-9f5b-073cef1237fe.png)

![](https://files.mdnice.com/user/34286/50b27057-1ef4-41f7-b471-bfa391af097c.png)

![](https://files.mdnice.com/user/34286/4e728913-c910-4f4e-8e64-ea93c622e431.png)

**text-shadow**：

文字添加阴影。可以为文字与 text-decorations 添加多个阴影，阴影值之间用逗号隔开。每个阴影值由元素在X和Y方向的偏移量、模糊半径和颜色值组成。

## 声明

- 本文所记述内容为作者个人学习的记载，不得以任何形式转发或者引用。

- 本文原文档已上传至作者GitHub，可自行查阅。