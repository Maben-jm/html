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

## Bootstrap按钮

### 基础样式

以下样式可用于<a>, <button>, 或 <input> 元素上：

| 类           | 描述                                    |
| :----------- | :-------------------------------------- |
| .btn         | 为按钮添加基本样式                      |
| .btn-default | 默认/标准按钮                           |
| .btn-primary | 原始按钮样式（未被操作）                |
| .btn-success | 表示成功的动作                          |
| .btn-info    | 该样式可用于要弹出信息的按钮            |
| .btn-warning | 表示需要谨慎操作的按钮                  |
| .btn-danger  | 表示一个危险动作的按钮操作              |
| .btn-link    | 让按钮看起来像个链接 (仍然保留按钮行为) |
| .btn-lg      | 制作一个大按钮                          |
| .btn-sm      | 制作一个小按钮                          |
| .btn-xs      | 制作一个超小按钮                        |
| .btn-block   | 块级按钮(拉伸至父元素100%的宽度)        |
| .active      | 按钮被点击                              |
| .disabled    | 禁用按钮                                |

### 按钮大小

下表列出了获得各种大小按钮的 class：

| Class      | 描述                                         |
| :--------- | :------------------------------------------- |
| .btn-lg    | 这会让按钮看起来比较大。                     |
| .btn-sm    | 这会让按钮看起来比较小。                     |
| .btn-xs    | 这会让按钮看起来特别小。                     |
| .btn-block | 这会创建块级的按钮，会横跨父元素的全部宽度。 |

### 按钮状态

```html
<div class="container" style="border: 1px solid red;">
    <p>
        <button type="button" class="btn btn-default btn-lg ">默认按钮</button>
        <button type="button" class="btn btn-default btn-lg active">激活按钮</button>
    </p>
    <p>
        <button type="button" class="btn btn-default btn-lg">默认按钮</button>
        <button type="button" class="btn btn-default btn-lg" disabled="disabled">禁用按钮</button>
    </p>
</div>
```

### 按钮组

> 在 div 中直接使用 .btn-group 可以创建按钮组：

```html
<div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```

> 使用 .btn-group-lg|sm|xs 来控制按钮组的大小：

```html
<div class="btn-group btn-group-lg">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <button type="button" class="btn btn-primary">Sony</button>
</div>
```

> 如果要设置垂直方向的按钮可以通过 .btn-group-vertical 类来设置：

```html
<div class="btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```

> 自适应大小的按钮组,通过 .btn-group-justified 类

```html
<div class="btn-group btn-group-justified">
    <a href="#" class="btn btn-primary">Apple</a>
    <a href="#" class="btn btn-primary">Samsung</a>
    <a href="#" class="btn btn-primary">Sony</a>
</div>
<!-- 如果是 <button> 元素, 你需要在外层使用 .btn-group 类来包裹 -->
<div class="btn-group btn-group-justified">
    <div class="btn-group">
        <button type="button" class="btn btn-primary">Apple</button>
    </div>
    <div class="btn-group">
        <button type="button" class="btn btn-primary">Samsung</button>
    </div>
    <div class="btn-group">
        <button type="button" class="btn btn-primary">Sony</button>
    </div>
</div>
```

### 内嵌下拉菜单的按钮组

```html
<div class="container" style="border: 1px solid red;">
    <div class="btn-group">
        <button type="button" class="btn btn-primary">Apple</button>
        <button type="button" class="btn btn-primary">Samsung</button>
        <div class="btn-group">
            <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
                Sony <span class="caret"></span>
            </button>
            <ul class="dropdown-menu" role="menu">
                <li><a href="#">Tablet</a></li>
                <li><a href="#">Smartphone</a></li>
            </ul>
        </div>
    </div>
</div>
```

### 分割按钮

```html
<div class="container" style="border: 1px solid red;">
    <div class="btn-group">
        <button type="button" class="btn btn-primary">Sony</button>
        <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
            <span class="caret"></span>
        </button>
        <ul class="dropdown-menu" role="menu">
            <li><a href="#">Tablet</a></li>
            <li><a href="#">Smartphone</a></li>
        </ul>
    </div>
</div>
```

## Bootstrap图片

### 普通样式

Bootstrap 提供了三个可对图片应用简单样式的 class：

- *.img-rounded*：添加 *border-radius:6px* 来获得图片圆角。
- *.img-circle*：添加 *border-radius:50%* 来让整个图片变成圆形。
- *.img-thumbnail*：添加一些内边距（padding）和一个灰色的边框。

### 响应式图片

通过在 <img> 标签添加 .img-responsive 类来让图片支持响应式设计。 图片将很好地扩展到父元素。

.img-responsive 类将 max-width: 100%; 和 height: auto; 样式应用在图片上

# Bootstrap布局组件

## Bootstrap字体图标

Bootstrap 捆绑了 200 多种字体格式的字形。首先让我们先来理解一下什么是字体图标。

在 *fonts* 文件夹内可以找到字体图标，它包含了下列这些文件：

- glyphicons-halflings-regular.eot
- glyphicons-halflings-regular.svg
- glyphicons-halflings-regular.ttf
- glyphicons-halflings-regular.woff

相关的 CSS 规则写在 *dist* 文件夹内的 css 文件夹内的 *bootstrap.css* 和 *bootstrap-min.css* 文件上。

```html
<!-- 定制字体图标(使用字体样式改变图标) -->
<button type="button" class="btn btn-primary btn-lg">
  <span class="glyphicon glyphicon-user"></span> User
</button>
<!-- 定制字体大小 -->
<button type="button" class="btn btn-primary btn-lg" style="font-size: 60px">
  <span class="glyphicon glyphicon-user"></span> User
</button>
<!-- 定制字体颜色 -->
<button type="button" class="btn btn-primary btn-lg" style="color: rgb(212, 106, 64);">
  <span class="glyphicon glyphicon-user"></span> User
</button>
<!-- 应用文本阴影（这个比较帅） -->
<button type="button" class="btn btn-primary btn-lg" style="text-shadow: black 5px 3px 3px;">
  <span class="glyphicon glyphicon-user"></span> User
</button>
```

