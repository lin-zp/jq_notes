## jQuery—DOM操作

#### 1.查找节点

##### 1.1 查找元素节点

```
var $li = $('ul li:eq(1)');			//获取<ul>里第二个节点
```

##### 1.2 查找属性节点

​		使用jQuery选择器找到需要的元素后，可用attr()方法获取该元素的属性值。

```
var $para = $("P");
var p_txt = $para.attr("title");	//获取<p>元素的title属性
alert（p_txt）；
```

#### 2.创建节点

##### 2.1 创建元素节点

```
var $li_1 = $("<li></li>");
var $li_2 = $("<li></li>");		//创建两个元素

$("ul").append($li_1);
	   .append($li_1);		//添加到<ul>节点中
```

##### 2.2 创建文本节点

```
var $li_1 = $("<li>香蕉</li>");
var $li_2 = $("<li>苹果</li>");		//创建两个元素节点，元素中的文本为文本节点

$("ul").append($li_1);
	   .append($li_1);		//添加到<ul>节点中
```

##### 2.3 创建属性节点

```
var $li_1 = $("<li title='香蕉'>香蕉</li>");
var $li_2 = $("<li title='苹果'>苹果</li>");		//创建两个元素节点，元素中的文本为文本节点，title为属性节点

$("ul").append($li_1);
	   .append($li_1);		//添加到<ul>节点中
```

#### 3.插入节点

| 方法           | 描述                                                         | 示例                                                         |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| append()       | 向匹配的元素内部追加内容                                     | <p>说：</p><br/>$("p").append("<t>你好</t>")<br />结果：<p>说：<t>你好</t></p> |
| appendTo()     | 将匹配的元素追加到指定元素中<br/>即颠倒了append()的操作      | <p>说：</p><br/>$("<t>你好</t>").append("p")<br />结果：<p>说：<t>你好</t></p> |
| prepend()      | 向所有匹配的元素内部前置内容                                 | <p>说：</p><br/>$("p").prepend("<t>你好</t>")<br />结果：<p><t>你好</t>说：</p> |
| prependTo()    | 将所有匹配的元素追加前置到指定元素中<br/>即颠倒了prepend()的操作 | <p>说：</p><br/>$("<t>你好</t>").prependTo("p")<br />结果：<p><t>你好</t>说：</p> |
| after()        | 在每个匹配元素后面插入内容                                   | $("p").after("<t>你好</t>")<br>结果：<p><p><t>你好</t>       |
| insertAfter()  | 将所有匹配的元素插入到指定元素后面<br>即颠倒了after()的操作  | $("<t>你好</t>").after("p")<br/>结果：<p><p><t>你好</t>      |
| before()       | 在每个匹配元素前面插入内容                                   | $("p").before("<t>你好</t>")<br/>结果：<t>你好</t><p><p>     |
| insertBefore() | 将所有匹配的元素插入到指定元素前面<br/>即颠倒了before()的操作 | $("<t>你好</t>").before("p")<br/>结果：<t>你好</t><p><p>     |

这些方法不仅能插入新创建的节点元素，也可以对原有的节点元素进行移动，例：

```
var $one_li = $("ul li:eq(0)");
var $two_li = $("ul li:eq(1)");		//获取<ul>元素中的第1和第2个<li>元素
$two_li.insertbefore($one_li);		//移动节点
```

#### 4.删除节点

##### 4.1 remove()方法

从DOM中删除所有匹配的元素

```
$("ul li:eq(1)").remove();		//删除<ul>元素中的第二个<li>元素
```

使用remove()方法后，该节点所包含的所有后代节点也被删除。此方法返回值是一个指向被删除节点的引用，即删除后的节点还可以继续使用，如：

```
var $li = $("ul li:eq(1)").remove();		//删除<ul>元素中的第二个<li>元素
$li.appendTo("ul");		//删除的节点又加回来
```

也可以直接用appendTo()实现

```
$("ul li:eq(1)").appendTo("ul");		//移动元素时，首先会删除此元素，再插入指定节点
```

remove()方法也可以选择性删除

```
$("ul li").remove("li[title!=菠萝]");		//将li元素中属性title不等于"菠萝"的li元素删除
```

##### 4.2 empty()方法

empty()方法是清空节点，清空元素中所有的后代节点。

```
$("ul li:eq(1)").remove();		//获取第二个li元素节点，清空元素里的内容，li节点不会被删除
```

#### 5.复制节点

使用clone(value)方法对节点进行复制，value为true时，被复制的节点保存原节点的功能（如点击事件）

```
$("ul li").click(function(){
	$this.clone().appendTo("ul");		//复制点击的节点，追加到ul元素中
})
```

#### 6.替换节点

使用replaceWith()方法或replaceAll()方法，replaceWith()方法是将所有匹配的元素替换成指定的元素，如：

