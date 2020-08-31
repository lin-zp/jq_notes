#### 引入jquery库

```
在<head></heaad>标签内引入<script src="../jq库路径"></script>
如：
<head>
<script src="../scripts/jquery.js" type="text/javascript"></script>
</head>
```

#### 程序的开始

jq程序在dom元素加载完成后才开始，使用$(document).ready()方法，程序在$(document).ready(function(){})中编写，可以简写为$(function(){})，与Javascript中的window.onload()方法类似

![image-20200831114451232](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831114451232.png)

#### Jquery对象和DOM对象的转换

##### 对象定义-jq对象

```
var $variable = jq对象
```

对象定义-DOM对象

```
var variable = DOM对象
```

##### 1.jquery对象转换为DOM对象

j对象与d对象的方法不可以通用，j对象是一个伪数组，可使用[index]或get(index)将j对象转化为d对象

(1)[index]方法(数组方法)

```
var $cr = $s("#cr")		//j对象
var cr = $cr[0]			//d对象
alert(cr.checked)		//检测是否被选中
```

(2)get(index)方法(j对象方法)

```
var $cr = $s("#cr")		//j对象
var cr = $cr.get(0)			//d对象
alert(cr.checked)		//检测是否被选中
```

##### 2.DOM对象转换为jquery对象

使用$()将dom对象包起来可以转化为jquery对象

```
var cr = document.getElementbyId("cr")
var $cr = $(cr)
```

#### JQuery库冲突

##### 1.在其他库后导入jquery库

可在任何时候使用 jQuery.noConflict() 函数将$控制权释放

![image-20200831200439400](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831200439400.png)

![image-20200831200453374](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831200453374.png)

也可使用jquery.noConflict()自定义快捷方式：

```
var $L = jQuery.noConflict();		//自定义快捷方式
$L(function(){						//使用jQuery库
	$L("p").click(function(){
		alert("$L(this).text");
	})
})
$("pp").style.display = "none";		//使用其他库
```

想使用$且不与其他库冲突：

1.使用jQuery设定页面加载是执行的函数

![image-20200831201126866](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831201126866.png)

2.定义立即执行的匿名函数，设置形参$与实参

![image-20200831201229464](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831201229464.png)

![image-20200831201244293](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831201244293.png)

##### 2.在其他库之前导入jQuery库

![image-20200831201331946](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200831201331946.png)