## Bootstrap下拉菜单

Bootstrap下拉菜单（DropDowns）是可切换的，是以列表格式显示链接的上下文菜单。

### 基本下拉菜单

```html
<div class="container" style="border: 1px solid red;">
    <div class="dropdown">
        <button type="button" class="btn dropdown-toggle" id="dropdownMenu1" data-toggle="dropdown">
            主题<span class="caret"></span>
        </button>
        <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">Java</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据挖掘</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据通信/网络</a>
            </li>
            <li role="presentation" class="divider"></li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">分离的链接</a>
            </li>
        </ul>
    </div>
</div>
```

### 下拉框标题

```html
<div class="container" style="border: 1px solid red;">
    <div class="dropdown">
        <button type="button" class="btn dropdown-toggle" id="dropdownMenu1" data-toggle="dropdown">
            主题<span class="caret"></span>
        </button>
        <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">Java</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据挖掘</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据通信/网络</a>
            </li>
            <li role="presentation" class="divider"></li>
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">分离的链接</a>
            </li>
        </ul>
    </div>
</div>
```

### 向上弹出(dropup)

```html
<div class="container" style="border: 1px solid red;">
    <div class="dropdown dropup">
        <button type="button" class="btn dropdown-toggle" id="dropdownMenu1" data-toggle="dropdown">
            向上弹出<span class="caret"></span>
        </button>
        <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">Java</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据挖掘</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据通信/网络</a>
            </li>
            <li role="presentation" class="divider"></li>
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">分离的链接</a>
            </li>
        </ul>
    </div>
</div>
```

### 禁用项(disabled)

```html
<div class="container" style="border: 1px solid red;">
    <div class="dropdown">
        <button type="button" class="btn dropdown-toggle" id="dropdownMenu1" data-toggle="dropdown">
            主题<span class="caret"></span>
        </button>
        <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">Java</a>
            </li>
            <li role="presentation" class="disabled">
                <a role="menuitem" tabindex="-1" href="#">数据挖掘</a>
            </li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">数据通信/网络</a>
            </li>
            <li role="presentation" class="divider"></li>
            <li role="presentation" class="dropdown-header">下拉菜单标题</li>
            <li role="presentation">
                <a role="menuitem" tabindex="-1" href="#">分离的链接</a>
            </li>
        </ul>
    </div>
</div>
```

## Bootstrap按钮组

按钮组允许多个按钮被堆叠在同一行上。

| Class                                       | 描述                                                         | 代码示例                                                     |
| :------------------------------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| .btn-group                                  | 该 class 用于形成基本的按钮组。在 **.btn-group** 中放置一系列带有 class **.btn** 的按钮。 | `<div class="btn-group">  <button type="button" class="btn btn-default">Button1</button>   <button type="button" class="btn btn-default">Button2</button> </div>` |
| .btn-toolbar                                | 该 class 有助于把几组 <div class="btn-group"> 结合到一个 <div class="btn-toolbar"> 中，一般获得更复杂的组件。 | `<div class="btn-toolbar" role="toolbar">  <div class="btn-group">...</div>  <div class="btn-group">...</div> </div>` |
| .btn-group-lg, .btn-group-sm, .btn-group-xs | 这些 class 可应用到整个按钮组的大小调整，而不需要对每个按钮进行大小调整。 | `<div class="btn-group btn-group-lg">...</div> <div class="btn-group btn-group-sm">...</div> <div class="btn-group btn-group-xs">...</div>` |
| .btn-group-vertical                         | 该 class 让一组按钮垂直堆叠显示，而不是水平堆叠显示。        | `<div class="btn-group-vertical">  ... </div>`               |

## Bootstrap输入框组

### 基本的输入框组

```html
<form class="form-horizontal" role="form">
    <div class="form-group">
        <label class="col-sm-2 control-label">启动资金1</label>
        <div class="col-sm-10">
            <div class="input-group">
                <input type="text" class="form-control">
                <span class="input-group-addon">.00</span>
            </div>
        </div>
    </div>
    <div class="form-group">
        <label class="col-sm-2 control-label">启动资金2</label>
        <div class="col-sm-10">
            <div class="input-group">
                <span class="input-group-addon">$</span>
                <input type="text" class="form-control">
                <span class="input-group-addon">.00</span>
            </div>
        </div>
    </div>
</form>
```

### 复选框和单选插件

```html
<div style="padding: 100px 100px 10px;">
    <form class="bs-example bs-example-form" role="form">
        <div class="row">
            <div class="col-lg-6">
                <div class="input-group">
                    <span class="input-group-addon">
                        <input type="checkbox"></span>
                    <input type="text" class="form-control">
                </div><!-- /input-group -->
            </div><!-- /.col-lg-6 -->
            <br>
            <div class="col-lg-6">
                <div class="input-group">
                    <span class="input-group-addon">
                        <input type="radio"></span>
                    <input type="text" class="form-control">
                </div><!-- /input-group -->
            </div><!-- /.col-lg-6 -->
        </div><!-- /.row -->
    </form>
</div>
```

### 按钮插件

```html
<div class="form-group">
    <label class="col-sm-2 control-label">请输入关键字</label>
    <div class="col-sm-10">
        <div class="input-group">
            <input type="text" class="form-control">
            <span class="input-group-btn">
                <button class="btn btn-default" type="button">Go!</button>
            </span>
        </div>
    </div>
</div>
```

### 带下拉菜单的按钮

