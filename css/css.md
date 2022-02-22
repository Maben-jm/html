# CSS伪元素

## 什么是伪元素？

CSS伪元素用于设置元素指定部分的样式。

例如，它可以用于：

* 设置元素的首字母、首行的样式。
* 在元素的内容之前或之后插入内容。

## 语法

```css
selector::pseudo-element {
  property: value;
}
```

## ::first-line

<code>::first-line</code> 伪元素用于向文本的首行添加特殊样式。

```css
p::first-line{
    color:#ff0000;
    font-variant: small-caps;
}
```

<i>注：【::first-line】伪元素只能应用于块级元素。</i>

## ::first-letter

<code>::first-letter</code>伪元素用于向文本的首字母添加特殊样式。

```css
p::first-letter{
    color:#ff0000;
    font-size: xx-large;
}
```

<i>注：【::first-letter】伪元素只能应用于块级元素。</i>

## 伪元素和CSS类结合

```css
p.intro::first-letter{
    color:#ff0000;
    font-size:200%;
}
```

## 多个伪元素组合

在下面的例子中，段落的第一个字母将是红色，字体大小为 xx-large。第一行的其余部分将变为蓝色，并使用小型大写字母。该段的其余部分将是默认的字体大小和颜色：

```css
p::first-letter:{
    color: #ff0000;
    font-size: xx-large;
}
p::first-line{
    color: #0000ff;
    font-size: small-caps;
}
```

## ::before

<code>::before</code>伪元素可以用于在元素内容之前插入一些内容。

```css
h1::before{
    content: url(1.jpg);
}
```

## ::after

<code>::after</code>伪元素可以用于在元素内容之后插入一些内容。

```css
h1::after{
    content: url(2.jpg);
}
```

## ::selection

<code>::selection</code>伪元素匹配用户选择的元素部分。

以下 CSS 属性可以应用于 ::selection：

- color
- background
- cursor
- outline

```css
::selection{
    color: red;
    backgroud: yellow;
}
```

