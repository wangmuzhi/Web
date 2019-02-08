<!-- MarkdownTOC -->

- [举例引入：鼠标悬停时，current元素的背景变色](#%E4%B8%BE%E4%BE%8B%E5%BC%95%E5%85%A5%EF%BC%9A%E9%BC%A0%E6%A0%87%E6%82%AC%E5%81%9C%E6%97%B6%EF%BC%8Ccurrent%E5%85%83%E7%B4%A0%E7%9A%84%E8%83%8C%E6%99%AF%E5%8F%98%E8%89%B2)
- [tab切换：初步的代码](#tab%E5%88%87%E6%8D%A2%EF%BC%9A%E5%88%9D%E6%AD%A5%E7%9A%84%E4%BB%A3%E7%A0%81)
- [tab切换：改进版代码（函数封装）](#tab%E5%88%87%E6%8D%A2%EF%BC%9A%E6%94%B9%E8%BF%9B%E7%89%88%E4%BB%A3%E7%A0%81%EF%BC%88%E5%87%BD%E6%95%B0%E5%B0%81%E8%A3%85%EF%BC%89)
    - [方式一：给current标签设置index值【推荐的代码】](#%E6%96%B9%E5%BC%8F%E4%B8%80%EF%BC%9A%E7%BB%99current%E6%A0%87%E7%AD%BE%E8%AE%BE%E7%BD%AEindex%E5%80%BC%E3%80%90%E6%8E%A8%E8%8D%90%E7%9A%84%E4%BB%A3%E7%A0%81%E3%80%91)
    - [方式二：通过attribute设置index的值](#%E6%96%B9%E5%BC%8F%E4%BA%8C%EF%BC%9A%E9%80%9A%E8%BF%87attribute%E8%AE%BE%E7%BD%AEindex%E7%9A%84%E5%80%BC)

<!-- /MarkdownTOC -->


京东网页上，可以看到下面这种tab栏的切换：

![](http://img.smyhvae.com/20180128_1750.gif)

我们把模型抽象出来，实现一下。

<a id="%E4%B8%BE%E4%BE%8B%E5%BC%95%E5%85%A5%EF%BC%9A%E9%BC%A0%E6%A0%87%E6%82%AC%E5%81%9C%E6%97%B6%EF%BC%8Ccurrent%E5%85%83%E7%B4%A0%E7%9A%84%E8%83%8C%E6%99%AF%E5%8F%98%E8%89%B2"></a>
## 举例引入：鼠标悬停时，current元素的背景变色

> 本段我们先举一个例子，因为这里用到了**排他思想**（先干掉 all，然后保留我一个）。对于理解tab切换，很有帮助。

完整的代码实现：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        button {
            margin: 10px;
            width: 100px;
            height: 40px;
            cursor: pointer;
        }
        .current {
            background-color: red;
        }
    </style>
</head>
<body>
<button>按钮1</button>
<button>按钮2</button>
<button>按钮3</button>
<button>按钮4</button>
<button>按钮5</button>

<script>
    //需求：鼠标放到哪个button上，改button变成黄色背景（添加类）


    var btnArr = document.getElementsByTagName("button");
    //绑定事件
    for(var i=0;i<btnArr.length;i++){   //要为每一个按钮绑定事件，所以用到了for循环
        btnArr[i].onmouseover = function () {
            //【重要】排他思想：先把所有按钮的className设置为空，然后把我（this）这个按钮的className设置为current
            //排他思想和for循环连用
            for(var j=0;j<btnArr.length;j++){
                btnArr[j].className = "";
            }
            this.className = "current";  //【重要】核心代码
        }
    }

    //鼠标离开current时，还原背景色
    for(var i=0;i<btnArr.length;i++){   //要为每一个按钮绑定事件，所以用到了for循环
        btnArr[i].onmouseout = function () { //鼠标离开任何一个按钮时，就把按钮的背景色还原
            this.className = "";
        }
    }

</script>

</body>
</html>
```

代码解释：

鼠标悬停时，current栏变色，这里用到了排他思想：先把所有按钮的className设置为空，然后把我(this)这个按钮的className设置为current，就可以达到变色的效果。核心代码是：


```javascript
            //排他思想：先把所有按钮的className设置为空，然后把我（this）这个按钮的className设置为current
            //排他思想和for循环连用
            for(var j=0;j<btnArr.length;j++){
                btnArr[j].className = "";
            }
            this.className = "current";
```

实现的效果如下：


![](http://img.smyhvae.com/20180128_1740.gif)

<a id="tab%E5%88%87%E6%8D%A2%EF%BC%9A%E5%88%9D%E6%AD%A5%E7%9A%84%E4%BB%A3%E7%A0%81"></a>
## tab切换：初步的代码

代码如下：


```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        .box {
            width: 500px;
            height: 200px;
            border: 1px solid #ccc;
            margin: 50px auto;
            overflow: hidden;
        }
        ul {
            width: 600px;
            height: 40px;
            margin-left: -1px;
            list-style: none;
        }
        li {
            float: left;
            width: 101px;
            height: 40px;
            text-align: center;
            font: 600 18px/40px "simsun";
            background-color: pink;
            cursor: pointer;
        }
        span {
            display: none;
            width: 500px;
            height: 160px;
            background-color: yellow;
            text-align: center;
            font: 700 100px/160px "simsun";
        }
        .show {
            display: block;
        }
        .current {
            background-color: yellow;
        }
    </style>

    <script>
        window.onload = function () {
            //需求：鼠标放到上面的li上，li本身变色(添加类)，对应的span也显示出来(添加类);
            //思路：1.点亮上面的盒子。   2.利用索引值显示下面的盒子。

            var liArr = document.getElementsByTagName("li");
            var spanArr = document.getElementsByTagName("span");

            for(var i=0;i<liArr.length;i++){
                //绑定索引值（新增一个自定义属性：index属性）
                liArr[i].index = i;
                liArr[i].onmouseover = function () {

                    //1.点亮上面的盒子。   2.利用索引值显示下面的盒子。(排他思想)
                    for(var j=0;j<liArr.length;j++){
                        liArr[j].className = "";
                        spanArr[j].className = "";
                    }
                    this.className = "current";
                    spanArr[this.index].className = "show"; //【重要代码】
                }
            }
        }
    </script>
</head>
<body>

<div class="box">
    <ul>
        <li class="current">鞋子</li>
        <li>袜子</li>
        <li>帽子</li>
        <li>裤子</li>
        <li>裙子</li>
    </ul>
    <span class="show">鞋子</span>
    <span>袜子</span>
    <span>帽子</span>
    <span>裤子</span>
    <span>裙子</span>
</div>

</body>
</html>
```

实现效果如下：

![](http://img.smyhvae.com/20180128_1610.gif)

上方代码的核心部分是：

```javascript
            for(var i=0;i<liArr.length;i++){
                //绑定索引值（新增一个自定义属性：index属性）
                liArr[i].index = i;
                liArr[i].onmouseover = function () {

                    //1.点亮上面的盒子。   2.利用索引值显示下面的盒子。(排他思想)
                    for(var j=0;j<liArr.length;j++){
                        liArr[j].className = "";
                        spanArr[j].className = "";
                    }
                    this.className = "current";
                    spanArr[this.index].className = "show"; //【重要代码】
                }
            }

```

这段代码中，我们是通过给 `liArr[i]`一个index属性：` liArr[i].index = i`，然后让下方的span对应的index也随之对应显示：`spanArr[this.index].className = "show"`。

这样做比较难理解，其实还有一种容易理解的方法是：**给liArr[i]增加index属性时，通过attribute的方式**，因为这种方式增加的属性是可以显示在标签上的。也就有了下面这样的代码：

```javascript
            for(var i=0;i<liArr.length;i++){
                //绑定索引值(自定义属性)，通过Attribute的方式【重要】
                liArr[i].setAttribute("index",i);
                liArr[i].onmouseover = function () {
                    //3.书写事件驱动程序（排他思想）
                    //1.点亮盒子。   2.利用索引值显示盒子。(排他思想)
                    for(var j=0;j<liArr.length;j++){
                        liArr[j].removeAttribute("class");
                        spanArr[j].removeAttribute("class");
                    }
                    this.setAttribute("class","current");
                    spanArr[this.getAttribute("index")].setAttribute("class","show");
                }
            }

```

显示的效果是一样的，不同的地方在于，我们审查元素发现，li标签中确实新增了自定义的index属性：

![](http://img.smyhvae.com/20180128_1625.gif)

本段中，我们的目的已经达到了，不足的地方在于，**本段中的代码是通过document获取的的标签**，如果网页中有很多个这种tab选项卡，必然互相影响。

为了多个tab栏彼此独立，我们就需要通过**封装函数**的方式把他们抽取出来，于是就有了下面的改进版代码。

<a id="tab%E5%88%87%E6%8D%A2%EF%BC%9A%E6%94%B9%E8%BF%9B%E7%89%88%E4%BB%A3%E7%A0%81%EF%BC%88%E5%87%BD%E6%95%B0%E5%B0%81%E8%A3%85%EF%BC%89"></a>
## tab切换：改进版代码（函数封装）

<a id="%E6%96%B9%E5%BC%8F%E4%B8%80%EF%BC%9A%E7%BB%99current%E6%A0%87%E7%AD%BE%E8%AE%BE%E7%BD%AEindex%E5%80%BC%E3%80%90%E6%8E%A8%E8%8D%90%E7%9A%84%E4%BB%A3%E7%A0%81%E3%80%91"></a>
### 方式一：给current标签设置index值【推荐的代码】

完整版代码实现：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        .box {
            width: 500px;
            height: 200px;
            border: 1px solid #ccc;
            margin: 50px auto;
            overflow: hidden;
        }

        ul {
            width: 600px;
            height: 40px;
            margin-left: -1px;
            list-style: none;
        }

        li {
            float: left;
            width: 101px;
            height: 40px;
            text-align: center;
            font: 600 18px/40px "simsun";
            background-color: pink;
            cursor: pointer;
        }

        span {
            display: none;
            width: 500px;
            height: 160px;
            background-color: yellow;
            text-align: center;
            font: 700 100px/160px "simsun";
        }

        .show {
            display: block;
        }

        .current {
            background-color: yellow;
        }
    </style>

    <script>
        window.onload = function () {
            //需求：鼠标放到上面的li上，li本身变色(添加类)，下方对应的span也显示出来(添加类);
            //思路：1.点亮上面的盒子。   2.利用索引值显示下面的对应的盒子。

            //1、获取所有的box
            var boxArr = document.getElementsByClassName("box");

            //让每一个box都调用函数
            for (var i = 0; i < boxArr.length; i++) {
                fn(boxArr[i]);
            }

            function fn(element) {
                var liArr = element.getElementsByTagName("li");   //注意，是element获取事件源，不是document获取事件源
                var spanArr = element.getElementsByTagName("span");
                //2.绑定事件（循环绑定）
                for (var i = 0; i < liArr.length; i++) {
                    //绑定索引值（新增一个自定义属性：index属性）
                    liArr[i].index = i;
                    liArr[i].onmouseover = function () {
                        //3.书写事件驱动程序（排他思想）
                        //1.点亮上面的盒子。   2.利用索引值显示下面的盒子。(排他思想)
                        for (var j = 0; j < liArr.length; j++) {
                            liArr[j].className = "";
                            spanArr[j].className = "";
                        }
                        this.className = "current";
                        spanArr[this.index].className = "show"; //【重要】核心代码
                    }
                }
            }
        }
    </script>
</head>
<body>

<div class="box">
    <ul>
        <li class="current">鞋子</li>
        <li>袜子</li>
        <li>帽子</li>
        <li>裤子</li>
        <li>裙子</li>
    </ul>
    <span class="show">鞋子</span>
    <span>袜子</span>
    <span>帽子</span>
    <span>裤子</span>
    <span>裙子</span>
</div>

<div class="box">
    <ul>
        <li class="current">鞋子</li>
        <li>袜子</li>
        <li>帽子</li>
        <li>裤子</li>
        <li>裙子</li>
    </ul>
    <span class="show">鞋子</span>
    <span>袜子</span>
    <span>帽子</span>
    <span>裤子</span>
    <span>裙子</span>
</div>

<div class="box">
    <ul>
        <li class="current">鞋子</li>
        <li>袜子</li>
        <li>帽子</li>
        <li>裤子</li>
        <li>裙子</li>
    </ul>
    <span class="show">鞋子</span>
    <span>袜子</span>
    <span>帽子</span>
    <span>裤子</span>
    <span>裙子</span>
</div>

</body>
</html>
```

注意，通过函数fn的封装之后，我们是通过参数element获取元素，而不再是document了。这样可以达到“抽象性”的作用，各个tab栏之间相互独立。

上方代码中，我们是通过给 liArr[i]一个index属性：` liArr[i].index = i`，然后让下方的span对应的index也随之对应显示：`spanArr[this.index].className = "show"`。

这样做比较难理解，根据上一段的规律，当然还有一种容易理解的方法是：**给liArr[i]增加index属性时，通过attribute的方式**，因为这种方式增加的属性是可以显示在标签上的。也就有了下面的方式二。

<a id="%E6%96%B9%E5%BC%8F%E4%BA%8C%EF%BC%9A%E9%80%9A%E8%BF%87attribute%E8%AE%BE%E7%BD%AEindex%E7%9A%84%E5%80%BC"></a>
### 方式二：通过attribute设置index的值

基于上面方式一中的代码，我们修改一下js部分的代码，其他部分的代码保持不变。js部分的代码如下：

```html
    <script>
        window.onload = function () {
            //需求：鼠标放到上面的li上，li本身变色(添加类)，下方对应的span也显示出来(添加类);
            //思路：1.点亮上面的盒子。   2.利用索引值显示下面的对应的盒子。

            //1、获取所有的box
            var boxArr = document.getElementsByClassName("box");

            //让每一个box都调用函数
            for (var i = 0; i < boxArr.length; i++) {
                fn(boxArr[i]);
            }

            function fn(element) {
                var liArr = element.getElementsByTagName("li");   //注意，是element获取事件源，不是document获取事件源
                var spanArr = element.getElementsByTagName("span");
                //2.绑定事件（循环绑定）
                for (var i = 0; i < liArr.length; i++) {
                    //绑定索引值(自定义属性)
                    liArr[i].setAttribute("index", i);
                    liArr[i].onmouseover = function () {
                        //3.书写事件驱动程序（排他思想）
                        //1.点亮盒子。   2.利用索引值显示盒子。(排他思想)
                        for (var j = 0; j < liArr.length; j++) {
                            liArr[j].removeAttribute("class");    //注意，这里是class，不是className
                            spanArr[j].removeAttribute("class");
                        }
                        this.setAttribute("class", "current");
                        spanArr[this.getAttribute("index")].setAttribute("class", "show");
                    }
                }
            }
        }
    </script>
```

不过，方式一的写法应该比方式二更常见。

**总结**：通过函数封装的形式，可以保证各个tab栏之间的切换互不打扰。最终实现效果如下：

![](http://img.smyhvae.com/20180128_1651.gif)

