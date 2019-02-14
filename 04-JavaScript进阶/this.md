<!-- MarkdownTOC -->

- [this](#this)
    - [this的作用](#this%E7%9A%84%E4%BD%9C%E7%94%A8)
    - [全局作用域中的this](#%E5%85%A8%E5%B1%80%E4%BD%9C%E7%94%A8%E5%9F%9F%E4%B8%AD%E7%9A%84this)
- [this的定律](#this%E7%9A%84%E5%AE%9A%E5%BE%8B)
    - [函数赋值给变量时，this指向window](#%E5%87%BD%E6%95%B0%E8%B5%8B%E5%80%BC%E7%BB%99%E5%8F%98%E9%87%8F%E6%97%B6%EF%BC%8Cthis%E6%8C%87%E5%90%91window)
    - [以函数形式调用时，this永远都是window](#%E4%BB%A5%E5%87%BD%E6%95%B0%E5%BD%A2%E5%BC%8F%E8%B0%83%E7%94%A8%E6%97%B6%EF%BC%8Cthis%E6%B0%B8%E8%BF%9C%E9%83%BD%E6%98%AFwindow)
    - [以方法的形式调用时，this是调用方法的对象](#%E4%BB%A5%E6%96%B9%E6%B3%95%E7%9A%84%E5%BD%A2%E5%BC%8F%E8%B0%83%E7%94%A8%E6%97%B6%EF%BC%8Cthis%E6%98%AF%E8%B0%83%E7%94%A8%E6%96%B9%E6%B3%95%E7%9A%84%E5%AF%B9%E8%B1%A1)
- [解决闭包中的this指向问题](#%E8%A7%A3%E5%86%B3%E9%97%AD%E5%8C%85%E4%B8%AD%E7%9A%84this%E6%8C%87%E5%90%91%E9%97%AE%E9%A2%98)
    - [当this遇到一些特殊的函数时](#%E5%BD%93this%E9%81%87%E5%88%B0%E4%B8%80%E4%BA%9B%E7%89%B9%E6%AE%8A%E7%9A%84%E5%87%BD%E6%95%B0%E6%97%B6)

<!-- /MarkdownTOC -->

<a id="this"></a>
## this

<a id="this%E7%9A%84%E4%BD%9C%E7%94%A8"></a>
### this的作用

- this可以帮我们简化很多代码。比如`xiaoming.name`、`xiaoming.age`可以直接写成`this.name`、`this.age`。

- 特别是当我们不知道一个对象是什么，或者这个对象没有名字但又很想调用它的时候，就会使用到this对象。

**举例：**

- 遍历DOM对象，绑定click事件，调用当前点击的对象的id，而不是所有对象的id。

代码：

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
    <title>Document</title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: green;
            margin: 10px;
        }

    </style>
</head>
<body>
<script>
    window.onload = function () {
        var myDiv = document.getElementsByTagName('div');
        for (var i = 0; i < myDiv.length; i++) {
            myDiv[i].onclick = function () {
                console.log(i);
                console.log(this.id);
            }
        }

    }

</script>
<section>
    <div id="div0"> div0</div>
    <div id="div1"> div1</div>
    <div id="div2"> div2</div>
    <div id="div3"> div3</div>
    <div id="div4"> div4</div>
</section>


</body>
</html>

```


点击其中的任何一个元素后，`i`的打印结果是5。你可能会觉得很惊讶。我们来解释一下：

当代码执行完毕后，i已经等于5了。因为一旦运行程序，for循环已经执行完了，此时i等于5。

现在，我们尝试在 myDiv[i].onclick事件中写代码，如果打印：

```
	console.log(i);  //打印结果为5
```


如果打印：

```
	console.log(myDiv[i].id);
```

上方这行代码，打印会报错，因为i=5；如果想打印每个div的id，应该这样写：

```
	console.log(this.id);
```

你看，this的作用，就体现出来了。

PS：顺便提醒一下，上面的代码中，如果把`var i`改成`let i`，效果又完全不同了。参考链接：[let和var在for循环中的表现](http://blog.csdn.net/stopllL/article/details/64130664)

<a id="%E5%85%A8%E5%B1%80%E4%BD%9C%E7%94%A8%E5%9F%9F%E4%B8%AD%E7%9A%84this"></a>
### 全局作用域中的this

当一段代码在浏览器中执行时，所有的全局变量和对象都是在window对象上定义的。换而言之，所有的全局变量和对象都属于window对象。


<a id="this%E7%9A%84%E5%AE%9A%E5%BE%8B"></a>
## this的定律

this关键字永远指向函数（方法）运行时的**所有者**。

<a id="%E5%87%BD%E6%95%B0%E8%B5%8B%E5%80%BC%E7%BB%99%E5%8F%98%E9%87%8F%E6%97%B6%EF%BC%8Cthis%E6%8C%87%E5%90%91window"></a>
### 函数赋值给变量时，this指向window


比如：

```
var foo1 = args.getInfo;
foo1();

var foo2 = function(){};
foo2();
```


this都是指向window。

<a id="%E4%BB%A5%E5%87%BD%E6%95%B0%E5%BD%A2%E5%BC%8F%E8%B0%83%E7%94%A8%E6%97%B6%EF%BC%8Cthis%E6%B0%B8%E8%BF%9C%E9%83%BD%E6%98%AFwindow"></a>
### 以函数形式调用时，this永远都是window


<a id="%E4%BB%A5%E6%96%B9%E6%B3%95%E7%9A%84%E5%BD%A2%E5%BC%8F%E8%B0%83%E7%94%A8%E6%97%B6%EF%BC%8Cthis%E6%98%AF%E8%B0%83%E7%94%A8%E6%96%B9%E6%B3%95%E7%9A%84%E5%AF%B9%E8%B1%A1"></a>
### 以方法的形式调用时，this是调用方法的对象


<a id="%E8%A7%A3%E5%86%B3%E9%97%AD%E5%8C%85%E4%B8%AD%E7%9A%84this%E6%8C%87%E5%90%91%E9%97%AE%E9%A2%98"></a>
## 解决闭包中的this指向问题


内部函数是可以访问到外部函数的变量的。

方式一：直接通过父函数的名字访问

方式二：如果不知道父函数的名字，在父函数里加一句`_this = this`，此时`_this`相当于父函数的名字。

<a id="%E5%BD%93this%E9%81%87%E5%88%B0%E4%B8%80%E4%BA%9B%E7%89%B9%E6%AE%8A%E7%9A%84%E5%87%BD%E6%95%B0%E6%97%B6"></a>
### 当this遇到一些特殊的函数时











