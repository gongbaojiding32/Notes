# 16th Dec Learn ief day4 notes

**课程目标：**
**1.背景，边框，列表，链接相关属性**
**2.CSS 各种选择器的概念，使用方法及使用场景**
**3.CSS 选择器的优先级**

---

***1.背景，边框，列表，链接相关属性***
**答：背景background**
| 属性 | 说明 |值|备注|
|:----|:---- |:---------:|:-------|
|background-color|背景色|		|建议加上，作为后备，以防背景图像无法加载|
|background-image|	背景图像|	url(...)、渐变: linear-gradient(to 渐变的方向,开始的颜色,结尾的颜色)|	渐变可以在中途选择其他的点|
|background-repeat|	背景重复|	|repeat(默认)、repeat-x、repeat-y、no-repeat|	|
|background-position|	背景定位|	关键字、百分数值、长度值|	坐标系为x坐标从左到右,y坐标从上到下;可以用于雪碧图|
|background-attachment|	背景附着	|scroll(默认)、fixed	|    |
|background-size|	背景图像大小|	长度值、百分数值、cover、contain|	|
|background|	背景简写|		|可按任意顺序放置|

**边框border**
| 属性 | 说明 |值|备注|
|:----|:---- |:---------:|:-------|
|border	边框简写|[border-width border-style border-color /inherit]|三角形和梯形可以使用border+transparent来做|
|border-style|边框样式|none、hidden、dotted、dashed、solid、double、(groove、ridge、inset、outset、)inherit|样式预览|
|border-width|边框宽度|	|不支持百分比、默认为medium(3px)|
|border-color|边框颜色|	透明:transparent|默认颜色同color|
|border-radius|边界圆角|  |  |

**列表list**
| 属性 | 说明 |值|备注|
|:----|:---- |:---------:|:-------|
|list-style-type|列表标志|标志值|	|
|list-style-image|列表项图像| url()|可用background代替|
|list-style-position|列表项位置|inside(文本内文本环绕)、outside(默认)、inherit|    |
|list-style|列表简写|	顺序:list-style-type list-style-position list-style-image(可省略某个值)|    |

**链接 a**

```css
a:link {color:#FF0000;}        /* 未被访问的链接 */
a:visited {color:#00FF00;}    /* 已被访问的链接 */
a:hover {color:#FF00FF;}    /* 鼠标指针移动到链接上 */
a:active {color:#0000FF;}    /* 正在被点击的链接 */
```

---

***2.CSS各种选择器的概念，使用方法及使用场景***
**答：**
1.标签选择器（如：body,div,p,ul,li） 

2.类选择器（如：class="head",class="head_logo"） 

3.ID选择器（如：id="name",id="name_txt"） 

4.全局选择器（如：*号） 

5.组合选择器（如：.head .head_logo,注意两选择器用空格键分开） 

6.继承选择器（如：div p,注意两选择器用空格键分开） 

7.伪类选择器（如：就是链接样式,a元素的伪类，4种不同的状态：link、visited、active、hover。） 

8.字符串匹配的属性选择符(^ $ *三种，分别对应开始、结尾、包含) 

在标签内写入style=" "的方式，应该是CSS的一种引入方式，而不是选择器，因为根本就没有用到选择器。 

我们分别来看下这些选择器： 

1：标签名选择器 

一个XHTML文档中有许多标签，例如p标签，h1标签等。若要使文档中的所有p标签都使用同一个CSS样式，就应使用标签选择器。 

复制代码
代码如下:

```CSS
div {color:red;border:1px blue solid;} 
p {color:#000;} 
```

2：类选择器 

使用标签选择器可以为整个XHTML文档中的同一个标签指定相同的CSS样式。但是在实际运用中，XHTML文档中的同一个标签会被反复使用。若要为相同的标签赋予不同的CSS样式就应使用类选择器。 

复制代码
代码如下:

```CSS
<div class="test">测试代码</div> 
.test {color:red;border:1px blue solid;} 
```

在html文档里，我们在要控制样式的标签的开标签（非成对标签如input直接放在标签里）里加入 class="xxx",在页面对应的css文件里，用.xxx就可以指向这个标签，从而对这个标签进行控制，我们称这种通过定义类（class）来找到标签的方式为 ：类选择器。 

这种定义class 的方式是前端开发最常用的选择器，有几个突出的特点：可以给不同的标签设置同一个类，从而用一条CSS命令控制几个标签，减少大量代码，是页面修改简单，易维护，易改版；其次，后台工作人员机会不会用到有关class的相关设置，不需要跟后台人员之间进行交互；再者，可以通过js等动态改变标签的Classname，从而改变整个标签的样式，使前端动态效果实现起来更为容易。 

3：ID选择器 

ID选择器和类选择器相似，不同的是，ID选择器不能复用。在一个XHTML文档中，一个ID选择器只能把其CSS样式指定给一个标签。 

