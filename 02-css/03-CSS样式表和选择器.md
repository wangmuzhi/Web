## 本文主要内容

- CSS概述
- CSS和HTML结合的三种方式：`行内样式表`、`内嵌样式表`、`外部样式表`
- CSS四种基本选择器：`标签选择器`、`类选择器`、`ID选择器`、`通用选择器`
- CSS几种扩展选择器：`后代选择器`、`交集选择器`、`并集选择器`
- CSS样式优先级



## 前言

现在的互联网前端分三层：

- HTML：超文本标记语言。从**语义**的角度描述页面**结构**。
- CSS：层叠样式表。从**审美**的角度负责页面**样式**。

## CSS 概述

CSS：Cascading Style Sheet，层叠样式表。CSS的作用就是给HTML页面标签添加各种样式，**定义网页的显示效果**。简单一句话：CSS将网页**内容和显示样式进行分离**，提高了显示功能。

css的最新版本是css3，**我们目前学习的是css2.1**。 因为css3和css2.1不矛盾，必须先学2.1然后学3。

接下来我们要讲一下为什么要使用CSS。

**HTML的缺陷：**

1. 不能够适应多种设备
2. 要求浏览器必须智能化足够庞大
3. 数据和显示没有分开
4. 功能不够强大

**CSS 优点：**

1. 使数据和显示分开
2. 降低网络流量
3. 使整个网站视觉效果一致
4. 使开发效率提高了（耦合性降低，一个人负责写html，一个人负责写css）

比如说，有一个样式需要在一百个页面上显示，如果是html来实现，那要写一百遍，现在有了css，只要写一遍。现在，html只提供数据和一些控件，完全交给css提供各种各样的样式。

### CSS的重点知识点

盒子模型、浮动、定位

### CSS 整体感知

我们先来看一段简单的css代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        p{
            color:red;
            font-size: 30px;
            text-decoration: underline;
            font-weight: bold;
            text-align: center;
            font-style: italic;
        }
        h1{
            color:blue;
            font-size: 50px;
            font-weight: bold;
            background-color: pink;
        }

    </style>
</head>
<body>
    <h1>我是大标题</h1>
    <p>
        我是内容
    </p>

</body>
</html>
```

解释如下：

![](http://img.smyhvae.com/20170710_1605.png)

我们写css的地方是style标签，就是“样式”的意思，写在head里面。后面的课程中我们将知道，css也可以写在单独的文件里面，现在我们先写在style标签里面。

如果在sublime中输入`<st`或者`<style`然后按tab键，可以自动生成的格式如下：（建议）

```html
    <style type="text/css"></style>
```

type表示“类型”，text就是“纯文本”，css也是纯文本。

但是，如果在sublime中输入`st`或者`style`然后按tab键，可以自动生成的格式如下：（不建议）

```html
    <style></style>
```

css对换行不敏感，对空格也不敏感。但是一定要有标准的语法。冒号，分号都不能省略。



## CSS语法

**语法格式：**（其实就是键值对）

```html
选择器{
    属性名: 属性值;
    属性名: 属性值;
}
```

或者可以写成：

```css
选择器{
    k:v;
    k:v;
    k:v;
    k:v;
}
选择器{
    k:v;
    k:v;
    k:v;
    k:v;
}
```

**解释：**

- 选择器代表页面上的某类元素，选择器后一定是大括号。
- 属性名后必须用冒号隔开，属性值后用分号（最后一个属性可以不用分号）。
- 属性名和冒号之间最好不要有空格（经验）。
- 如果一个属性有多个值的话，那么多个值用 空格 隔开

**举例：**

```css
p{color: red;}
```

**完整版代码举例：**

```html
<style type="text/css">
    p{
        font-weight: bold;
        font-style: italic;
        color: red;
    }

</style>

 <body>
    <p>洗白白</p>
    <p>你懂得</p>
    <p>我不会就这样轻易的狗带</p>
 </body>
```

效果：

![](http://img.smyhvae.com/2015-10-03-css-01.png)

### css代码的注释

**格式：**

```html
<style type="text/css">

    /*
        具体的注释
    */

    p{
        font-weight: bold;
        font-style: italic;
        color: red;
    }

</style>
```

注意：CSS只有`/*  */`这种注释，没有`//`这种注释。而且注释要写在`<style>`标签里面才算生效哦。

接下来，我们要开始真正地讲css的知识咯。

css怎么学？CSS有两个知识部分：
1） 选择器，怎么选；
2） 属性，样式是什么



## CSS的一些简单常见的属性

> 我们先来接触CSS的一些简单常见的属性，因为接下来需要用到。后期会专门用一篇文章来写CSS的属性。

以下属性值中，括号中的内容表示sublime中的快捷键。

**字体颜色：**（c）

```html
color:red;
```

color属性的值，可以是英语单词，比如red、blue、yellow等等；也可以是rgb、十六进制(后期详细讲)。

**字号大小：**（fos）

