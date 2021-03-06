<!-- MarkdownTOC -->

- [隐藏盒子的几种方式](#%E9%9A%90%E8%97%8F%E7%9B%92%E5%AD%90%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E5%BC%8F)
    - [设置盒子的半透明](#%E8%AE%BE%E7%BD%AE%E7%9B%92%E5%AD%90%E7%9A%84%E5%8D%8A%E9%80%8F%E6%98%8E)
    - [给标签的形状设置为圆角矩形](#%E7%BB%99%E6%A0%87%E7%AD%BE%E7%9A%84%E5%BD%A2%E7%8A%B6%E8%AE%BE%E7%BD%AE%E4%B8%BA%E5%9C%86%E8%A7%92%E7%9F%A9%E5%BD%A2)
    - [行高的问题：儿子把父亲撑开](#%E8%A1%8C%E9%AB%98%E7%9A%84%E9%97%AE%E9%A2%98%EF%BC%9A%E5%84%BF%E5%AD%90%E6%8A%8A%E7%88%B6%E4%BA%B2%E6%92%91%E5%BC%80)
    - [背景图不能撑开盒子](#%E8%83%8C%E6%99%AF%E5%9B%BE%E4%B8%8D%E8%83%BD%E6%92%91%E5%BC%80%E7%9B%92%E5%AD%90)
- [JS](#js)
    - [超链接``的href跳转](#%E8%B6%85%E9%93%BE%E6%8E%A5%E7%9A%84href%E8%B7%B3%E8%BD%AC)

<!-- /MarkdownTOC -->

## 隐藏盒子的几种方式

隐藏盒子，有以下几种方式：

（1）方式一：

```
overflow：hidden;   //隐藏盒子超出的部分
```


（2）**方式二**：

```
display: none;	  隐藏盒子，而且不占位置(用的最多)
```

比如，点击`X`，关闭京东首页上方的广告栏。

（3）方式三：

```
visibility: hidden;   //隐藏盒子，占位置。
visibility: visible;   //让盒子重新显示

```

（4）方式四：

```
pacity: 0;       //设置盒子的透明度（不建议，因为内容也会半透明），占位置
```


（4）方式五：

```
Position/top/left/...-999px   //把盒子移得远远的，占位置。
```

（5）方式六：

```
margin-left: 1000px;
```



### 设置盒子的半透明

方式一：`pacity: 0.4`。优点是方便。缺点是：里面的内容也会半透明


方式二：css3的技术来解决半透明。如下：

- background: rgba(0,0,0,0.3);

- background: rgba(0,0,0,.3);

备注：`a`指的是alpha透明度。


### 给标签的形状设置为圆角矩形

```
border-radius: 50%;
border-radius: 10px 0 0 10px;
```


### 行高的问题：儿子把父亲撑开

比如对于下面这样的标签：

```
	<div>
		<a href=""></a>
	</div>

```


前置条件：如果我们给父亲div的行高设为31px，然后给儿子a的行高也设置为31

结果：当我们给儿子a设置了字体属性之后，会发现，父亲被撑高为32px了。因为font字体自身会比较大，多撑出了一个像素。

解决办法：**行内元素尽量不要设置font属性**。对于行内元素而言，如果它和父亲都设置了行高，就不要去给自己设置font属性了。要么就，不要同时设置行高。


### 背景图不能撑开盒子

高和行高都可以城开盒子，但背景图不能撑开盒子。







## JS

### 超链接`<a>`的href跳转

一个空白的超链接如下：

```
<a href=""></a>
```

当点击超链接时，由于 href 的属性值的不同，可以产生很多种情况：

```bash
	href=""                    //刷新页面

	href="#"                   //跳转到当前页面的顶部（不会刷新）

	href="javascript:void(0)"  // 什么都不做

	href="javascript:;"        // 什么都不做

```

