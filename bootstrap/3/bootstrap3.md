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

# Bootstrap CSS学习

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

### 网络选项

|              | 超小设备手机（<768px）         | 小型设备平板电脑（≥768px）     | 中型设备台式电脑（≥992px）     | 大型设备台式电脑（≥1200px）    |
| :----------- | :----------------------------- | :----------------------------- | :----------------------------- | ------------------------------ |
| 网格行为     | 一直是水平的                   | 以折叠开始，断点以上是水平的   | 以折叠开始，断点以上是水平的   | 以折叠开始，断点以上是水平的   |
| 最大容器宽度 | None (auto)                    | 750px                          | 970px                          | 1170px                         |
| Class 前缀   | **.col-xs-**                   | **.col-sm-**                   | **.col-md-**                   | **.col-lg-**                   |
| 列数量和     | 12                             | 12                             | 12                             | 12                             |
| 最大列宽     | Auto                           | 60px                           | 78px                           | 95px                           |
| 间隙宽度     | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） | 30px （一个列的每边分别 15px） |
| 可嵌套       | Yes                            | Yes                            | Yes                            | Yes                            |
| 偏移量       | Yes                            | Yes                            | Yes                            | Yes                            |
| 列排序       | Yes                            | Yes                            | Yes                            | Yes                            |

### 基本网格结构

```html
<div class='container'>
    <div class='row'>
        <div class='col-*-*'>
            ***
        </div>
        <div class='col-*-*'>
            ***
        </div>
    </div>
    <div class='row'>
        ***
    </div>
</div>
```

### 偏移列

偏移列是一个更专业的布局功能，它可以给列腾出更多的空间来。例如，**.col-xs-\*** 类不支持偏移，但是它们可以简单地通过使用一个空的单元格来实现该效果。

为了在大屏幕显示器上使用偏移，请使用 **.col-md-offset-\*** 类。这些类会把一个列的左外边距（margin）增加 ***** 列，其中 ***** 范围是从 **1** 到 **11**。

在下面的实例中，我们有 <div class="col-md-6">..</div>，我们将使用 **.col-md-offset-3** class 来居中这个 div。

```html
<span>偏移列使用（居中使用）</span>
<div class="container" style="border: 1px solid;">
    <div class="row" style="height: 25px;">
        <div class="col-md-6 col-md-offset-3"></div>
    </div>
</div>
```

### 嵌套列

要在内容中使用嵌套列，需要添加一个新的**.row**，并在一个已有的 **.col-md-\*** 列内添加一组 **.col-md-\*** 列。

```html
<span>嵌套列</span>
<div class="container" style="border: 1px solid black;">
    <div class="row">
        <div class="col-md-3" style="height: 25px;background-color: gray;"></div>
        <div class="col-md-9" style="background-color: green;">
            <div class="row">
                <div class="col-md-6" style="height: 25px;background-color: aqua;">嵌套列111</div>
                <div class="col-md-2" style="height: 25px;background-color: brown;">嵌套列222</div>
            </div>
        </div>
    </div>
</div>
```

### 列排序

Bootstrap的列排序属性可以很好的控制列的显示顺序。

标签有 **.col-md-push-\*** 和 **.col-md-pull-\*** 类；

```html
<span>列排序1</span>
<div class="container">
    <div class="row">
        <p style="text-align: center;">排序前</p>
        <div class="col-md-4" style="height: 25px;background-color: aqua;"></div>
        <div class="col-md-8" style="height: 25px;background-color: greenyellow;"></div>
    </div>
    <div class="row">
        <p style="text-align: center;">排序后</p>
        <div class="col-md-4 col-md-push-8" style="height: 25px;background-color: aqua;"></div>
        <div class="col-md-8 col-md-pull-4" style="height: 25px;background-color: green;"></div>
    </div>
</div>
<span>列排序2</span>
<div class="container">
    <div class="row">
        <div id="px1" class="col-md-4" style="height: 25px;background-color: aqua;"></div>
        <div id="px2" class="col-md-8" style="height: 25px;background-color: green;"></div>
    </div>
</div>
```

```js
function func1(){
    var flag = false; 
    setInterval(function(){
        flag = !flag;
        if(flag){
            $('#px1').addClass('col-md-push-8');
            $('#px2').addClass('col-md-pull-4');
        }else{
            $('#px1').removeClass('col-md-push-8');
            $('#px2').removeClass('col-md-pull-4');
        }
    },3000);
}
```

## Bootstrap排版