```html
<div class="form-group">
    <label class="col-sm-2 control-label">请输入关键字</label>
    <div class="col-sm-10">
        <div class="input-group">
            <input type="text" class="form-control">
            <span class="input-group-btn">
                <button type="button" class="btn btn-default  dropdown-toggle" data-toggle="dropdown">
                    下拉菜单 <span class="caret"></span>
                </button>
                <ul class="dropdown-menu pull-right">
                    <li>
                        <a href="#">功能</a>
                    </li>
                    <li>
                        <a href="#">另一个功能</a>
                    </li>
                    <li>
                        <a href="#">其他</a>
                    </li>
                    <li class="divider"></li>
                    <li>
                        <a href="#">分离的链接</a>
                    </li>
                </ul>
            </span>
        </div>
    </div>
</div>
```

## Bootstrap导航栏

### 基础导航栏

创建一个标签式的导航菜单：

- 以一个带有 class **.nav** 的无序列表开始。
- 添加 class **.nav-tabs**。

```html
<div class="container" style="border: 1px solid red;">
    <ul class="nav nav-tabs" id="u1">
        <li class="active"><a href="#">Home</a></li>
        <li><a href="#">SVN</a></li>
        <li><a href="#">iOS</a></li>
        <li><a href="#">VB.Net</a></li>
        <li><a href="#">Java</a></li>
        <li><a href="#">PHP</a></li>
    </ul>
</div>
```

### 胶囊式导航菜单

如果需要把标签改成胶囊的样式，只需要使用 class **.nav-pills** 代替 **.nav-tabs** 即可，其他的步骤与上面相同。

```html
<div class="container" style="border: 1px solid red;">
    <ul class="nav nav-pills" id="u2">
        <li class="active"><a href="#">Home</a></li>
        <li><a href="#">SVN</a></li>
        <li><a href="#">iOS</a></li>
        <li><a href="#">VB.Net</a></li>
        <li><a href="#">Java</a></li>
        <li><a href="#">PHP</a></li>
    </ul>
</div>
```

### 垂直胶囊式导航菜单

您可以在使用 class **.nav、.nav-pills** 的同时使用 class **.nav-stacked**，让胶囊垂直堆叠。

```html
<div class="container" style="border: 1px solid red;">
    <ul class="nav nav-pills nav-stacked" id="u3">
        <li class="active"><a href="#">Home</a></li>
        <li><a href="#">SVN</a></li>
        <li><a href="#">iOS</a></li>
        <li><a href="#">VB.Net</a></li>
        <li><a href="#">Java</a></li>
        <li><a href="#">PHP</a></li>
    </ul>
</div>
```

### 禁用链接

对每个 **.nav** class，如果添加了 **.disabled** class，则会创建一个灰色的链接，同时禁用了该链接的 **:hover** 状态；

```html
<ul class="nav nav-pills">
    <li class="active"><a href="#">Home</a></li>
    <li><a href="#">SVN</a></li>
    <li class="disabled"><a href="#">iOS（禁用链接）</a></li>
    <li><a href="#">VB.Net</a></li>
    <li><a href="#">Java</a></li>
    <li><a href="#">PHP</a></li>
</ul>
```

### 带下拉菜单的导航

```html
<div class="container" style="border: 1px solid red;">
    <ul class="nav nav-tabs">
        <li class="active"><a href="#">Home</a></li>
        <li><a href="#">SVN</a></li>
        <li><a href="#">iOS</a></li>
        <li><a href="#">VB.Net</a></li>
        <li class="dropdown">
            <a class="dropdown-toggle" data-toggle="dropdown" href="#">
                Java <span class="caret"></span>
            </a>
            <ul class="dropdown-menu">
                <li><a href="#">Swing</a></li>
                <li><a href="#">jMeter</a></li>
                <li><a href="#">EJB</a></li>
                <li class="divider"></li>
                <li><a href="#">分离的链接</a></li>
            </ul>
        </li>
        <li><a href="#">PHP</a></li>
    </ul>
</div>
```

### 导航栏中的表单

