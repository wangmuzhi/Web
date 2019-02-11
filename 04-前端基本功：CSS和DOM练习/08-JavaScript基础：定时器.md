<!-- MarkdownTOC -->

- [定时器的常见方法](#%E5%AE%9A%E6%97%B6%E5%99%A8%E7%9A%84%E5%B8%B8%E8%A7%81%E6%96%B9%E6%B3%95)
    - [定义定时器的方式](#%E5%AE%9A%E4%B9%89%E5%AE%9A%E6%97%B6%E5%99%A8%E7%9A%84%E6%96%B9%E5%BC%8F)
    - [定时器高级：清除定时器](#%E5%AE%9A%E6%97%B6%E5%99%A8%E9%AB%98%E7%BA%A7%EF%BC%9A%E6%B8%85%E9%99%A4%E5%AE%9A%E6%97%B6%E5%99%A8)
- [定时器举例](#%E5%AE%9A%E6%97%B6%E5%99%A8%E4%B8%BE%E4%BE%8B)
    - [举例一：5秒后关闭网页两侧的广告栏](#%E4%B8%BE%E4%BE%8B%E4%B8%80%EF%BC%9A5%E7%A7%92%E5%90%8E%E5%85%B3%E9%97%AD%E7%BD%91%E9%A1%B5%E4%B8%A4%E4%BE%A7%E7%9A%84%E5%B9%BF%E5%91%8A%E6%A0%8F)
    - [举例二：关闭京东顶部广告栏（带动画效果关闭）](#%E4%B8%BE%E4%BE%8B%E4%BA%8C%EF%BC%9A%E5%85%B3%E9%97%AD%E4%BA%AC%E4%B8%9C%E9%A1%B6%E9%83%A8%E5%B9%BF%E5%91%8A%E6%A0%8F%EF%BC%88%E5%B8%A6%E5%8A%A8%E7%94%BB%E6%95%88%E6%9E%9C%E5%85%B3%E9%97%AD%EF%BC%89)

<!-- /MarkdownTOC -->

<a id="%E5%AE%9A%E6%97%B6%E5%99%A8%E7%9A%84%E5%B8%B8%E8%A7%81%E6%96%B9%E6%B3%95"></a>
## 定时器的常见方法

- setInterval()：循环定时器。周而复始的执行（循环执行）

- setTimeout()：定时炸弹。用完以后立刻报废（只执行一次）


<a id="%E5%AE%9A%E4%B9%89%E5%AE%9A%E6%97%B6%E5%99%A8%E7%9A%84%E6%96%B9%E5%BC%8F"></a>
### 定义定时器的方式

**方式一：**匿名函数

每间隔一秒打印一次：

```javascript
   setInterval(function () {
       console.log(1);
   },1000);
```

**方式二：**

每间隔一秒打印一次：


```javascript
    setInterval(fn,1000);

    function fn(){
        console.log(1);
    }

```

<a id="%E5%AE%9A%E6%97%B6%E5%99%A8%E9%AB%98%E7%BA%A7%EF%BC%9A%E6%B8%85%E9%99%A4%E5%AE%9A%E6%97%B6%E5%99%A8"></a>
### 定时器高级：清除定时器

定时器的返回值可以用来清除定时器。具体方法是：假设定时器setInterval()的返回值是`参数1`，那么`clearInterval(参数1)`就可以清除定时器。

setTimeout()的道理是一样的。

代码举例：



```html
<script>
    var num = 1;

    var timer = setInterval(function () {
        console.log(num);  //每间隔一秒，打印一次num的值
        num ++;
        if(num ===5) {  //打印四次之后，就清除定时器
            clearInterval(timer);
        }

    }, 1000);
</script>

```

<a id="%E5%AE%9A%E6%97%B6%E5%99%A8%E4%B8%BE%E4%BE%8B"></a>
## 定时器举例

<a id="%E4%B8%BE%E4%BE%8B%E4%B8%80%EF%BC%9A5%E7%A7%92%E5%90%8E%E5%85%B3%E9%97%AD%E7%BD%91%E9%A1%B5%E4%B8%A4%E4%BE%A7%E7%9A%84%E5%B9%BF%E5%91%8A%E6%A0%8F"></a>
### 举例一：5秒后关闭网页两侧的广告栏

假设网页两侧的广告栏为两个img标签，它们的样式为：


```html
<style>
    ...
    ...

</style>

```

5秒后关闭广告栏的js代码为：

```html
    <script>
        window.onload = function () {
            //获取相关元素
            var imgArr = document.getElementsByTagName("img");
            //设置定时器：5秒后关闭两侧的广告栏
            setTimeout(fn,5000);
            function fn(){
                imgArr[0].style.display = "none";
                imgArr[1].style.display = "none";
            }
        }
    </script>
```


<a id="%E4%B8%BE%E4%BE%8B%E4%BA%8C%EF%BC%9A%E5%85%B3%E9%97%AD%E4%BA%AC%E4%B8%9C%E9%A1%B6%E9%83%A8%E5%B9%BF%E5%91%8A%E6%A0%8F%EF%BC%88%E5%B8%A6%E5%8A%A8%E7%94%BB%E6%95%88%E6%9E%9C%E5%85%B3%E9%97%AD%EF%BC%89"></a>
### 举例二：关闭京东顶部广告栏（带动画效果关闭）

我们在[之前的文章](https://github.com/smyhvae/Web/blob/master/03-JavaScript%E5%9F%BA%E7%A1%80/07-JavaScript%E5%9F%BA%E7%A1%80%EF%BC%9ADOM%E6%93%8D%E4%BD%9C.md)中做过这道题。但是现在，要求广告栏在关闭的时候，带动画效果：**点击关闭按钮后，顶部广告栏慢慢地变透明，直到全部关闭。**

我们可以用定时器来做。完整版代码如下：

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

        .top-banner {
            background-color: pink;
            height: 80px;
        }

        .w {
            width: 1210px;
            margin: 10px auto;
            position: relative;
        }

        img {
            display: block;
            width: 1210px;
            height: 80px;
            background-color: blue;
        }

        a {
            position: absolute;
            top: 5px;
            right: 5px;
            color: #fff;
            background-color: #000;
            text-decoration: none;
            width: 20px;
            height: 20px;
            font: 700 14px/20px "simsum";
            text-align: center;
        }

        .hide {
            display: none !important;
        }

        .search {
            width: 1210px;
            height: 80px;
            background-color: green;
            margin: 0 auto;
        }
    </style>
</head>
<body>
<div class="top-banner" id="topBanner" style="opacity: 1">
    <div class="w">
        <img src="blue" alt=""/>
        <a href="#" id="closeBanner">×</a>
    </div>
</div>
<div class="search">

</div>

<script>
    //需求：点击关闭按钮，先让top-banner这个盒子透明度变为0，紧接着display：none;

    //1.获取事件源和相关元素
    var closeBanner = document.getElementById("closeBanner");
    var topBanner = document.getElementById("topBanner");
    //定义定时器
    var timer = null;
    //2.绑定事件
    closeBanner.onclick = function () {
        //3.书写事件驱动程序（定时器，透明度变为0，清除定时器，并隐藏盒子）
        timer = setInterval(function () {
            topBanner.style.opacity -= 0.1;
            if (topBanner.style.opacity < 0) {
                topBanner.style.display = "none";
                clearInterval(timer);
            }
        }, 50);
    }
</script>
</body>
</html>
```

代码解释：

注意，我们要实现给顶部的div加一个行内样式`style="opacity: 1"`，然后才能通过定时器判断`topBanner.style.opacity`的值。

定时器的返回值其实是number类型的，但我们习惯性地设置初始值为null。

实现效果：

![](http://img.smyhvae.com/20180201_2240.gif)

