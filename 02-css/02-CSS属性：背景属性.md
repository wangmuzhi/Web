## background系列属性
<!-- MarkdownTOC -->

- 常见背景属性
- background-color：背景颜色的表示方法
- `background-repeat`属性（重要）
- `background-position`属性
- background-attachment属性
- background 综合属性
- 3、定义列表``
- 表格标签
- ``：行

<!-- /MarkdownTOC -->

### 常见背景属性

CSS样式中，常见的背景属性有以下几种：（经常用到，要记住）

- `background-color:#ff99ff;`  设置元素的背景颜色。

- `background-image:url(images/2.gif);` 将图像设置为背景。

-  `background-repeat: no-repeat;`  设置背景图片是否重复及如何重复，默认平铺满。（重要）
    - `no-repeat`不要平铺；
    - `repeat-x`横向平铺；
    - `repeat-y`纵向平铺。

- `background-position:center top;` 设置背景图片在当前容器中的位置。

- `background-attachment:scroll;` 设置背景图片是否跟着滚动条一起移动。
属性值可以是：`scroll`（背景图片不动）、`fixed`（背景图片跟着滚动条一起移动）。注意属性值的含义不要搞反了，它的含义是根据滚动条来定义的。

- 另外还有一个简写属性叫做`background`，它的作用是：将上面的多个属性写在一个声明中。

上面这几个属性经常用到，需要记住。现在我们逐个进行讲解。


### background-color：背景颜色的表示方法

css2.1中，背景颜色的表示方法有三种：单词、rgb表示法、十六进制表示法。

比如红色可以有下面的三种表示方法：

```
    background-color: red;
    background-color: rgb(255,0,0);
    background-color: #ff0000;
```

下面分别介绍。

**1、用英语单词来表示：**

能够用英语单词来表述的颜色，都是简单颜色。比如红色：

```
background-color: red;
```

**2、rgb表示法：**

rgb表示三原色“红”red、“绿”green、“蓝”blue。

光学显示器中，每个像素都是由三原色的发光原件组成的，靠明亮度不同调成不同的颜色的。r、g、b的值，每个值的取值范围0~255，一共256个值。

比如红色：

```
background-color: rgb(255,0,0);
```

黑色：

```
background-color: rgb(0,0,0);
```

颜色可以叠加，比如黄色就是红色和绿色的叠加：

```
background-color: rgb(255,255,0);
```

**3、十六进制表示法：**

比如红色：

```
background-color: #ff0000;
```

PS:所有用#开头的值，都是16进制的。

这里，我们就要学会16进制与10进制之间的转换。下面举几个例子。

问：16进制中28等于10进制多少？
答：2*16+8 = 40。

16进制中的af等于10进制多少？
答：10 * 16 + 15 = 175

所以，#ff0000就等于rgb(255,0,0)。

`background-color: #123456;`等价于`background-color: rgb(18,52,86);`


**十六进制可以简化为3位，所有#aabbcc的形式，能够简化为#abc**。举例如下：

比如：

```
    background-color:#ff0000;
```

等价于：

```
    background-color:#f00;
```

比如：

```
    background-color:#112233;
```

等价于：

```
    background-color:#123;
```

但是，比如下面这个是无法简化的：

```
    background-color:#222333;
```

再比如，下面这个也是无法简化的：

```
    background-color:#123123;
```

几种常见的颜色简写可以记住。如下：

```
    #000   黑
    #fff   白
    #f00   红
    #222   深灰
    #333   灰
    #ccc   浅灰
```


### `background-repeat`属性（重要）

`background-repeat:no-repeat;`设置背景图片是否重复及如何重复，默认平铺满。属性值可以是：

- `no-repeat`（不要平铺）
- `repeat-x`（横向平铺）
- `repeat-y`（纵向平铺）

这个属性在开发的时候也是经常用到的。我们通过设置不同的属性值来看一下效果吧：

（1）不加这个属性时：（即默认时）（背景图片会被平铺满）