Bootstrap 使用 Helvetica Neue、 Helvetica、 Arial 和 sans-serif 作为其默认的字体栈。

使用 Bootstrap 的排版特性，可以创建标题、段落、列表及其他内联元素。

### 内联子标题

给一个标题加上副标题，可以使用<code> <small></code>或者添加<code>.small</code>样式类；

```html
<p style="text-align: center;">*********内联子标题*********</p>
<div class="container" style="border: 1px solid red;">
    <h1>我是标题1 h1. <small>我是副标题1 h1</small></h1>
    <h2>我是标题2 h2. <small>我是副标题2 h2</small></h2>
    <h3>我是标题3 h3. <small>我是副标题3 h3</small></h3>
    <h4>我是标题4 h4. <small>我是副标题4 h4</small></h4>
    <h5>我是标题5 h5. <small>我是副标题5 h5</small></h5>
    <h6>我是标题6 h6. <small>我是副标题6 h6</small></h6>
</div>
```

### 引导主体副本

**引导主体文本**的目的是给段落添加强调，使用标签是<code>class='lead'</code>;

```html
<p style="text-align: center;">引导主体副本</p>
<div class="container" style="border: 1px solid red;">
    <h2>这里是标题</h2>
    <p class="lead">这里是标题解释段落，加上样式起强调作用。</p>
</div>
```

### 强调标签

```html
<p style="text-align: center;">强调标签</p>
<div class="container" style="border: 1px solid red;width: 500px;">
    <h2>这里是标题2<small>small设置文本是父文本大小的85%，没有换行效果</small></h2>
    <strong>strong是让文本加粗，没有换行效果</strong><br/>
    <em>em是让文本变为斜体，没有换行效果</em><br><br>
    <p class="text-left">向左对齐文本</p>
    <p class="text-center">居中对齐文本</p>
    <p class="text-right">向右对齐文本</p>
    <p class="text-muted">本行内容是减弱的 text-muted</p>
    <p class="text-primary">本行内容带有一个 primary class</p>
    <p class="text-success">本行内容带有一个 success class</p>
    <p class="text-info">本行内容带有一个 info class</p>
    <p class="text-warning">本行内容带有一个 warning class</p>
    <p class="text-danger">本行内容带有一个 danger class</p>
    <p class="text-justify">本行内容带有一个 justify class，超过长度会自动换行123456789789456123123456789</p>
</div>
```

### 缩写

Bootstrap针对缩写单词提供了标签<code><abbr></code> ; 该样式会在文本底部显示一条虚拟框。如果想要比默认字体更小的，可以添加<code>.initialism</code>;

```html
<p style="text-align: center;">缩写</p>
<div class="container" style="border: 1px solid red;">
    <abbr title="World Wide Web">WWW</abbr><br>
    <abbr title="World Wide Web" class="initialism">WWW</abbr>
</div>
```

### 地址

```html
<address>
  <strong>Some Company, Inc.</strong><br>
  007 street<br>
  Some City, State XXXXX<br>
  <abbr title="Phone">P:</abbr> (123) 456-7890
</address>
<address>
  <strong>Full Name</strong><br>
  <a href="mailto:#">mailto@somedomain.com</a>
</address>
```

### 引用

```html
<p style="text-align: center;">引用</p>
<div class="container" style="border: 1px solid red;">
    <blockquote>
        <p>
            这是一个默认的引用实例。这是一个默认的引用实例。这是一个默认的引用实例。
        </p>
    </blockquote>
    <blockquote>
        这是一个带有源标题的引用。
        <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
    </blockquote>
    <blockquote class="pull-right">
        这是一个向右对齐的引用。
        <small>Someone famous in <cite title="Source Title">Source Title</cite></small>
    </blockquote>
</div>
```

### 列表

Bootstrap支持【有序列表】、【无序列表】、【定义列表】三个；

- **有序列表**：有序列表是指以数字或其他有序字符开头的列表。
- **无序列表**：无序列表是指没有特定顺序的列表，是以传统风格的着重号开头的列表。如果您不想显示这些着重号，您可以使用 class *.list-unstyled* 来移除样式。您也可以通过使用 class *.list-inline* 把所有的列表项放在同一行中。
- **定义列表**：在这种类型的列表中，每个列表项可以包含 <dt> 和 <dd> 元素。<dt> 代表 *定义术语*，就像字典。接着，<dd> 是 <dt> 的描述。`.dl-horizontal` 可以让 `<dl>` 内的短语及其描述排在一行。开始是像 `<dl>` 的默认样式堆叠在一起，随着导航条逐渐展开而排列在一行。