复制代码
代码如下:

```CSS
<div id="test">测试代码</div> 
#test {color:red;border:1px blue solid;} 
```

有 ID 的 HTML元素可以被JavaScript来操纵.再就是ID也是后台开发人员会经常用的，所以前端开发人员应该尽量少的使用。 

4.全局选择器 

全局选择器是一个星号。它能作用于XHTML文档中的所有元素。 

复制代码
代码如下:

`*{margin:0; padding:0;} `

5.组合选择器 

标签选择器、类选择器和ID选择器是可以组合起来使用的。一般的组合方式是标签选择器和类选择器组合，标签选择器和ID选择器组合。由于这两种组合方式的原理和效果一样，所以只介绍标签选择器和类选择器的组合。组合选择器只是一种组合形式，并不算是一种真正的选择器，但在实际中经常使用。 

比如 `.orderlist li {xxxx} 或者 .tableset td {} `

我们使用的时候一般用在重复出现并且样式相同的一些标签里，比如 li td dd等。 

比如 `<h1 class="red"></h1> H1.red {color: red} `

群组选择器 

复制代码
代码如下:

```CSS
.test1,span,test2 {border:1px blue solid;} 
div,span,img {border:1px blue solid;} 
```

群组选择器实际上是对CSS的一种简化写法，只不过把有相同定义的不同选择器放在一起，省了很多代码。 

6.继承选择器 

学习使用继承选择器就必须先了解文档树和CSS的继承。每个XHTML都可以被看作一个文档树，文档树的根部就是html标签，而head和body标签就是其子元素。在head和body里的其他标签就是html标签的孙子元素。整个XHTML就呈现一种祖先和子孙的树状关系。CSS的继承是指子孙元素继承祖先元素的某些属性。以下通过实例来详细讲解这两个重要的CSS概念。 

文档树 CSS的继承 继承选择器 

复制代码
代码如下:

```CSS
<div class="test"> 
<span><img src="xxx" alt="示例图片"/></span> 
</div> 
.test span img {border:1px blue solid;} 
div span img {border:1px blue solid;} 
```

后代选择器实际上是使用：多个选择器加上中间的空格来找到具体的要控制标签；从左往右，依次细化，最后锁定要控制的标签，如上例，先找到class为test的标签，再从他的子标签里查找span标签，再从span的子标签中找到IMG标签。 

7.伪类选择器 

伪类也是选择器的一种，但是用伪类定义的CSS样式并不是作用在标签上的。伪类作用在标签的状态上。由于很多浏览器支持不同类型的伪类，没有一个统一的标准，所以很多伪类都不常被用到。伪类包括：:first-child、:link:、:visited、:hover、:active、:focus和:lang等等。其中有一组伪类是主流浏览器都支持的，就是超链接的伪类，包括:link:、:visited、:hover和:active。 

a的这四个伪类，分别表示了a的四种状态，要注意的是，a可以只具有一种状态（:link），或者同时具有2种或者三种状态！比如说，任何一个有HREF属性的a标签，在未有任何操作时都已经具备了:link的条件，也就是满足了有链接属性这个条件；如果访问过的a标签，同时会具备 :link :visited 两种状态。把鼠标移到访问过的a标签上 

8.字符串匹配的属性选择符--主要有三种 

语法：`E[att^="val"] ： {attribute} `
说明：匹配具有att属性、且值以val开头的E元素 

复制代码
代码如下:

```CSS
<span style="font-size:18px;"><style type="text/css"> 
p[title^="val"] {color:#FF0000;} 
</style> 
<body> 
<div style="width:733px; border: 1px solid #666; padding:5px;"> 
<p title="value">匹配具有att属性、且值以val开头的E元素</p> 
</div></span> 
```

语法:`E[att$="val"] ： {attribute} `
说明：匹配具有att属性、且值以val结尾的E元素 

复制代码
代码如下:

```CSS
<style type="text/css"> 
p[title$="val"] {font-weight:bold;} 
</style> 
<body> 
<div style="width:733px; border: 1px solid #666; padding:5px;"> 
<p title="this is val">匹配具有att属性、且值以val结尾的E元素</p> 
</div> 
</body>
``` 

语法:`E[att*="val"] ： {attribute} `
说明：匹配具有att属性、且值中包含val的E元素。 

复制代码
代码如下:

```CSS
<style type="text/css"> 
p[title*="val"] {text-decoration:underline;} 
</style> 
<title>子串匹配的属性选择符 E[att*="val"]</title> 
</head> 
<body> 
<div style="width:733px; border: 1px solid #666; padding:5px;"> 
<p title="have val word">匹配具有att属性、且值中含有val的E元素</p> 
</div> 
</body>
``` 


---

***3.CSS 选择器的优先级***
**答：!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性**