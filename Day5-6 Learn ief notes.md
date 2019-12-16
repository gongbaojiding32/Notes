# 16th Dec Learn ief day5-6 notes

**课程目标：**
**1.盒模型的概念**
**2.inline、block和inline-block的概念**
**3.内外边距，宽度，高度，box-sizing等属性**
**4.浮动，清除浮动**
**5.如何使用浮动进行布局**

---

***1.盒模型的概念***
**答：![box](https://www.w3school.com.cn/i/ct_boxmodel.gif "盒模型")**
**盒子的宽度 = margin-left + border-left + padding-left +width + padding-right + border-right + margin-right**
**1.1 内容区**
width和height是框内容显示的区域——包括框内的文本内容，以及表示嵌套子元素的其他框也可以使用min-width、max-width、min-height、max-height来设置最低/最高限度的width和height
默认情况下，width和height只包括内容区域的宽和高，不包括border、padding、margin。使用box-sizing可以使其包含content、padding、border**
**box-sizing的值:**
/* 默认值，标准盒子模型，只含内容区 */ 
box-sizing:content-box;
/* width 和 height 属性包括内容，内边距和边框，但不包括外边距 */ 
box-sizing:border-box;
**1.2 内边距**
padding

**1.3 边框**
border 详见day4的笔记

**1.4 外边框**
margin

外边距塌陷: 块级元素的上外边距和下外边距有时会合并（或折叠）为一个外边距，其大小取其中的最大者

相邻兄弟元素margin合并
父级和第一个/最后一个子元素
空块级元素的margin合并
**1.5 注意点**
框的高度不能使用百分比长度
border不能使用百分比长度
如果内容区过大，将会溢出，此时可使用overflow
**overflow的值:**

```css
/* 默认值。内容不会被修剪，会呈现在元素框之外  */
overflow: visible;
/* 内容会被修剪，并且其余内容不可见  */
overflow: hidden;
/* 内容会被修剪，浏览器会显示滚动条以便查看其余内容  */
overflow: scroll;
/* 由浏览器定夺，如果内容被修剪，就会显示滚动条  */
overflow: auto;
```

**display**
|值|说明|
|:------|:-------|
|block|	块框（ block box）是定义为堆放在其他框上的框（例如：其内容会独占一行），而且可以设置它的宽高，之前所有对于框模型的应用适用于块框 （ block box）|
|inline|	行内框（ inline box）与块框是相反的，它随着文档的文字（例如：它将会和周围的文字和其他行内元素出现在同一行，而且它的内容会像一段中的文字一样随着文字部分的流动而打乱），对行内盒设置宽高无效，设置padding, margin 和 border都会更新周围文字的位置，但是对于周围的的块框（ block box）不会有影响。|
|inline-block|	行内块状框（inline-block box） 像是上述两种的集合：它不会重新另起一行但会像行内框（ inline box）一样随着周围文字而流动，而且他能够设置宽高，并且像块框一样保持了其块特性的完整性，它不会在段落行中断开。|
|table|像处理table布局那样处理非table元素，而不是滥用HTML的table;标签来达到同样的目的。|
|flex|处理一些困扰CSS已久的一些传统布局问题，例如布置一系列弹性等宽容器或者垂直居中内容。|
|grid|给出一种简单实现CSS网格系统的方式，而在传统上它依赖于一些棘手难以处理的CSS网格框架|

---

***4.浮动，清除浮动***
**答：**
|值	|描述|
|-----|:------|
|left|	元素向左浮动。|
|right|	元素向右浮动。|
|none|	默认值。元素不浮动，并会显示在其在文本中出现的位置。|
|inherit|	规定应该从父元素继承 float 属性的值。|

**clear属性**
图像的左侧和右侧均不允许出现浮动元素：

```css
img
  {
  float:left;
  clear:both;
  }
```

***5.如何使用浮动进行布局***
浮动是将该块元素从原来的文档流模式中分离出来，它后面的对象，就视它不存在，从而占领它的位置。
常用的布局效果，例如，在一行中，显示几个块元素，就全部元素都用float（用flex或者grid就来得非常简单）。
注意：
    1、浮动到的位置是它的父元素的位置，如：在li标签中使用float，则浮动到的位置是ul的位置；
    2、在IE6下，当父元素中的子元素的高度超过了父元素的高度，则子元素会把父元素的高度撑大到子元素的高度。
float属性的属性值：
    1、none  //不浮动
    2、left  //元素向左浮动，而后面的内容流向对象的右侧
    3、right  //对象向右浮动，而后面的内容流向对象的左侧

