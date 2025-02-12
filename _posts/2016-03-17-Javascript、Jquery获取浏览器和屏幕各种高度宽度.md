---
layout:     post
title:      

subtitle:   Javascript、Jquery获取浏览器和屏幕各种高度宽度
date:       2016-03-17
author:     BY
header-img: img/post-bg-debug.png
catalog: true
tags:
    - Dom
---

# 前言

 很多场景都需要用到获取浏览器和屏幕各种高度宽度，总结如下。

# 正文
#### 图解如下
![](https://thumbnail0.baidupcs.com/thumbnail/6ed98c9023570cff29e2ed78f6fb9312?fid=3198699892-250528-190949000193907&time=1572487200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-qGTiX3KiLOOsJm0A9U92uguoYHw%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=119610340541850792&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video)
	
#### Javascript:

###### IE中：
document.body.clientWidth ==> BODY对象宽度

document.body.clientHeight ==> BODY对象高度

document.documentElement.clientWidth ==> 可见区域宽度

document.documentElement.clientHeight ==> 可见区域高度

###### FireFox中：
document.body.clientWidth ==> BODY对象宽度

document.body.clientHeight ==> BODY对象高度

document.documentElement.clientWidth ==> 可见区域宽度

document.documentElement.clientHeight ==> 可见区域高度

###### Opera中：
document.body.clientWidth ==> 可见区域宽度

document.body.clientHeight ==> 可见区域高度

document.documentElement.clientWidth ==> 页面对象宽度（即BODY对象宽度加上Margin宽）

document.documentElement.clientHeight ==> 页面对象高度（即BODY对象高度加上Margin高）

 

 

alert(document.body.clientWidth);        //网页可见区域宽(body)

alert(document.body.clientHeight);       //网页可见区域高(body)

alert(document.body.offsetWidth);       //网页可见区域宽(body)，包括border、margin等

alert(document.body.offsetHeight);      //网页可见区域宽(body)，包括border、margin等

alert(document.body.scrollWidth);        //网页正文全文宽，包括有滚动条时的未见区域

alert(document.body.scrollHeight);       //网页正文全文高，包括有滚动条时的未见区域

alert(document.body.scrollTop);           //网页被卷去的Top(滚动条)

alert(document.body.scrollLeft);           //网页被卷去的Left(滚动条)

alert(window.screenTop);                     //浏览器距离Top

alert(window.screenLeft);                     //浏览器距离Left

alert(window.screen.height);                //屏幕分辨率的高

alert(window.screen.width);                 //屏幕分辨率的宽

alert(window.screen.availHeight);          //屏幕可用工作区的高

alert(window.screen.availWidth);           //屏幕可用工作区的宽


#### Jquery

alert($(window).height());                           //浏览器当前窗口可视区域高度

alert($(document).height());                        //浏览器当前窗口文档的高度

alert($(document.body).height());                //浏览器当前窗口文档body的高度

alert($(document.body).outerHeight(true));  //浏览器当前窗口文档body的总高度 包括border padding margin

alert($(window).width());                            //浏览器当前窗口可视区域宽度

alert($(document).width());                        //浏览器当前窗口文档对象宽度

alert($(document.body).width());                //浏览器当前窗口文档body的宽度

alert($(document.body).outerWidth(true));  //浏览器当前窗口文档body的总宽度 包括border padding margin
	
#### 示例代码：
```html
<!DOCTYPE html>
<html>
	<head>
		<title>aaa</title>
	</head>
	<body>
		<h1>
			aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
		</h1>
		<p>Welcome to aaa</p>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<h1>aaa</h1>
		<script type="text/javascript">
			alert(document.body.clientWidth);
			alert(document.body.clientHeight);
			alert(document.body.offsetWidth);
			alert(document.body.offsetHeight);

			alert(document.body.scrollWidth);
			alert(document.body.scrollHeight);

			alert(document.body.scrollTop);
			alert(document.body.scrollLeft);
			alert(window.screenTop);
			alert(window.screenLeft);
			alert(window.screen.height);
			alert(window.screen.width);
			alert(window.screen.availHeight);
			alert(window.screen.availWidth);
		</script>
	</body>
</html>
```

	
		