```html
<p style="text-align: center;">列表</p>
<div class="container" style="border: 1px solid red;">
    <h4>有序列表ol</h4>
    <ol>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
        <li>Item 4</li>
    </ol>
    <h4>无序列表ul</h4>
    <ul>
        <li>item1</li>
        <li>item2</li>
        <li>item3</li>
        <li>item4</li>
    </ul>
    <h4>未定义样式列表ul</h4>
    <ul class="list-unstyled">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
        <li>Item 4</li>
    </ul>
    <h4>内联列表</h4>
    <ul class="list-inline">
        <li>item1</li>
        <li>item2</li>
        <li>item3</li>
    </ul>
    <h4>定义列表</h4>
    <dl>
        <dt>dt111</dt>
        <dd>dd222</dd>
    </dl>
    <h4>水平的定义列表</h4>
    <dl class="dl-horizontal">
        <dt>dt111</dt>
        <dd>dd111</dd>
        <dt>dt222</dt>
        <dd>dd222</dd>
    </dl>
</div>
```

## Bootstrap表格

### 表格基础元素

| 标签      | 描述                                                         |
| :-------- | :----------------------------------------------------------- |
| <table>   | 为表格添加基础样式。                                         |
| <thead>   | 表格标题行的容器元素（<tr>），用来标识表格列。               |
| <tbody>   | 表格主体中的表格行的容器元素（<tr>）。                       |
| <tr>      | 一组出现在单行上的表格单元格的容器元素（<td> 或 <th>）。     |
| <td>      | 默认的表格单元格。                                           |
| <th>      | 特殊的表格单元格，用来标识列或行（取决于范围和位置）。必须在 <thead> 内使用。 |
| <caption> | 关于表格存储内容的描述或总结。                               |

### 表格类

| 类               | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| .table           | 为任意 <table> 添加基本样式 (只有横向分隔线)                 |
| .table-striped   | 在 <tbody> 内添加斑马线形式的条纹 ( IE8 不支持) --(自测并没有啥效果) |
| .table-bordered  | 为所有表格的单元格添加边框                                   |
| .table-hover     | 在 <tbody> 内的任一行启用鼠标悬停状态                        |
| .table-condensed | 让表格更加紧凑                                               |

### tr,td,th类

| 类       | 描述                             |
| :------- | :------------------------------- |
| .active  | 将悬停的颜色应用在行或者单元格上 |
| .success | 表示成功的操作                   |
| .info    | 表示信息变化的操作               |
| .warning | 表示一个警告的操作               |
| .danger  | 表示一个危险的操作               |

```html
<div class="container">
    <p style="text-align: center;">基础表格</p>
    <table class="table table-striped table-bordered table-hover table-condensed">
        <thead>
            <tr>
                <th>序号</th>
                <th>名字</th>
            </tr>
        </thead>
        <tbody>
            <tr class="active">
                <td>1</td>
                <td>宋书航</td>
            </tr>
            <tr class="success">
                <td>2</td>
                <td>白</td>
            </tr>
            <tr>
                <td>3</td>
                <td>阿十六</td>
            </tr>
        </tbody>
    </table>
</div>
```

### 响应式表格

通过把任意的 *.table* 包在 *.table-responsive* class 内，可以让表格水平滚动以适应小型设备（小于 768px）。当在大于 768px 宽的大型设备上查看时，将看不到任何的差别。

*备注：加上container都一样了。。。。*

```html
<div class="container table-responsive">
    <p style="text-align: center;">响应式表格</p>
    <table class="table table-striped table-bordered table-hover table-condensed">
        <thead>
            <tr>
                <th>序号</th>
                <th>名字</th>
            </tr>
        </thead>
        <tbody>
            <tr class="active">
                <td>1</td>
                <td>宋书航</td>
            </tr>
            <tr class="success">
                <td>2</td>
                <td>白</td>
            </tr>
            <tr>
                <td>3</td>
                <td>阿十六</td>
            </tr>
        </tbody>
    </table>
</div>
```

## Bootstrap表单

### 表单布局

Bootstrap提供了三种表单布局：

- 垂直表单（默认）
- 内联表单
- 水平表单

### 垂直表单

创建垂直表单的步骤：

1. 向父<code><form></code>元素添加<code>role='form'</code>
2. 把标签和控件放在一个带有class<code>.form-group</code>的div中。这是获取最佳间距所必须的
3. 向所有的文本元素 <input>、<textarea> 和 <select> 添加 class ="*form-control*" 。

