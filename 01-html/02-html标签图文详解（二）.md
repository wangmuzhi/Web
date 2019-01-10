<!-- MarkdownTOC -->

- 列表标签
    - 1、无序列表``，无序列表中的每一项是``
        - ul标签实际应用场景
    - 2、有序列表``，里面的每一项是``

<!-- /MarkdownTOC -->


 - 列表标签：`<ul>`、`<OL>`、`<dl>`
 - 表格标签：`<table>`
 - 框架标签及内嵌框架`<iframe>`
 - 表单标签：`<form>`
 - 多媒体标签
 - 滚动字幕标签：`<marquee>`



## 列表标签

列表标签分为三种。

### 1、无序列表`<ul>`，无序列表中的每一项是`<li>`

英文单词解释如下：

- ul：unordered list，“无序列表”的意思。
- li：list item，“列表项”的意思。

例如：

```html
<ul>
    <li>默认1</li>
    <li>默认2</li>
    <li>默认3</li>
</ul>
```

效果：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_01.png)

注意：

- li不能单独存在，必须包裹在ul里面；反过来说，ul的“儿子”不能是别的东西，只能有li。
- 我们这里再次强调，ul的作用，并不是给文字增加小圆点的，而是增加无序列表的“语义”的。



**属性：**

 - `type="属性值"`。属性值可以选： `disc`(实心原点，默认)，`square`(实心方点)，`circle`(空心圆)。
效果如下：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_02_1.png)

不光是`<ul>`标签有`type`属性，`<ul>`里面的`<li>`标签也有`type`属性（虽然说这种写法很少见）。效果如下：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_03.png)

注意：项目符号可以是图片，但是通过CSS设置<li>标记的背景图片来实现(CSS中讲)。

当然了，列表之间是可以**嵌套**的。我们来举个例子：
代码：

```html
  <ul>
    <li><b>北京市</b>
        <ul>
            <li>海淀区</li>
            <li>朝阳区</li>
            <li>东城区</li>

        </ul>
    </li>

    <li><b>广州市</b>
        <ul>
            <li>天河区</li>
            <li>越秀区</li>
        </ul>
    </li>
  </ul>
```
效果：

![](http://img.smyhvae.com/2015-10-01-cnblogs_html_40.png)


#### ul标签实际应用场景

场景1 —— 导航条：

![](http://img.smyhvae.com/20170704_1717.png)

场景2 —— li里面放置的内容可能很多：

![](http://img.smyhvae.com/20170704_1719.png)

声明：ul的儿子，只能是li。但是li是一个容器级标签，**li里面什么都能放，甚至可以再放一个ul**。

### 2、有序列表`<OL>`，里面的每一项是`<li>`

英文单词：Ordered List。

例如：

```html
<ol >
    <li>呵呵哒1</li>
    <li>呵呵哒2</li>
    <li>呵呵哒3</li>
</ol>
```

效果：

![](http://img.smyhvae.com/2015-10-02-cnblogs_html_04.png)

**属性：**
 - `type="属性值"`。属性值可以是：1(阿拉伯数字，默认)、a、A、i、I。结合`start`属性表示`从几开始`。

举例：

```html
<ol type="1">
    <li>呵呵</li>
    <li>呵呵</li>
    <li>呵呵</li>
</ol>

<ol type="a">
    <li>嘿嘿</li>
    <li>嘿嘿</li>
    <li>呵呵</li>
</ol>

<ol type="i" start="4">
    <li>哈哈</li>
    <li>哈哈</li>
    <li>哈哈</li>
</ol>

<ol type="I" start="10">
    <li>么么</li>
    <li>么么</li>
    <li>么么</li>
</ol>
```

效果如下：
![](http://img.smyhvae.com/2015-10-02-cnblogs_html_07.png)

和无序列表一样，有序列表也是可以嵌套的哦，这里就不举类似的例子了。


ol和ul就是语义不一样，怎么使用都是一样的。
ol里面只能有li，li必须被ol包裹。li是容器级。

ol这个东西用的不多，如果想表达顺序，大家一般也用ul。举例如下：

```html
<ul>
    <li>1. 小苹果</li>
    <li>2. 月亮之上</li>
    <li>3. 最炫民族风</li>
</ul>
```