```html
font-size:40px;
```

font就是“字体”，size就是“尺寸”。px是“像素”。单位必须加，不加不行。

**背景颜色：**（bgc）

```html
background-color: blue;
```

background就是“背景”。

**加粗：**（fwb）

```html
font-weight: bold;
```

font是“字体” weight是“重量”的意思，bold粗。

**不加粗：**（fwn）

```html
font-weight: normal;

```

normal就是正常的意思。

**斜体：**（fsi）

```html
font-style: italic;
```

italic就是“斜体”。

**不斜体：**（fsn）

```html
font-style: normal;
```

**下划线：**（tdu）

```html
text-decoration: underline;
```

decoration就是“装饰”的意思。

**没有下划线：**（tdn）

```html
text-decoration:none;
```

PS：css没啥难的，就是要把属性给记忆准确。

## CSS和HTML结合的方式（样式表）

CSS和HTML结合的方式，其实就是问你css的代码放在哪里比较合适。CSS代码理论上的位置是任意的，**但通常写在`<style>`标签里**。只要是`<style>`标签里的代码，那就是css代码，浏览器就是这样来进行解析的。

CSS和HTML的结合方式有3种：

- **行内样式**：在某个特定的标签里采用style**属性**。范围只针对此标签。
- **内嵌样式表**：在页面的head里采用`<style>`**标签**。范围针对此页面。
- **引入外部样式表css文件**的方式。这种方式又分为两种：
  - 1、采用`<link>`标签。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`
  - 2、采用import，必须写在`<style>`标签中，并且必须是第一句。例如：`@import url(a.css) ;`

> 两种引入样式方式的区别：外部样式表中不能写<link>标签,但是可以写import语句。

下面来详细的讲一讲这三种方式。

### 1、CSS和HTML结合方式一：行内样式

采用style属性。范围只针对此标签适用。

该方式比较灵活，但是对于多个相同标签的同一样式定义比较麻烦，适合局部修改。

举例：

```html
<p style="color:white;background-color:red">我不会就这样轻易的狗带</p>
```

效果：

![](http://img.smyhvae.com/2015-10-03-css-02.png)

### 2、CSS和HTML结合方式二：内嵌样式表

在head标签中加入`<style>`标签，对多个标签进行统一修改，范围针对此页面。

该方式可以对单个页面的样式进行统一设置，但对于局部不够灵活。

举例：

```html
<style type="text/css">
    p{
        font-weight: bold;
        font-style: italic;
        color: red;
    }

</style>



 <body>
    <p>洗白白</p>
    <p style="color:blue">你懂得</p>
 </body>
```

![](http://img.smyhvae.com/2015-10-03-css-03.png)

### 3、CSS和HTML结合方式三：引入外部样式表css文件

**引入样式表文件**的方式又分为两种：

- （1）**采用`<link>`标签**。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`
- （2）**采用import**，必须写在`<style>`标签中，并且必须是第一句。例如：`@import url(a.css) ;`

> 两种引入样式方式的区别：外部样式表中不能写<link>标签，但是可以写import语句。

**具体操作如下：**
我们先在html页面的同级目录下新建一个`a.css`文件，那说明这里面的代码全是css代码，此时就没有必要再写`<style>`标签这几个字了。
`a.css`的代码如下：

```css
p{
    border: 1px solid red;
    font-size: 40px;
}
```

上方的css代码中，注意像素要带上px这个单位，不然不生效。
然后我们在html文件中通过`<link>`标签引入这个css文件就行了。效果如下：

![](http://img.smyhvae.com/2015-10-03-css-04.png)

这里再讲一个补充的知识：link标签的rel属性
**`<link>`标签的rel属性：**
其属性值有以下两种：

- `stylesheet`：定义的样式表
- `alternate stylesheet`：候选的样式表

看字面意思可能比较难理解，我们来举个例子，一下子就明白了。
举例：

现在定义我们来定义3种样式表：
a.css：定义一个实线的黑色边框

```css
div{
    width: 200px;
    height: 200px;
    border: 3px solid black;
}
```

ba.css：蓝色的虚线边框

```css
div{
    width: 200px;
    height: 200px;
    border: 3px dotted blue;
}
```

c.css：来个背景图片

```css
div{
    width: 200px;
    height: 200px;
    border: 3px solid red;
    background-image: url("1.jpg");
}
```

然后我们在html文件中引用三个样式表：

```html
  <link rel = "stylesheet" type = "text/css" href = "a.css"></link>
  <link rel = "alternate stylesheet" type = "text/css" href = "b.css" title="第二种样式"></link>
  <link rel = "alternate stylesheet" type = "text/css" href = "c.css" title="第三种样式"></link>
```

上面引入的三个样式表中，后面两个样式表作为备选。注意备选的样式表中，title属性不要忘记写，不然显示不出来效果的。现在来看一下效果：（在IE中打开网页）

![](http://img.smyhvae.com/2015-10-03-css-05.gif)