```html
<div class="container" style="border: 1px solid red;">
    <form role="form">
        <div class="form-group">
            <label for="name">名称</label>
            <input type="text" name="name" id="name" class="form-control" placeholder="请输入名称">
        </div>
        <div class="form-group">
            <label for="inputFile">文件上传</label>
            <input type="file" name="inputFile" id="inputFile">
        </div>
        <div class="checkbox">
            <label>
                <input type="checkbox">请打勾
            </label>
        </div>
        <button type="submit" class="btn btn-default">提交</button>
    </form>
</div>
```

### 内联表单

如果需要创建一个表单，它的所有元素是内联的，向左对齐的，标签是并排的，请向 <form> 标签添加 class *.form-inline*。

**使用内联表单需要注意：**

- 默认情况下，Bootstrap 中的 input、select 和 textarea 有 100% 宽度。在使用内联表单时，您需要在表单控件上设置一个宽度。
- 使用 class *.sr-only*，您可以隐藏内联表单的标签。

```html
<div class="container" style="border: 1px solid black;">
    <form class="form-inline" role="form">
        <div class="form-group">
            <label class="sr-only" for="name">名称</label>
            <input type="text" class="form-control" id="name" placeholder="请输入名称">
        </div>
        <div class="form-group">
            <label class="sr-only" for="inputfile">文件输入</label>
            <input type="file" id="inputfile">
        </div>
        <div class="checkbox">
            <label>
                <input type="checkbox">请打勾
            </label>
        </div>
        <button type="submit" class="btn btn-default">提交</button>
    </form>
</div>
```

### 水平表单

如需创建一个水平布局的表单，请按下面的几个步骤进行：

- 向父 <form> 元素添加 class *.form-horizontal*。
- 把标签和控件放在一个带有 class *.form-group* 的 <div> 中。
- 向标签添加 class *.control-label*。

```html
<div class="container" style="border: 1px solid gold;">
    <form class="form-horizontal" role="form">
        <div class="form-group">
            <label for="username" class="col-sm-2 control-label">用户名</label>
            <div class="col-sm-10">
                <input type="text" class="form-control" id="username" placeholder="请输入用户名">
            </div>
        </div>
        <div class="form-group">
            <label for="password" class="col-sm-2 control-label">密码</label>
            <div class="col-sm-10">
                <input type="password" class="form-control" id="password" placeholder="请输入密码">
            </div>
        </div>
        <div class="form-group">
            <div class="col-sm-offset-2 col-sm-10">
                <div class="checkbox">
                    <label>
                        <input type="checkbox">请记住我
                    </label>
                </div>
            </div>
        </div>
        <div class="form-group">
            <div class="col-sm-offset-2 col-sm-10">
                <button type="submit" class="btn btn-default">登录</button>
            </div>
        </div>
    </form>
</div>
```

### 支持的表单控件

Bootstrap 支持最常见的表单控件，主要是 *input、textarea、checkbox、radio 和 select*。

#### 输入框（Input）

最常见的表单文本字段是输入框 input。用户可以在其中输入大多数必要的表单数据。Bootstrap 提供了对所有原生的 HTML5 的 input 类型的支持，包括：*text、password、datetime、datetime-local、date、month、time、week、number、email、url、search、tel* 和 *color*。适当的 *type* 声明是必需的，这样才能让 *input* 获得完整的样式。

```html
<div class="form-group">
    <label for="username" class="col-sm-2 control-label">用户名</label>
    <div class="col-sm-10">
        <input type="text" class="form-control" id="username" placeholder="请输入用户名">
    </div>
</div>
<div class="form-group">
    <label for="password" class="col-sm-2 control-label">密码</label>
    <div class="col-sm-10">
        <input type="password" class="form-control" id="password" placeholder="请输入密码">
    </div>
</div>
<div class="form-group">
    <label for="t0" class="col-sm-2 control-label">datetime(没啥用)</label>
    <div class="col-sm-10">
        <input type="datetime" name="t0" id="t0" class="form-control" >
    </div>
</div>
<div class="form-group">
    <label for="t1" class="col-sm-2 control-label">datetime-local（很难用，点击后不会自动隐藏）</label>
    <div class="col-sm-10">
        <input type="datetime-local" name="t1" id="t1" class="form-control" >
    </div>
</div>
<div class="form-group">
    <label for="t2" class="col-sm-2 control-label">date</label>
    <div class="col-sm-10">
        <input type="date" name="t2" id="t2" class="form-control" >
    </div>
</div>
<div class="form-group">
    <label for="t3" class="col-sm-2 control-label">month</label>
    <div class="col-sm-10">
        <input type="month" name="t3" id="t3" class="form-control" >
    </div>
</div>
<div class="form-group">
    <label for="t4" class="col-sm-2 control-label">week</label>
    <div class="col-sm-10">
        <input type="week" name="t4" id="t4" class="form-control" >
    </div>
</div>
<div class="form-group">
    <label for="t5" class="col-sm-2 control-label">search和普通输入差不多</label>
    <div class="col-sm-10">
        <input type="search" name="t5" id="t5" class="form-control" >
    </div>
</div>
```

