* [CSS学习](#css学习)
  * [概览](#概览)
    * [HTML5 文档类型](#html5-文档类型)
    * [移动设备优先](#移动设备优先)
    * [响应式图像](#响应式图像)
    * [基本的全局展示](#基本的全局展示)
    * [链接样式](#链接样式)
    * [容器](#容器)
    * [Bootstrap支持的浏览器](#bootstrap支持的浏览器)
  * [Bootstrap网格系统](#bootstrap网格系统)
    * [什么是网格Grid？](#什么是网格grid)
    * [Bootstrap网格系统的工作原理](#bootstrap网格系统的工作原理)
    * [媒体查询](#媒体查询)

# CSS学习

## 概览

> 在这一章中，我们将讲解 Bootstrap 底层结构的关键部分，包括我们让 web 开发变得更好、更快、更强壮的最佳实践。

### HTML5 文档类型

Bootstrap使用了一些HTML5元素和CSS属性。为了让这些正常工作，需要使用HMTL5文档类型；

```html
<!DOCTYPE html>
<html>
...
</html>
```

### 移动设备优先

  <font color='red'>Bootstrap3的设计目的是移动设备优先，然后才是桌面设备。</font>为了让Bootstrap开发的网站对移动设备友好，确保适当的绘制和触屏缩放，需要在网页的head之中添加<code>viewport meta</code>标签，如下所示：

```html
<head>
    <!-- 
		【initial-scale】:最初规模 | 【1.0】：页面加载时，以1：1比例呈现，不会任何缩放。
		【user-scalable=no】：禁用其缩放功能。
		【maximum-scale=1.0】通常和【user-scalable=no】一起使用，这样禁用缩放功能之后，用户只能滚动屏幕。
	-->
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
</head>
```

### 响应式图像

```html
<img src="..." class="img-responsive" alt="响应式图像">
```

通过添加<code>img-responsive</code>class可以让Bootstrap3中的图像对响应式布局的支持更好。

默认样式是这样的：

```css
.img-responsive{
    display: block; 
    height: auto;
    max-width: 100%;
}
```

【 display: block】：图像以块级元素显示。

【height: auto】：相关元素的高度取决于浏览器。

【 max-width: 100%】：会重写任何通过width属性指定的高度，让图片对响应式布局支持更好。

<i>注：想要让【img-responsive】类的图片水平居中，使用 .center-block 类，不要使用.text-center</i>

### 基本的全局展示

Bootstrap3使用<code>body{margin:0}</code>来移除body的边距。

下面是Bootstrap3的设置：

```css
body{
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 14px;
  line-height: 1.428571429;
  color: #333333;
  background-color: #ffffff;
}
```

- 【font-family】设置默认字体样式
- 【font-size】设置默认字体发小
- 【line-height】设置默认行高度
- 【color】设置默认文本颜色
- 【background-color】设置默认背景颜色

### 链接样式

链接的默认样式如下：

```css
a:hover,
a:focus {
  color: #2a6496;
  text-decoration: underline;
}

a:focus {
  outline: thin dotted #333;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
```

效果：

​	1、当鼠标悬停在链接上，或者点击过的链接，颜色会被设置为 #2a6496。同时，会呈现一条下划线。

​    2、点击过的链接，会呈现一个颜色码为 #333 的细的虚线轮廓。

​	3、另一条规则是设置轮廓为 5 像素宽，且对于基于 webkit 浏览器有一个 -webkit-focus-ring-color 的浏览器扩展。轮廓偏移设置为 -2 像素。

### 容器

```html
<div class="container">
    ...
</div>
```

下面是<code>.container</code>Class的默认样式：

```css
.container {
   padding-right: 15px;
   padding-left: 15px;
   margin-right: auto;
   margin-left: auto;
}
```

通过上面的样式可以看出，container的左右外边距是交由浏览器控制的。

但是，由于内边距是固定宽度，所以默认情况下<font color='red'>容器是不可嵌套的</font >。

### Bootstrap支持的浏览器

Bootstrap 可以在最新的桌面系统和移动端浏览器中很好的工作。

旧的浏览器可能无法很好的支持。

下表为 Bootstrap 支持最新版本的浏览器和平台：

|              | Chrome | Firefox | IE     | Opera  | Safari |
| :----------- | :----- | :------ | :----- | :----- | :----- |
| **Android**  | YES    | YES     | 不适用 | 不适用 | 不适用 |
| **iOS**      | YES    | 不适用  | 不适用 | 不适用 | YES    |
| **Mac OS X** | YES    | YES     | 不适用 | YES    | YES    |
| **Windows**  | YES    | YES     | YES*   | YES    | 不适用 |

\* Bootstrap 支持 Internet Explorer 8 及更高版本的 IE 浏览器。

## Bootstrap网格系统

Bootstrap提供了一套响应式、移动设备优先的流式网格系统，随着屏幕或者视口尺寸的增加，系统会自动分成12列。

### 什么是网格Grid？

简单的说，网页设计中的网格用于组织内容，让网站易于浏览，并降低用户端的负载。

### Bootstrap网格系统的工作原理

网格系统通过一系列包含内容的行和列来创建页面布局。Bootstrap的工作原理是：

* 行必须放在【.container】Class中,以便于获得适当的对其（alignment）和内边距（padding）
* 使用行来创建列的水平组。
* 内容应该放置在列内，且唯有列可以是行的直接子元素。
* 预定义的网格类，比如【.row】和【.col-xs-4】，可用于快速创建网络布局。
* 列通过内边距（padding）来创建列内容之间的间隙。该内边距是通过【.row】上的外边距（margin）取负，表示第一列和最后一列的行偏移。
* 网络系统是通过横跨的十二个可用的列来创建的。例如：要创建三个相等的列，则使用三个【.col-xs-4】

### 媒体查询

媒体查询是非常别致的“有条件的查询”。它只适用于一些基于某些规定条件的CSS。如果满足那些条件，则应用相应的样式。

Bootstrap中的媒体查询允许基于视口大小移动，显示并隐藏内容