![](http://img.smyhvae.com/2015-10-03-css-19.png)

PS：padding的区域也是有背景图的。

（2）属性值为`no-repeat`（不要平铺）时：

![](http://img.smyhvae.com/2015-10-03-css-20.png)

（3）属性值为`repeat-x`（横向平铺）时：

![](http://img.smyhvae.com/2015-10-03-css-21.png)

其实这种属性的作用还是很广的。举个例子，设计师设计一张宽度只有1px、颜色纵向渐变的图片，然后我们通过这个属性将其进行水平方向的平铺，就可以看到整个页面都是渐变的了。

在搜索引擎上搜“**平铺背景**”，就可以发现，**周期性的图片**可以采用此种方法进行平铺。

（4）属性值为`repeat-y`（纵向平铺）时：

![](http://img.smyhvae.com/2015-10-03-css-22.png)


### `background-position`属性

`background-position`属性指的是**背景定位**属性。公式如下：

在描述属性值的时候，有两种方式：用像素描述、用单词描述。下面分别介绍。

**1、用像素值描述属性值：**

格式如下：

```
    background-position:向右偏移量 向下偏移量;
```

属性值可以是正数，也可以是负数。比如：`100px 200px`、`-50px -120px`。

举例如下：

![](http://img.smyhvae.com/20170812_1643.png)


![](http://img.smyhvae.com/20170812_1645.png)

**2、用单词描述属性值：**

格式如下：

```
    background-position: 描述左右的词 描述上下的词;
```

- 描述左右的词：left、center、right
- 描述上下的词：top 、center、bottom

比如说，`right center`表示将图片放到右边的中间；`center center`表示将图片放到正中间。

比如说，`bottom`表示图片的底边和父亲**底边贴齐**（好好理解）。

位置属性有很多使用场景的。我们来举两个例子。

场景1：（大背景图）

打开“暗黑3 台湾”的官网<https://tw.battle.net/d3/zh/>，可以看到官网的效果是比较炫的：

![](http://img.smyhvae.com/20170812_1945.jpg)

检查网页后，找到网站背景图片的url：<https://tw.battle.net/d3/static/images/layout/bg-repeat.jpg>。背景图如下：

![](http://img.smyhvae.com/20170812_1950.jpg)

实际上，我们是通过把这张图片作为网站的背景图来达到显示效果的。只需要给body标签加如下属性即可：

```
        body{
            background-image: url(/Users/smyhvae/Dropbox/img/20170812_1950.jpg);
            background-repeat: no-repeat;
            background-position: center top;
        }
```

上方代码中，如果没加`background-position`这个属性，背景图会默认处于浏览器的左上角（显得很丑）；加了此属性之后，图片在水平方向就位于浏览器的中间了。

场景2：（通栏banner）

很多网站的首页都会有banner图（网站最上方的全屏大图叫做「**通栏banner**」），这种图要求横向的宽度特别大。比如说，设计师给你一张1920*465的超大banner图，如果我们把这个banner图作为img标签直接插入网页中，会有问题的：首先，图片不在网页的中间；其次，肯定会出现横向滚动条。如下图所示：

![](http://img.smyhvae.com/20170813_1102.gif)

正确的做法是，将banner图作为div的背景图，这样的话，背景图超出div的部分，会自动移溢出。需要给div设置的属性如下：

```css
        div{
            height: 465px;
            background-image: url(http://img.smyhvae.com/20170813_1053.jpg);
            background-position: center top;
            background-repeat: no-repeat;
        }
```

上方代码中，我们给div设置height（高度为banner图的高度），不需要设置宽度（因为宽度会自动霸占整行）。效果如下：

![](http://img.smyhvae.com/20170813_1119.gif)

上图可以看出，将banner图作为div的背景后，banner图会永远处于网页的正中间（水平方向来看）。

### background-attachment属性

- `background-attachment:scroll;` 设置背景图片是否固定。属性值可以是：
    - `fixed`（背景就会被固定住，不会被滚动条滚走）。
    - `scroll`（与fixed属性相反，默认属性）

`background-attachment:fixed;`的效果如下：

![](http://img.smyhvae.com/20170813_1158.gif)

### background 综合属性

background属性和border一样，是一个综合属性，可以将多个属性写在一起。(在[盒子模型](http://www.cnblogs.com/smyhvae/p/7256371.html)这篇文章中专门讲到border)

举例1:

```
    background:red url(1.jpg) no-repeat 100px 100px fixed;
```

等价于：

```
    background-color:red;
    background-image:url(1.jpg);
    background-repeat:no-repeat;
    background-position:100px 100px;
    background-attachment:fixed;
```

以后，我们可以用小属性层叠掉大属性。

上面的属性中，可以任意省略其中的一部分。

比如说，对于下面这样的属性：

```
    background: blue url(images/wuyifan.jpg) no-repeat 100px 100px;
```

效果如下：

![](http://img.smyhvae.com/20170813_1515.png)


PS：以后的CSS3内容中，我们会接触到更多的background属性： background-origin、background-clip、background-size（在CSS2.1背景图片是不能调整尺寸，IE9开始兼容）、多背景。

### 3、定义列表`<dl>`

> 定义列表的作用非常大。

`<dl>`英文单词：definition list，没有属性。dl的子元素只能是dt和dd。

 - `<dt>`：definition title 列表的标题，这个标签是必须的
 - `<dd>`：definition description 列表的列表项，如果不需要它，可以不加

备注：dt、dd只能在dl里面；dl里面只能有dt、dd。

举例：

```html
<dl>
    <dt>第一条</dt>
    <dd>你若是觉得你有实力和我玩，良辰不介意奉陪到底</dd>
    <dd>我会让你明白，我从不说空话</dd>
    <dd>我是本地的，我有一百种方式让你呆不下去；而你，无可奈何</dd>

    <dt>第二条</dt>
    <dd>良辰最喜欢对那些自认能力出众的人出手</dd>
    <dd>你可以继续我行我素，不过，你的日子不会很舒心</dd>
    <dd>你只要记住，我叫叶良辰</dd>
    <dd>不介意陪你玩玩</dd>
    <dd>良辰必有重谢</dd>

</dl>
```

效果：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_09.png)


上图可以看出，定义列表表达的语义是两层：

- （1）是一个列表，列出了几个dd项目
- （2）每一个词儿都有自己的描述项。

备注：dd是描述dt的。




定义列表用法非常灵活，可以一个dt配很多dd：

```html
    <dl>
        <dt>北京</dt>
        <dd>国家首都，政治文化中心</dd>
        <dd>污染很严重，PM2.0天天报表</dd>
        <dt>上海</dt>
        <dd>魔都，有外滩、东方明珠塔、黄浦江</dd>
        <dt>广州</dt>
        <dd>中国南大门，有珠江、小蛮腰</dd>
    </dl>
```

还可以拆开，让每一个dl里面只有一个dt和dd，这样子感觉清晰一些：

```html
    <dl>
        <dt>北京</dt>
        <dd>国家首都，政治文化中心</dd>
        <dd>污染很严重，PM2.0天天报表</dd>
    </dl>

    <dl>
        <dt>上海</dt>
        <dd>魔都，有外滩、东方明珠塔、黄浦江</dd>
    </dl>

    <dl>
        <dt>广州</dt>
        <dd>中国南大门，有珠江、小蛮腰</dd>
    </dl>
```

真实案例：（京东最下方）

![](http://img.smyhvae.com/20170704_1727.png)


上图中的结构如下：

```html
<dl>
    <dt>购物指南</dt>
    <dd>
        <a href="#">购物流程</a>
        <a href="#">会员介绍</a>
        <a href="#">生活旅行/团购</a>
        <a href="#">常见问题</a>
        <a href="#">大家电</a>
        <a href="#">联系客服</a>
    </dd>
</dl>
<dl>
    <dt>配送方式</dt>
    <dd>
        <a href="#">上门自提</a>
        <a href="#">211限时达</a>
        <a href="#">配送服务查询</a>
        <a href="#">配送费收取标准</a>
        <a href="#">海外配送</a>
    </dd>
</dl>

```

京东商品分类如下：

![](http://img.smyhvae.com/20170704_1729.png)

dt、dd都是容器级标签，想放什么都可以。所以，现在就应该更加清晰的知道：用什么标签，不是根据样子来决定，而是语义（语义本质上是结构）。


## 表格标签

表格标签用`<table>`表示。
一个表格`<table>`是由每行`<tr>`组成的，每行是由每个单元格`<td>`组成的。
所以我们要记住，一个表格是由行组成的（行是由列组成的），而不是由行和列组成的。
在以前，要想固定标签的位置，唯一的方法就是表格。现在可以通过CSS定位的功能来实现。但是现在在做页面的时候，表格作用还是有一些的。

例如，一行的单元格：
```html
    <table>
        <tr>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </table>
```
上面的表格中没有加文字，所以在生成的网页中什么都看不到。
例如，3行4列的单元格：
```html
    <table>
        <tr>
            <td>生命壹号</td>
            <td>23</td>
            <td>男</td>
            <td>黄冈</td>
        </tr>

        <tr>
            <td>许嵩</td>
            <td>29</td>
            <td>男</td>
            <td>安徽</td>
        </tr>

        <tr>
            <td>邓紫棋</td>
            <td>23</td>
            <td>女</td>
            <td>香港</td>
        </tr>

    </table>
```
效果：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_10.png)

上图中的表格好像没看到边框呀，不急，接下来看看`<table>`标签的属性。

**`<table>`的属性：**
 - `border`：边框。像素为单位。
 - `style="border-collapse:collapse;"`：单元格的线和表格的边框线合并（表格的两边框合并为一条）
 - `width`：宽度。像素为单位。
 - `height`：高度。像素为单位。
 - `bordercolor`：表格的边框颜色。
 - `align`：**表格**的水平对齐方式。属性值可以填：left right center。
注意：这里不是设置表格里内容的对齐方式，如果想设置内容的对齐方式，要对单元格标签`<td>`进行设置）
 - `cellpadding`：单元格内容到边的距离，像素为单位。默认情况下，文字是紧挨着左边那条线的，即默认情况下的值为0。
注意不是单元格内容到四条边的距离哈，而是到一条边的距离，默认是与左边那条线的距离。如果设置属性`dir="rtl"`，那就指的是内容到右边那条线的距离。
 - `cellspacing`：单元格和单元格之间的距离（外边距），像素为单位。默认情况下的值为0
 - `bgcolor="#99cc66"`：表格的背景颜色。
 - `background="路径src/..."`：背景图片。
背景图片的优先级大于背景颜色。
 - `bordercolorlight`：表格的上、左边框，以及单元格的右、下边框的颜色
 - `bordercolordark`：表格的右、下边框，以及单元格的上、左的边框的颜色
这两个属性的目的是为了设置3D的效果。
 - `dir`：公有属性，单元格内容的排列方式(direction)。 可以 取值：`ltr`：从左到右（left to right，默认），`rtl`：从右到左（right to left）
既然说`dir`是共有属性，如果把这个属性放在任意标签中，那表明这个标签的位置可能会从右开始排列。

单元格带边框的效果：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_11.png)

备注：表格中很细表格边线的制作：
CSS的写法：
```html
style="border-collapse:collapse;"
```

### `<tr>`：行
一个表格就是一行一行组成的嘛。
**属性：**
 - `dir`：公有属性，设置这一行单元格内容的排列方式。可以取值：`ltr`：从左到右（left to right，默认），`rtl`：从右到左（right to left）
 - `bgcolor`：设置这一行的单元格的背景色。
注：没有background属性，即：无法设置这一行的背景图片，如果非要设置，可以用css实现。
 - `height`：一行的高度
 - `align="center"`：一行的内容水平居中显示，取值：left、center、right
 - `valign="center"`：一行的内容垂直居中，取值：top、middle、bottom