#### 文本框（Textarea）

```html
<div class="form-group">
    <label for="name">文本框</label>
    <textarea class="form-control" rows="3"></textarea>
</div>
```

#### 复选框（Checkbox）和单选框（Radio）

复选框和单选按钮用于让用户从一系列预设置的选项中进行选择。

- 当创建表单时，如果您想让用户从列表中选择若干个选项时，请使用 *checkbox*。如果您限制用户只能选择一个选项，请使用 *radio*。
- 对一系列复选框和单选框使用 *.checkbox-inline* 或 *.radio-inline* class，控制它们显示在同一行上。

```html
<!-- 复选框 -->
<div class="form-group">
    <label for="hobby" class="col-sm-2 control-label">爱好</label>
    <div class="col-sm-10">
        <label class="checkbox-inline"><input type="checkbox" name="hobby" value="">篮球</label>
        <label class="checkbox-inline"><input type="checkbox" name="hobby" value="">足球</label>
    </div>
</div>
<!-- 单选框 -->
<div class="form-group">
    <label for="gender" class="col-sm-2 control-label">性别</label>
    <div class="col-sm-10">
        <label class="radio-inline"><input type="radio" name="gender">男</label>
        <label class="radio-inline"><input type="radio" name="gender">女</label>
    </div>
</div>
```

#### 选择框（Select）

当您想让用户从多个选项中进行选择，但是默认情况下只能选择一个选项时，则使用选择框。

- 使用 <select> 展示列表选项，通常是那些用户很熟悉的选择列表，比如州或者数字。
- 使用 *multiple="multiple"* 允许用户选择多个选项。

```html
<!-- 下拉选项 -->
<div class="form-group">
    <label for="birthplace" class="col-sm-2 control-label">出生地</label>
    <div class="col-sm-10">
        <select name="birthplace" id="birthplace" class="form-control">
            <option value="">---请选择---</option>
            <option value="1">北京</option>
            <option value="2">上海</option>
        </select>
    </div>
</div>
<div class="form-group">
    <label for="identify" class="col-sm-2 control-label">身份（下拉多选不好用）</label>
    <div class="col-sm-10">
        <select name="identify" id="identify" class="form-control" multiple>
            <option value="">---请选择---</option>
            <option value="1">学生</option>
            <option value="2">成年人</option>
            <option value="3">男人</option>
        </select>
    </div>
</div>
```

#### 静态控件

当您需要在一个水平表单内的表单标签后放置纯文本时，请在 <p> 上使用 class *.form-control-static*。

```html
<!-- 静态控件 -->
<div class="form-group">
    <label class="col-sm-2 control-label">Email</label>
    <div class="col-sm-10">
        <p class="form-control-static">email@example.com</p>
    </div>
</div>
```

#### 控件状态

1. 禁用的输入框 input

   如果您想要禁用一个输入框 input，只需要简单地添加 disabled 属性，这不仅会禁用输入框，还会改变输入框的样式以及当鼠标的指针悬停在元素上时鼠标指针的样式。

2. 禁用的字段集 fieldset
   对 <fieldset> 添加 disabled 属性来禁用 <fieldset> 内的所有控件。

3. 验证状态
   Bootstrap 包含了错误、警告和成功消息的验证样式。只需要对父元素简单地添加适当的 class（.has-warning、 .has-error 或 .has-success）即可使用验证状态。

#### 表单帮助文本

Bootstrap 表单控件可以在输入框 input 上有一个块级帮助文本。为了添加一个占用整个宽度的内容块，请在 <input> 后使用 *.help-block*。

```html
<form role="form">
  <span>帮助文本实例</span>
  <input class="form-control" type="text" placeholder="">
  <span class="help-block">一个较长的帮助文本块，超过一行，
  需要扩展到下一行。本实例中的帮助文本总共有两行。</span>
</form>
```