```
$("p").replaceWith("<storng>HELLO</strong>");
```

replaceAll()是颠倒replaceWith()的操作

#### 7.包裹节点

使用wrap()方法将匹配的元素节点用指定的元素节点单独包裹起来：

```
$("ul").wrap("<div></div>");		//使用<div>标签将<ul>标签包裹起来
```

另外还有wrapAll()方法，将匹配的所有元素使用指定的一个元素包裹起来；

wrapInner()方法，将匹配的元素的子内容（包括文本节点、元素节点）用其他标签包裹起来

#### 8.属性操作

##### 8.1 获取和设置属性

使用attr(value,data)方法获取属性和设置属性，当只获取获取属性时，value值为属性名称，加上data值为设置该属性：

```
var $para = $("p");
$para.attr("title","your title");		//获取title属性的值并设置为"your title"
```

##### 8.2 删除属性

使用removeAttr()方法删除指定元素的某个特定属性：

```
$("p").removeAttr("title");		//删除p标签的title属性
```

#### 9.样式操作

##### 9.1 获取和设置样式

使用attr()方法获取样式class，也可以进行替换：

```
var p_class = $("p").attr("class");		//获取p标签的class
$("p").attr("class","high");		//将p标签的class替换为high
```

##### 9.2 追加样式

使用addClass()方法追加样式，此方法不同于attr(),不会将原有样式替换掉

##### 9.3 移除样式

使用removeClass()方法删除样式，不带参数时默认删除所有样式，删除多个样式时使用空格隔开：

```
$("p").removeClass("high another");		//删除class为high和another的样式
```

##### 9.4 切换样式

使用toggleClass()方法控制样式的重复切换，类名存在则删除，不存在则添加：

```
$("p").toggleClass("another");		//重复切换类名“another”
```

##### 9.5判断是否含有某个类

使用hasClass()方法判断是否含有某个class，有则返回true，否则返回false:

```
$("p").hasClass("another");		//判断p元素是否含有another类
```

#### 10.设置和获取HTML、文本和值

##### 10.1 html()方法

类似于javascript中的innerHTML()方法：

```
var p_html = $("p").html();		//获取p元素的html代码
alert(p_html);		//打印：<p></p>
$("p").html("<strong>设置p标签里的值</strong>");		//设p标签的html代码
```

##### 10.2 text()方法

类似于javascript中的innerText()方法，可用来读取或设置某个元素中的文本内容：

```
var p_text = $("p").text();		//获取p元素的文本内容
alert(p_text);		//打印<p>元素内的文本内容
$("p").text("<strong>设置p标签里的文本内容</strong>");		//设p标签的文本内容
```

##### 10.3 val()方法

类似于javascript中的value属性，可用来获取或设置元素的值

#### 11.遍历节点

##### 11.1 children()方法

此方法用于取得匹配元素的子元素集合，只考虑子元素而不考虑任何后代元素

##### 11.2 next()方法

此方法用于获取匹配元素后面紧邻的同辈元素

##### 11.3 prev()方法

此方法用于获取匹配元素前面紧邻的同辈元素

##### 11.4 siblings()方法

此方法用于获取匹配元素前后所有紧邻的同辈元素

##### 11.5 closet()方法

此方法用来取得最近的匹配元素，先检查元素是否匹配，匹配则返回元素本身，不匹配则向上查询父辈元素，真么都没找到则返回空的jQuery对象：

```
$(document)。bind("click",function(3){
	$(e.target).closet("li").css("color","red");
})
```

#### 12.CSS-DOM操作

##### 12.1.可以直接利用css()方法获取或设置元素的样式属性：

```
$("p").css("color","red");
```

可同时设置多个样式：

```
$("p").css({
"fontSize":"30px",
"color":"red"
});
```

在css()方法中，属性带有"-"的属性，可以不带引号，或者使用驼峰命名法再加引号

##### 12.2.其他常用方法

###### 12.2.1 offset()方法

获取元素在当前视窗的相对偏移，返回的对象包括top和left，只对可见元素有效：

```
var offset = $("p").offset();
var left = offset.left;
var top = offset.top;
```

12.2.2 position()方法

获取元素相对于最近一个position样式属性为relative或absolute的祖父节点的相对偏移

```
var position = $("p").position();
var left = position.left;
var top = position.top;
```

12.2.3 scrollTop()方法和scrollLeft()方法

分别获取元素的滚动条距顶端的距离和距左端的距离

```
var $p = $("p");
var scrollTop = $p.scrollTop();
var scrollLeft() = $p.scrollLeft();
```

当指定参数是，为控制滚动条滚动到指定位置：

```
$("p").scrollTop(300);
$("p").scrollLeft(300);
```

