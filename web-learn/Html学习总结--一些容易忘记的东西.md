# HTML
1.  当显示页面时，浏览器会移除源代码中多余的空格和空行。所有连续的空格或空行都会
被算作一个空格。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为一个>
空格。

2. 折行是使用`<br />`来进行换行.
3. `a`链接元素是使用`href`属性,是指向的意思.`target="_blank"
通过`name`为锚命名,使用
```
<a href="#name">
```
 来直接定位到这里.对于其他文件也是在后面加上`#name`
4. `img`图片元素是使用`src`属性,意为图片的来源的意思.用`alt`来退换遗传预备的文本.

注释：`<img> `中的 `usemap `属性可引用 `<map> `中的` id `或 `name` 属性（由浏览器决定），所以我们需要同时向 <map> 添加 id 和 name 两个属性
`<map>`定义图像地图
`<area>`定义图像地图中的可点击区域,总是嵌套在map中.
注意看下面的代码:
```
<html>
<body>

<p>请点击图像上的星球，把它们放大。</p>

<img
src="/i/eg_planets.jpg"
border="0" usemap="#planetmap"
alt="Planets" />

<map name="planetmap" id="planetmap">

<area
shape="circle"
coords="180,139,14"
href ="/example/html/venus.html"
target ="_blank"
alt="Venus" />

<area
shape="circle"
coords="129,161,10"
href ="/example/html/mercur.html"
target ="_blank"
alt="Mercury" />

<area
shape="rect"
coords="0,0,110,260"
href ="/example/html/sun.html"
target ="_blank"
alt="Sun" />

</map>

<p><b>注释：</b>img 元素中的 "usemap" 属性引用 map 元素中的 "id" 或 "name" 属性（根据浏览器），所以我们同时向 map 元素添加了 "id" 和 "name" 属性。</p>

</body>
</html>

```
5. `<hr />`是水平线的意思.
6. `<p>`元素是块标签
7. `style`属性
![](https://upload-images.jianshu.io/upload_images/271046-4dbcd90f578cfd28.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`background-color属性,为元素定义了背景颜色.
`font-family`字体系列
`font-size`字体尺寸
`color`字体颜色

`text-align`文本对齐方式.如center.淘汰了旧的`align`属性.
8. 文本格式化的相关标签
```
<b>:bold粗体
<strong>:加粗
两者虽然在网页中显示效果一样，但实际目的不同。<b>这个标签对应 bold，即文本加粗，其目的仅仅是为了加粗显示文本，是一种样式／风格需求；<strong>这个标签意思是加强，表示该文本比较重要，提醒读者／终端注意。为了达到这个目的，浏览器等终端将其加粗显示；总结：<b>为了加粗而加粗，<strong>为了标明重点而加粗。
<big>放大
<i>无意义的斜体
<em>强调的斜体 类似的和上面的b/strong相同
<small>放小
<sub>下标
<sup>上标

```

9. `<pre>`标签是预格式文本,它保留了空格和换行,适合显示代码.

10. 计算机输出标签
![](https://upload-images.jianshu.io/upload_images/271046-b219f2a8c3f58993.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

注意: `code`元素不显示多余的空行和折行.
可以在code元素中嵌套pre元素
11. 地址标签 `<address>`
12. ![](https://upload-images.jianshu.io/upload_images/271046-6cc585c22709bf9a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

13. 
`<blockquote>`:长引用
`<q>`:短引用
使用` blockquote `元素的话，浏览器会插入换行和外边距，而 `q `元素浏览器会解析成`""`
14. 删除字和插入字效果
![](https://upload-images.jianshu.io/upload_images/271046-1b3fb842ba750d56.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

15.
 | [<abbr>](http://www.w3school.com.cn/tags/tag_abbr.asp) | 定义缩写。 |
| [<acronym>](http://www.w3school.com.cn/tags/tag_acronym.asp) | 定义首字母缩写。 |

另一个用于定义的HTML `<dfn>`
此标签可以自己定义`title`属性,
![](https://upload-images.jianshu.io/upload_images/271046-1b3ccf8b8e623299.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
也可以使用嵌套`abbr`标签,`abbr`标签内使用`title`属性.
![](https://upload-images.jianshu.io/upload_images/271046-c0cb4d17e234c94d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

16. 用于著作标题的 HTML `<cite>`,浏览器会以斜体显示`<cite>`元素'

17. HTML `<bdo>` 元素定义双流向覆盖（bi-directional override）。

`<bdo> `元素用于覆盖当前文本方向：
![](https://upload-images.jianshu.io/upload_images/271046-d776134dfb64b277.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

18. css外部样式表
```
<head>
<link rel = "stylesheet" type = "text/css" href="mystyle.css">
</head>
```
内部样式表:
```

<head>
<style type = "text/css">
...
</style>
</head>
```

19. 应该使用` %20` 来替换单词之间的空格，这样浏览器就可以正确地显示文本了。

20. `<table>`表格.`<tr>`行  `<td>`列 `<th>`表头  (都在tr标签内部使用) 使用`border`属性来显示边框.`<caption>`标题
`rowspan = "2"`两行合并.
`colspan = "2"`两列合并.
[点击观看实例](http://www.w3school.com.cn/tiy/t.asp?f=html_table_span)
`cellpadding`单元格边距
![](https://upload-images.jianshu.io/upload_images/271046-cf4d85f62f44253e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
`cellspacing`单元格间距
![](https://upload-images.jianshu.io/upload_images/271046-37ad5e1d952cb312.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`bgcolor = "red"` ![](https://upload-images.jianshu.io/upload_images/271046-3fb8b88f9eb9c2bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
`background = "/i.gif"`![](https://upload-images.jianshu.io/upload_images/271046-f5d7fdd8064244ee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
上面两个背景是在整个table中的,将这个属性加入到<td>标签里,会在单元格中显示出背景.
使用align属性可以排列位置`left`  `right`

`frame`属性:
![](https://upload-images.jianshu.io/upload_images/271046-de925ab6372aca9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

21.  ` &nbsp `空格占位符
22. 自定义列表
以`<dl>`标签开始,列表项以`<dt>`开始.列表项的定义以`<dd>`开始
![](https://upload-images.jianshu.io/upload_images/271046-8802928ef24678f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

有序列表`<ol>`,使用`type属性` type = "A" "a" "I" "i" 
无序列表`<ul>`,type = "disc" "circle" "square"
23. HTML5的新语义元素

header	定义文档或节的页眉
nav	定义导航链接的容器
section	定义文档中的节
article	定义独立的自包含文章
aside	定义内容之外的内容（比如侧栏）
footer	定义文档或节的页脚
details	定义额外的细节
summary	定义 details 元素的标题

24. 表单元素
`<form>`
包含`<input>`元素,根据不同的`type`属性,有很多形态. 如:`text`定义常规文本输入 `radio`定义单选按钮输入 `submit`定义提交按钮(提交表单)

详见这一节:[点击跳转-->](http://www.w3school.com.cn/html/html_forms.asp)

其中form表单有一个method属性，有Post Put Delete Get 方法，见此文章[点击](https://www.cnblogs.com/hyddd/archive/2009/03/31/1426026.html)

25. [meta标签](http://www.w3school.com.cn/tags/tag_meta.asp)
	[meta标签详解](https://blog.csdn.net/daydayup654/article/details/78666178)