导航栏中的表单不是使用 [Bootstrap 表单](https://www.runoob.com/bootstrap/bootstrap-forms.html) 章节中所讲到的默认的 class，它是使用 **.navbar-form** class。这确保了表单适当的垂直对齐和在较窄的视口中折叠的行为。使用对齐方式选项（这将在组件对齐方式部分进行详细讲解）来决定导航栏中的内容放置在哪里。

```html
<div class="container" style="border: 1px solid red;">
    <nav class="navbar navbar-default" role="navigation">
        <div class="container-fluid"> 
            <div class="navbar-header">
                <a class="navbar-brand" href="#">菜鸟教程</a>
            </div>
            <form class="navbar-form navbar-left" role="search">
                <div class="form-group">
                    <input type="text" class="form-control" placeholder="Search">
                </div>
                <button type="submit" class="btn btn-default">提交</button>
            </form>
        </div>
    </nav>
</div>
```

### 导航栏中的文本

如果需要在导航中包含文本字符串，请使用 class **.navbar-text**。这通常与 <p> 标签一起使用，确保适当的前导和颜色。

```html
<div class="container" style="border: 1px solid red;">
    <nav class="navbar navbar-default" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" href="#">菜鸟教程</a>
            </div>
            <div>
                <p class="navbar-text">Runoob 用户登录</p>
            </div>
        </div>
    </nav>
</div>
```

### 结合图标的导航链接

如果您想在常规的导航栏导航组件内使用图标，那么请使用 class **glyphicon glyphicon-\*** 来设置图标.

```html
<div class="container" style="border: 1px solid red;">
    <nav class="navbar navbar-default" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" href="#">菜鸟教程</a>
            </div>
            <ul class="nav navbar-nav navbar-right">
                <li><a href="#"><span class="glyphicon glyphicon-user"></span> 注册</a></li>
                <li><a href="#"><span class="glyphicon glyphicon-log-in"></span> 登录</a></li>
            </ul>
        </div>
    </nav>
</div>
```

### 固定到顶部

Bootstrap 导航栏可以动态定位。默认情况下，它是块级元素，它是基于在 HTML 中放置的位置定位的。通过一些帮助器类，您可以把它放置在页面的顶部或者底部，或者您可以让它成为随着页面一起滚动的静态导航栏。

如果您想要让导航栏固定在页面的顶部，请向 **.navbar class** 添加 class **.navbar-fixed-top**。

```html
<div class="container" style="border: 1px solid red;">
    <nav class="navbar navbar-default navbar-fixed-top" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" href="#">菜鸟教程</a>
            </div>
            <div>
                <ul class="nav navbar-nav" id="u4">
                    <li class="active"><a href="#">iOS</a></li>
                    <li><a href="#">SVN</a></li>
                    <li class="dropdown">
                        <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                            Java <b class="caret"></b>
                        </a>
                        <ul class="dropdown-menu">
                            <li><a href="#">jmeter</a></li>
                            <li><a href="#">EJB</a></li>
                            <li><a href="#">Jasper Report</a></li>
                            <li class="divider"></li>
                            <li><a href="#">分离的链接</a></li>
                            <li class="divider"></li>
                            <li><a href="#">另一个分离的链接</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</div>
```

### 固定到底部

如果您想要让导航栏固定在页面的底部，请向 **.navbar class** 添加 class **.navbar-fixed-bottom**。

```html
<div class="container" style="border: 1px solid red;">
    <nav class="navbar navbar-default navbar-fixed-bottom" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" href="#">菜鸟教程</a>
            </div>
            <div>
                <ul class="nav navbar-nav" id="u5">
                    <li class="active"><a href="#">iOS</a></li>
                    <li><a href="#">SVN</a></li>
                    <li class="dropdown">
                        <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                            Java <b class="caret"></b>
                        </a>
                        <ul class="dropdown-menu">
                            <li><a href="#">jmeter</a></li>
                            <li><a href="#">EJB</a></li>
                            <li><a href="#">Jasper Report</a></li>
                            <li class="divider"></li>
                            <li><a href="#">分离的链接</a></li>
                            <li class="divider"></li>
                            <li><a href="#">另一个分离的链接</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</div>
```

### 静态顶部

如需创建能随着页面一起滚动的导航栏，请添加 **.navbar-static-top** class。该 class 不要求向 <body> 添加内边距（padding）。

```html
<nav class="navbar navbar-default navbar-static-top" role="navigation">
    <div class="container-fluid">
        <div class="navbar-header">
            <a class="navbar-brand" href="#">静态顶部</a>
        </div>
        <div>
            <ul class="nav navbar-nav">
                <li class="active"><a href="#">iOS</a></li>
                <li><a href="#">SVN</a></li>
                <li class="dropdown">
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown">
                        Java <b class="caret"></b>
                    </a>
                    <ul class="dropdown-menu">
                        <li><a href="#">jmeter</a></li>
                        <li><a href="#">EJB</a></li>
                        <li><a href="#">Jasper Report</a></li>
                        <li class="divider"></li>
                        <li><a href="#">分离的链接</a></li>
                        <li class="divider"></li>
                        <li><a href="#">另一个分离的链接</a></li>
                    </ul>
                </li>
            </ul>
        </div>
    </div>
</nav>
```

## Bootstrap分页

分页（Pagination），是一种无序列表，Bootstrap 像处理其他界面元素一样处理分页。

### 分页（Pagination）

下表列出了 Bootstrap 提供的处理分页的 class。

| Class                          | 描述                                                         | 示例代码                                                     |
| :----------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| .pagination                    | 添加该 class 来在页面上显示分页。                            | `<ul class="pagination">  <li><a href="#">«</a></li>  <li><a href="#">1</a></li>  ....... </ul>` |
| .disabled, .active             | 您可以自定义链接，通过使用 **.disabled** 来定义不可点击的链接，通过使用 **.active** 来指示当前的页面。 | `<ul class="pagination">  <li class="disabled"><a href="#">«</a></li>  <li class="active"><a href="#">1<span class="sr-only">(current)</span></a></li>  ....... </ul>` |
| .pagination-lg, .pagination-sm | 使用这些 class 来获取不同大小的项。                          | `<ul class="pagination pagination-lg">...</ul> <ul class="pagination">...</ul> <ul class="pagination pagination-sm">...</ul>` |

```html
<ul class="pagination">
    <li><a href="#">&laquo;</a></li>
    <li><a href="#">1</a></li>
    <li><a href="#">2</a></li>
    <li><a href="#">3</a></li>
    <li><a href="#">4</a></li>
    <li><a href="#">5</a></li>
    <li><a href="#">&raquo;</a></li>
</ul>
```

### 翻页

如果您想要创建一个简单的分页链接为用户提供导航，可通过翻页来实现。与分页链接一样，翻页也是无序列表。默认情况下，链接是居中显示。下表列出了 Bootstrap 处理翻页的 class。

| Class            | 描述                                                         | 示例代码                                                     |
| :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| .pager           | 添加该 class 来获得翻页链接。                                | `<ul class="pager">  <li><a href="#">Previous</a></li>  <li><a href="#">Next</a></li> </ul>` |
| .previous, .next | 使用 class **.previous** 把链接向左对齐，使用 **.next** 把链接向右对齐。 | `<ul class="pager">  <li class="previous"><a href="#">← Older</a></li>  <li class="next"><a href="#">Newer →</a></li> </ul>` |
| .disabled        | 添加该 class 来设置对应按钮禁止使用。                        | `<ul class="pager">  <li class="previous disabled"><a href="#">← Older</a></li>  <li class="next"><a href="#">Newer →</a></li> </ul>` |

## Bootstrap徽章

徽章与标签相似，主要的区别在于徽章的边角更加圆滑。

徽章（Badges）主要用于突出显示新的或未读的项。如需使用徽章，只需要把 **<span class="badge">** 添加到链接、Bootstrap 导航等这些元素上即可。

### 基本使用

```html
<div class="container" style="border: 1px solid red;">
    <a href="#">Mailbox <span class="badge">50</span></a>
</div>
```

### 结合导航使用

```html
<div class="container" style="border: 1px solid red;">
    <ul class="nav nav-pills" id="u1">
        <li class="active">
            <a href="#">首页
                <span class="badge">42</span>
            </a>
        </li>
        <li>
            <a href="#">简介</a>
        </li>
        <li>
            <a href="#">消息
                <span class="badge">3</span>
            </a>
        </li>
    </ul>
    <br>
    <h4>列表导航中的激活状态</h4>
    <ul class="nav nav-pills nav-stacked" style="max-width: 260px;"  id="u2">
        <li class="active">
            <a href="#">
                <span class="badge pull-right">42</span>首页</a>
        </li>
        <li>
            <a href="#">简介</a>
        </li>
        <li>
            <a href="#">
                <span class="badge pull-right">3</span>消息
            </a>
        </li>
    </ul>
</div>
```

## Bootstrap缩略图

### 基础用法

```html
<div class="container" style="border: 1px solid red;">
    <div class="row">
        <div class="col-sm-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
            </a>
        </div>
        <div class="col-sm-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
            </a>
        </div>
        <div class="col-sm-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
            </a>
        </div>
        <div class="col-sm-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
            </a>
        </div>
    </div>
</div>
```

### 添加一些讲解

```html
<div class="container" style="border: 1px solid red;">
    <div class="row">
        <div class="col-sm-6 col-md-3">
            <div class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
                <div class="caption">
                    <h3>缩略图标签</h3>
                    <p>一些示例文本。一些示例文本。</p>
                    <p>
                        <a href="#" class="btn btn-primary" role="button">
                            按钮
                        </a>
                        <a href="#" class="btn btn-default" role="button">
                            按钮
                        </a>
                    </p>
                </div>
            </div>
        </div>
        <div class="col-sm-6 col-md-3">
            <div class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
                <div class="caption">
                    <h3>缩略图标签</h3>
                    <p>一些示例文本。一些示例文本。</p>
                    <p>
                        <a href="#" class="btn btn-primary" role="button">
                            按钮
                        </a>
                        <a href="#" class="btn btn-default" role="button">
                            按钮
                        </a>
                    </p>
                </div>
            </div>
        </div>
        <div class="col-sm-6 col-md-3">
            <div class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
                <div class="caption">
                    <h3>缩略图标签</h3>
                    <p>一些示例文本。一些示例文本。</p>
                    <p>
                        <a href="#" class="btn btn-primary" role="button">
                            按钮
                        </a>
                        <a href="#" class="btn btn-default" role="button">
                            按钮
                        </a>
                    </p>
                </div>
            </div>
        </div>
        <div class="col-sm-6 col-md-3">
            <div class="thumbnail">
                <img src="./img/2.jpg" alt="通用的占位符缩略图">
                <div class="caption">
                    <h3>缩略图标签</h3>
                    <p>一些示例文本。一些示例文本。</p>
                    <p>
                        <a href="#" class="btn btn-primary" role="button">
                            按钮
                        </a>
                        <a href="#" class="btn btn-default" role="button">
                            按钮
                        </a>
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>
```

## Bootstrap进度条

### 基础进度条

创建一个基本的进度条的步骤如下：

- 添加一个带有 class **.progress** 的 <div>。
- 接着，在上面的 <div> 内，添加一个带有 class **.progress-bar** 的空的 <div>。
- 添加一个带有百分比表示的宽度的 style 属性，例如 style="width: 60%"; 表示进度条在 60% 的位置。

```html
<div class="container" style="border: 1px solid red;">
    <div class="progress">
        <div class="progress-bar" role="progressbar" aria-valuenow="60" 
             aria-valuemin="0" aria-valuemax="100" style="width: 40%;">
            <!-- sr-only：隐藏文本 -->
            <span class="sr-only">40% 完成</span>
        </div>
    </div>
</div>  
```

### 进度条基础样式

```html
<div class="container" style="border: 1px solid red;">
    <div class="progress">
        <div class="progress-bar progress-bar-success" role="progressbar" aria-valuenow="40" aria-valuemin="0"
             aria-valuemax="100" style="width:40%">
            40% Complete (success)
        </div>
    </div>

    <div class="progress">
        <div class="progress-bar progress-bar-info" role="progressbar" aria-valuenow="50" aria-valuemin="0"
             aria-valuemax="100" style="width:50%">
            50% Complete (info)
        </div>
    </div>

    <div class="progress">
        <div class="progress-bar progress-bar-warning" role="progressbar" aria-valuenow="60" aria-valuemin="0"
             aria-valuemax="100" style="width:60%">
            60% Complete (warning)
        </div>
    </div>

    <div class="progress">
        <div class="progress-bar progress-bar-danger" role="progressbar" aria-valuenow="70" aria-valuemin="0"
             aria-valuemax="100" style="width:70%">
            70% Complete (danger)
        </div>
    </div>
</div>
```

### 条纹进度条

创建一个条纹的进度条的步骤如下：

- 添加一个带有 class **.progress** 和 **.progress-striped** 的 <div>。
- 接着，在上面的 <div> 内，添加一个带有 class **.progress-bar** 和 class **progress-bar-\*** 的空的 <div>。其中，* 可以是 **success、info、warning、danger**。
- 添加一个带有百分比表示的宽度的 style 属性，例如 style="60%"; 表示进度条在 60% 的位置。

```html
<div class="container" style="border: 1px solid red;">
    <div class="progress progress-striped">
        <div class="progress-bar progress-bar-success" role="progressbar" aria-valuenow="60" aria-valuemin="0"
             aria-valuemax="100" style="width: 90%;">
            <span>90% 完成（成功）</span>
        </div>
    </div>
</div>
```

### 动态进度条

```html
<div class="progress progress-striped active">
    <div class="progress-bar progress-bar-success" role="progressbar" aria-valuenow="60" aria-valuemin="0"
         aria-valuemax="100" style="width: 40%;">
        <span>40% 完成</span>
    </div>
</div>
```

### 堆叠进度条

```html
<div class="container" style="border: 1px solid red;padding-top: 5px;">
    <div class="progress">
        <div class="progress-bar progress-bar-success" role="progressbar"
             aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
             style="width: 40%;">
            <span >40% 完成</span>
        </div>
        <div class="progress-bar progress-bar-info" role="progressbar"
             aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
             style="width: 30%;">
            <span >30% 完成（信息）</span>
        </div>
        <div class="progress-bar progress-bar-warning" role="progressbar"
             aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
             style="width: 30%;">
            <span >30% 完成（警告）</span>
        </div>
    </div>
</div>
```

## Bootstrap多媒体对象

 Bootstrap 中的多媒体对象（Media Object）包含：图像、视频、音频等。 多媒体对象的样式可用于创建各种类型的组件（比如：博客评论），我们可以在组件中使用图文混排，图像可以左对齐或者右对齐。媒体对象可以用更少的代码来实现媒体对象与文字的混排。

### 基本使用

```html
<div class="container" style="border: 1px solid red;">
    <!-- 左对齐 -->
    <div class="media">
        <div class="media-left">
            <img src="./img/2.jpg" class="media-object" style="width:60px">
        </div>
        <div class="media-body">
            <h4 class="media-heading">左对齐</h4>
            <p>这是一些示例文本...</p>
        </div>
    </div>

    <!-- 右对齐 -->
    <div class="media">
        <div class="media-body">
            <h4 class="media-heading">左对齐</h4>
            <p>这是一些示例文本...</p>
        </div>
        <div class="media-right">
            <img src="./img/2.jpg" class="media-object" style="width:60px">
        </div>
    </div>
</div>
```

### 置顶、居中、底部

```html
<div class="container" style="border: 1px solid red;">
    <!-- 置顶 -->
    <div class="media">
        <div class="media-left media-top">
            <img src="./img/2.jpg" class="media-object" style="width:60px">
        </div>
        <div class="media-body">
            <h4 class="media-heading">置顶</h4>
            <p>这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...</p>
        </div>
    </div>

    <!-- 居中对齐 -->
    <div class="media">
        <div class="media-left media-middle">
            <img src="./img/2.jpg" class="media-object" style="width:60px">
        </div>
        <div class="media-body">
            <h4 class="media-heading">居中</h4>
            <p>这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...</p>
        </div>
    </div>

    <!-- 置底 -->
    <div class="media">
        <div class="media-left media-bottom">
            <img src="./img/2.jpg" class="media-object" style="width:60px">
        </div>
        <div class="media-body">
            <h4 class="media-heading">置底</h4>
            <p>这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...这是一些示例文本...</p>
        </div>
    </div>
</div>
```

## Bootstrap列表组

列表组件用于以列表形式呈现复杂的和自定义的内容。创建一个基本的列表组的步骤如下：

- 向元素 <ul> 添加 class **.list-group**。
- 向 <li> 添加 class **.list-group-item**。

### 基础演示

```html
<div class="container" style="border: 1px solid red;padding-top: 5px;">
    <ul class="list-group">
        <li class="list-group-item">免费域名注册</li>
        <li class="list-group-item">免费 Window 空间托管</li>
        <li class="list-group-item">图像的数量</li>
        <li class="list-group-item">24*7 支持</li>
        <li class="list-group-item">每年更新成本</li>
    </ul>
</div>
```

### 添加徽章

```html
<div class="container" style="border: 1px solid red;">
    <ul class="list-group">
        <li class="list-group-item">免费域名注册</li>
        <li class="list-group-item">免费 Window 空间托管</li>
        <li class="list-group-item">图像的数量</li>
        <li class="list-group-item">
            24*7 支持
            <span class="badge">新</span>
        </li>
        <li class="list-group-item">每年更新成本</li>
        <li class="list-group-item">
            <span class="badge">新</span>
            折扣优惠
        </li>
    </ul>
</div>
```

### 添加链接

```html
<div class="container" style="border: 1px solid red;">
    <ul class="list-group" id="u1">
        <a href="#" class="list-group-item active">
            免费域名注册
        </a>
        <a href="#" class="list-group-item">24*7 支持</a>
        <a href="#" class="list-group-item">免费 Window 空间托管</a>
        <a href="#" class="list-group-item">图像的数量</a>
        <a href="#" class="list-group-item">每年更新成本</a>
    </ul>
</div>
```

```js
Array.from($('#u1 a')).forEach(element => {
    element.onclick = function () {
        console.log(element.textContent);
        $('#u1 a.active').removeClass('active');
        element.className += ' active';
    }
});
```

## Bootstrap面板（Panels）

### 基础用法

```html
<div class="container" style="border: 1px solid red;">
    <div class="panel panel-default">
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
</div>
```

### 面板标题

可以通过以下两种方式来添加面板标题：

- 使用 **.panel-heading** class 可以很简单地向面板添加标题容器。
- 使用带有 **.panel-title** class 的 <h1>-<h6> 来添加预定义样式的标题。

```html
<div class="container" style="border: 1px solid red;">
    <div class="panel panel-default">
        <div class="panel-heading">
            不带 title 的面板标题
        </div>
        <div class="panel-body">
            面板内容
        </div>
    </div>

    <div class="panel panel-default">
        <div class="panel-heading">
            <h3 class="panel-title">
                带有 title 的面板标题
            </h3>
        </div>
        <div class="panel-body">
            面板内容
        </div>
    </div>
</div>
```

### 面板脚注

```html
<div class="container" style="border: 1px solid red;">
    <div class="panel-heading">
        <h3 class="panel-title">
            带有 title 的面板标题
        </h3>
    </div>
    <div class="panel panel-default">
        <div class="panel-body">
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
            这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板这是一个基本的面板
        </div>
        <div class="panel-footer">面板脚注</div>
    </div>
</div>
```

### 带语境色彩的面板

使用语境状态类 **panel-primary、panel-success、panel-info、panel-warning、panel-danger**，来设置带语境色彩的面板，实例如下：

```html
<div class="container" style="border: 1px solid red;">
    <div class="panel panel-primary">
        <div class="panel-heading">
            <h3 class="panel-title">面板标题</h3>
        </div>
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
    <div class="panel panel-success">
        <div class="panel-heading">
            <h3 class="panel-title">面板标题</h3>
        </div>
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
    <div class="panel panel-info">
        <div class="panel-heading">
            <h3 class="panel-title">面板标题</h3>
        </div>
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
    <div class="panel panel-warning">
        <div class="panel-heading">
            <h3 class="panel-title">面板标题</h3>
        </div>
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
    <div class="panel panel-danger">
        <div class="panel-heading">
            <h3 class="panel-title">面板标题</h3>
        </div>
        <div class="panel-body">
            这是一个基本的面板
        </div>
    </div>
</div>
```

# Bootstrap插件

所有的插件依赖于 jQuery。所以必须在插件文件之前引用 jQuery。

## 模态框(Modal)插件

模态框（Modal）是覆盖在父窗体上的子窗体。通常，目的是显示来自一个单独的源的内容，可以在不离开父窗体的情况下有一些互动。子窗体可提供信息、交互等。

### 基础使用

```html
<div class="container" style="border: 1px solid red;">
    <h2>创建模态框（Modal）</h2>
    <!-- 按钮触发模态框 -->
    <button class="btn btn-primary btn-lg" data-toggle="modal" data-target="#myModal">
        开始演示模态框
    </button>
    <!-- 模态框（Modal） -->
    <div class="modal fade" id="myModal" data-keyboard="false" tabindex="-1" role="dialog" aria-labelledby="myModalLabel"
         aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                        &times;
                    </button>
                    <h4 class="modal-title" id="myModalLabel">
                        模态框（Modal）标题
                    </h4>
                </div>
                <div class="modal-body">
                    在这里添加一些文本
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-default" data-dismiss="modal">关闭
                    </button>
                    <button type="button" class="btn btn-primary">
                        提交更改
                    </button>
                </div>
            </div><!-- /.modal-content -->
        </div><!-- /.modal -->
    </div>
</div>
```

### 选项

有一些选项可以用来定制模态窗口（Modal Window）的外观和感观，它们是通过 data 属性或 JavaScript 来传递的。下表列出了这些选项：

| 选项名称 | 类型/默认值                               | Data 属性名称 | 描述                                                         |
| :------- | :---------------------------------------- | :------------ | :----------------------------------------------------------- |
| backdrop | boolean 或 string 'static' *默认值：true* | data-backdrop | 指定一个静态的背景，当用户点击模态框外部时不会关闭模态框。   |
| keyboard | boolean *默认值：true*                    | data-keyboard | 当按下 escape 键时关闭模态框，设置为 false 时则按键无效。    |
| show     | boolean *默认值：true*                    | data-show     | 当初始化时显示模态框。                                       |
| remote   | path *默认值：false*                      | data-remote   | 使用 jQuery *.load* 方法，为模态框的主体注入内容。如果添加了一个带有有效 URL 的 href，则会加载其中的内容。如下面的实例所示：`<a data-toggle="modal" href="remote.html" data-target="#modal" rel="noopener noreferrer">请点击我</a>` |

### 方法

下面是一些可与 modal() 一起使用的有用的方法。

| 方法                         | 描述                                           | 实例                                          |
| :--------------------------- | :--------------------------------------------- | :-------------------------------------------- |
| **Options:** .modal(options) | 把内容作为模态框激活。接受一个可选的选项对象。 | `$('#identifier').modal({ keyboard: false })` |
| **Toggle:** .modal('toggle') | 手动切换模态框。                               | `$('#identifier').modal('toggle')`            |
| **Show:** .modal('show')     | 手动打开模态框。                               | `$('#identifier').modal('show')`              |
| **Hide:** .modal('hide')     | 手动隐藏模态框。                               | `$('#identifier').modal('hide')`              |

### 事件

下表列出了模态框中要用到事件。这些事件可在函数中当钩子使用。

| 事件            | 描述                                                  | 实例                                                         |
| :-------------- | :---------------------------------------------------- | :----------------------------------------------------------- |
| show.bs.modal   | 在调用 show 方法后触发。                              | `$('#identifier').on('show.bs.modal', function () {  // 执行一些动作... })` |
| shown.bs.modal  | 当模态框对用户可见时触发（将等待 CSS 过渡效果完成）。 | `$('#identifier').on('shown.bs.modal', function () {  // 执行一些动作... })` |
| hide.bs.modal   | 当调用 hide 实例方法时触发。                          | `$('#identifier').on('hide.bs.modal', function () {  // 执行一些动作... })` |
| hidden.bs.modal | 当模态框完全对用户隐藏时触发。                        | `$('#identifier').on('hidden.bs.modal', function () {  // 执行一些动作... })` |

> 示例

```js
$(function() {
    $('#myModal').on('hide.bs.modal',
    function() {
        alert('嘿，我听说您喜欢模态框...');
    })
});
```

## 滚动监听（Scrollspy）插件

### 用法

您可以向顶部导航添加滚动监听行为：

- 通过 data 属性：向您想要监听的元素（通常是 body）添加<code>data-spy="scroll"</code>。然后添加带有 Bootstrap.nav组件的父元素的 ID 或 class 的属性data-target。为了它能正常工作，您必须确保页面主体中有匹配您所要监听链接的 ID 的元素存在。

  ```html
  <body data-spy="scroll" data-target=".navbar-example">
  ...
  <div class="navbar-example">
      <ul class="nav nav-tabs">
          ...
      </ul>
  </div>
  ...
  </body>
  ```

- 通过 JavaScript：您可以通过 JavaScript 调用滚动监听，选取要监听的元素，然后调用<code>.scrollspy()</code>函数：

  ```js
  $('body').scrollspy({ target: '.navbar-example' })
  ```

### 基础示例

```html
<div class="container">
    <nav id="navbar-example" class="navbar navbar-default navbar-static" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" href="#">教程名称</a>
            </div>
            <div class="collapse navbar-collapse bs-js-navbar-scrollspy">
                <ul class="nav navbar-nav">
                    <li><a href="#ios">iOS</a></li>
                    <li><a href="#svn">SVN</a></li>
                    <li class="dropdown">
                        <a href="#" id="navbarDrop1" class="dropdown-toggle" data-toggle="dropdown">Java
                            <b class="caret"></b>
                        </a>
                        <ul class="dropdown-menu" role="menu" aria-labelledby="navbarDrop1">
                            <li><a href="#jmeter" tabindex="-1">jmeter</a></li>
                            <li><a href="#ejb" tabindex="-1">ejb</a></li>
                            <li class="divider"></li>
                            <li><a href="#spring" tabindex="-1">spring</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <div data-spy="scroll" data-target="#navbar-example" data-offset="0"
         style="height:200px;overflow:auto; position: relative;">
        <h4 id="ios">iOS</h4>
        <p>iOS 是一个由苹果公司开发和发布的手机操作系统。最初是于 2007 年首次发布 iPhone、iPod Touch 和 Apple
            TV。iOS 派生自 OS X，它们共享 Darwin 基础。OS X 操作系统是用在苹果电脑上，iOS 是苹果的移动版本。
        </p>
        <h4 id="svn">SVN</h4>
        <p>Apache Subversion，通常缩写为 SVN，是一款开源的版本控制系统软件。Subversion 由 CollabNet 公司在 2000 年创建。但是现在它已经发展为 Apache Software
            Foundation 的一个项目，因此拥有丰富的开发人员和用户社区。
        </p>
        <h4 id="jmeter">jMeter</h4>
        <p>jMeter 是一款开源的测试软件。它是 100% 纯 Java 应用程序，用于负载和性能测试。
        </p>
        <h4 id="ejb">EJB</h4>
        <p>Enterprise Java Beans（EJB）是一个创建高度可扩展性和强大企业级应用程序的开发架构，部署在兼容应用程序服务器（比如 JBOSS、Web Logic 等）的 J2EE 上。
        </p>
        <h4 id="spring">Spring</h4>
        <p>Spring 框架是一个开源的 Java 平台，为快速开发功能强大的 Java 应用程序提供了完备的基础设施支持。
        </p>
        <p>Spring 框架最初是由 Rod Johnson 编写的，在 2003 年 6 月首次发布于 Apache 2.0 许可证下。
        </p>
    </div>
</div>
```

### 刷新方法

> 当DOM中元素发生变化时，需要调用刷新方法来更新DOM。

```html
<div class="container" style="border: 1px solid red;">
    <nav id="myScrollspy" class="navbar navbar-default navbar-static" role="navigation">
        <div class="container-fluid">
            <div class="navbar-header">
                <button class="navbar-toggle" type="button" data-toggle="collapse"
                        data-target=".bs-js-navbar-scrollspy">
                    <span class="sr-only">切换导航</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a class="navbar-brand" href="#">教程名称</a>
            </div>
            <div class="collapse navbar-collapse bs-js-navbar-scrollspy">
                <ul class="nav navbar-nav">
                    <li class="active"><a href="#ios">iOS</a></li>
                    <li><a href="#svn">SVN</a></li>
                    <li class="dropdown">
                        <a href="#" id="navbarDrop1" class="dropdown-toggle" data-toggle="dropdown">Java
                            <b class="caret"></b>
                        </a>
                        <ul class="dropdown-menu" role="menu" aria-labelledby="navbarDrop1">
                            <li><a href="#jmeter" tabindex="-1">jmeter</a></li>
                            <li><a href="#ejb" tabindex="-1">ejb</a></li>
                            <li class="divider"></li>
                            <li><a href="#spring" tabindex="-1">spring</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <div data-spy="scroll" data-target="#myScrollspy" data-offset="0"
         style="height:200px;overflow:auto; position: relative;">
        <div class="section">
            <h4 id="ios">iOS<small><a href="#" onclick="removeSection(this);">
                &times; 删除该部分</a></small>
            </h4>
            <p>iOS 是一个由苹果公司开发和发布的手机操作系统。最初是于 2007 年首次发布 iPhone、iPod Touch 和 Apple
                TV。iOS 派生自 OS X，它们共享 Darwin 基础。OS X 操作系统是用在苹果电脑上，iOS 是苹果的移动版本。</p>
        </div>
        <div class="section">
            <h4 id="svn">SVN<small></small></h4>
            <p>Apache Subversion，通常缩写为 SVN，是一款开源的版本控制系统软件。Subversion 由 CollabNet 公司在 2000 年创建。但是现在它已经发展为 Apache
                Software Foundation 的一个项目，因此拥有丰富的开发人员和用户社区。</p>
        </div>
        <div class="section">
            <h4 id="jmeter">jMeter<small><a href="#" onclick="removeSection(this);">
                &times; 删除该部分</a></small>
            </h4>
            <p>jMeter 是一款开源的测试软件。它是 100% 纯 Java 应用程序，用于负载和性能测试。</p>
        </div>
        <div class="section">
            <h4 id="ejb">EJB</h4>
            <p>Enterprise Java Beans（EJB）是一个创建高度可扩展性和强大企业级应用程序的开发架构，部署在兼容应用程序服务器（比如 JBOSS、Web Logic 等）的 J2EE 上。</p>
        </div>
        <div class="section">
            <h4 id="spring">Spring</h4>
            <p>Spring 框架是一个开源的 Java 平台，为快速开发功能强大的 Java 应用程序提供了完备的基础设施支持。</p>
            <p>Spring 框架最初是由 Rod Johnson 编写的，在 2003 年 6 月首次发布于 Apache 2.0 许可证下。</p>
        </div>
    </div>
    <script>
        $(function () {
            removeSection = function (e) {
                $(e).parents(".section").remove();
                $('[data-spy="scroll"]').each(function () {
                    var $spy = $(this).scrollspy('refresh')
                    });
            }
            $("#myScrollspy").scrollspy();
        });
    </script>
</div>
```

