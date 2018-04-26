# 参考资料

1. [基本样式和字体样式](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals)
3. [css介绍一直到css选择器,跳过拟类选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Introduction_to_CSS)

# 基础问答

完成以上学习并进行以下问答:


1. 什么是CSS?浏览器是如何处理
HTML和CSS的,是浏览器能够显示文档?

2. DOM是什么?
3. 通过什么能将CSS应用到HTML中呢?对每一种方式每一步详细说明.
4. 可以用`//`来进行注释吗?
5. CSS属性是不区分大小写的,上述说法是否正确?
6. 对于CSS中的语句,是不是必须加`;`?详细说明情况.
7. CSS语句块可以嵌套吗?该怎么嵌套,回忆有哪些例子.(提示:`@-规则`的用法)
8. `background`怎么简写属性?将每个属性的实际说出来.

答: 
```
background: red url(bg-graphic.png) 10px 10px repeat-x fixed;
```
代表了:
```
background-color: red;
background-image: url(bg-graphic.png);
background-position: 10px 10px;
background-repeat: repeat-x;
background-scroll: fixed;
```

9. 文字的样式主要分为两种,字体样式和字体布局风格,分别说出字体样式包含哪些常用的属性,字体布局风格呢?分别详细说明每个属性的用法和注意事项.尤其注意:`font-family` 和`font-size`

10. 何时使用em和rem,以及px?html根标签默认的字体大小是多少px?

# 实践环节
1. 完成百度前端学院第三天任务[任务链接](http://ife.baidu.com/course/detail/id/37)
2. 在这个积极的学习中，我们希望您尝试添加属性选择器到一些规则来创建一个简单的足球结果列表。 这里有三件事要做：
前三个规则分别在列表项的左侧添加英国，德国和西班牙国旗图标。 您需要填写适当的属性选择器，以便团队获得正确的国家标志，并配合语言。
规则4-6在列表项中添加背景颜色，以指示球队是否已经在联盟中升格（绿色，rgba（0,255,0,0.7）），向下（红色，rgba（255,0,0,0.5）） ），或者留在同一个地方（蓝色，rgba（0,0,255,0.5））。填写适当的属性选择器，以将正确的颜色与正确的队列匹配，并与inc，相同和dec字符串匹配 data-perf属性值。
规则7-8使得晋级的球队变得加粗，有降级危险的球队为斜体和灰色。 填写适当的属性选择器，将这些样式与正确的队列进行匹配，并与data-perf属性值中显示的pro和rel字符串进行匹配。

HTML:
```
<ol>
  <li lang="en-GB" data-perf="inc-pro">Manchester United</li>
  <li lang="es" data-perf="same-pro">Barcelona</li>
  <li lang="de" data-perf="dec">Bayern Munich</li>
  <li lang="es" data-perf="same">Real Madrid</li>
  <li lang="de" data-perf="inc-rel">Borussia Dortmund</li>
  <li lang="en-GB" data-perf="dec-rel">Southampton FC</li>
</ol>
```


CSS:
```
li[] {
   background: url("http://mdn.github.io/learning-area/css/introduction-to-css/css-selectors/en-GB.png") 5px center no-repeat;
 }

li[] {
   background: url("http://mdn.github.io/learning-area/css/introduction-to-css/css-selectors/de.png") 5px center no-repeat;
 }

li[] {
   background: url("http://mdn.github.io/learning-area/css/introduction-to-css/css-selectors/es.png") 5px center no-repeat;
 }

li[] {
   background-color: rgba(0,255,0,0.7);
 }

li[] {
   background-color: rgba(0,0,255,0.5);
 }

li[] {
   background-color: rgba(255,0,0,0.7);
 }

li[] {
   font-weight: bold;
 }

li[] {
   font-style: italic;
   color: #666;
 }

ol {
   padding: 0;
 }

li {
   padding: 3px 3px 3px 34px;
   margin-bottom: 5px;
   list-style-position: inside;
 }
```

答:　[答案及效果](https://codepen.io/try1best/pen/wjzWjQ)

# 关于实践环节的一些问题.
1, 百度前端学院如何实现一个如图的效果下图的效果:
![](https://upload-images.jianshu.io/upload_images/271046-59351d8c645ca9e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 分析上面的图最上方为何有一段距离的原因,如何去掉?(在padding和margin都设为0的情况下)

.打开调试工具可以看到,就是h1这个标签的有了margin属性,margin属性是不可继承的.详细了解css的继承性.
[哪些可以继承,哪些不可以继承](https://www.cnblogs.com/thislbq/p/5882105.html)
[继承深度剖析](https://www.cnblogs.com/Chen-XiaoJun/p/6213173.html)
