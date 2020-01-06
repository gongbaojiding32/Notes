## SVG 基础

**SVG是使用XML来描述二维图形和绘图程序的语言**
- SVG指可伸缩矢量图形(Scable Vecotr Graphics)
- SVG用来定义用于网络的基于矢量的图形
- SVG使用XML格式定义图形
- SVG图像在放大或改变尺寸的情况下其图形质量不会有损失
- SVG是万维网的标准
- SVG与诸如DOM、XSL之类的W3C标准是一个整体

**SVG实例**

```svg
<?xml version="1.0" standalone="no"?>

<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<circle cx="100" cy="50" r="40" stroke="black"
stroke-width="2" fill="red"/>

</svg>
```

**standalone属性规定此SVG文件是否是"独立的"，或者有对外部文件的引用。standalone="no" 意味着 SVG 文档会引用一个外部文件 - 在这里，是 DTD 文件。第二和第三行引用了这个外部的 SVG DTD。该 DTD 位于 “http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd”。该 DTD 位于 W3C，含有所有允许的 SVG 元素。**
**SVG代码以`<svg>`元素开始，包括开启标签`<svg>`和关闭标签`</svg>`,width和height属性设置SVG稳当的宽度和高度,version属性定义所使用的SVG版本，xmlns属性可定义SVG命名空间**
**`<circle>`用来创建一个圆，cx和cy属性定义圆中心的x和y坐标，若忽略这两个属性，圆点会被设置为(0,0),r属性定义圆的半径。stroke和stroke-width属性控制如何显示形状的轮廓，fill属性设置形状内的颜色**
**所有开启标签必须有关闭标签**

**SVG in HTML**
**SVG标签可通过以下标签嵌入HTML文档`<embed>`,`<object>`,`<iframe>`**

**使用`<embed>`标签**
**所有主流浏览器支持，并允许使用脚本**
**在HTML页面中嵌入SVG时使用`<embed>`标签是Adobe SVG Viewer推荐的方法，如果需要创建合法的XHTML,就不能使用`<embed>`，任何HTML规范中都没有`<embed>`标签

```js embed
<embed src="rect.svg" width="300" height="100"
type="image/svg+xml"
pluginspage='http://www.adobe.com/svg/viewer/install/"/>
//pluginspage属性指向下载插件的URL
```

**使用`<object>`标签**
**`<object>`标签是HTML4的标准标签，被所有较新的浏览器支持，缺点是不支持脚本**
**假如安装了最新版本的Adobe SVG Viewer,那么当使用`<object>`标签时SVG文件无法工作(至少不能再IE中工作)**

```js object
<object data="rect.svg width="300 height="100"
type="img/svg+xml"
codebase="http://www.adobe.com/svg/viewer/install/"/>
//codebase属性指向下载插件的URL
```

**使用`<iframe>`标签,可工作在大部分的浏览器中**

```js iframe
<iframe src="rect.svg" width="300 height="100">
</iframe>
```

--- 

## SVG形状

**SVG形状**
- 矩形`<rect>`
- 原型`<circle>`
- 椭圆`<ellipse>`
- 线`<line>`
- 折线`<polyline>`
- 多边形`<polygon>`
- 路径`<path>`

**`<rect>`标签 用来创建矩形，以及矩形的变种**

```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect width="300" height="100"
style="fill:rgb(0,0,255);stroke-width:1;
stroke:rgb(0,0,0)"/>

</svg>
```

**代码解释**
- rect元素的width和height属性可定义矩形的宽度和高度
- style属性定义CSS属性
- CSS的fill属性定义矩形的填充颜色(rgb值，颜色名或者十六进制值)
- CSS的stroke-width属性定义矩形边框的宽度
- CSS的stroke属性定义矩形边框的颜色

```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" width="250" height="250"
style="fill:blue;stroke:pink;stroke-width:5;
fill-opacity:0.1;stroke-opacity:0.9"/>

</svg>
```
- x 属性定义矩形的左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px）
- y 属性定义矩形的顶端位置（例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px）
- CSS 的 fill-opacity 属性定义填充颜色透明度（合法的范围是：0 - 1）
- CSS 的 stroke-opacity 属性定义笔触颜色的透明度（合法的范围是：0 - 1）

**为整个元素定义透明度**
```svg 
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" width="250" height="250"
style="fill:blue;stroke:pink;stroke-width:5;
opacity:0.9"/>

</svg>
```
**CSS的opacity属性定义整个元素的透明值(盒饭的范围是：0-1)

**创建带有圆角的矩形**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" rx="20" ry="20" width="250"
height="100" style="fill:red;stroke:black;
stroke-width:5;opacity:0.5"/>

</svg>
```
**rx和ry属性可以使矩形产生圆角**

**SVG 圆形**
**`<circle>`标签创建一个圆**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<circle cx="100" cy="50" r="40" stroke="black"
stroke-width="2" fill="red"/>

</svg>
```
**cx和cy属性定义圆点的x和y坐标，省略圆的中心设置为(0,0),r属性定义圆的半径**


**SVG 椭圆**
**`<ellipse>`标签用来创建椭圆，椭圆有不同的x和y的半径，圆的x和y的半径是相同的**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<ellipse cx="300" cy="150" rx="200" ry="80"
style="fill:rgb(200,100,50);
stroke:rgb(0,0,100);stroke-width:2"/>

</svg>
```
- cx属性定义原点的x坐标
- cy属性定义原点的y坐标
- rx属性定义水平半径
- ry属性定义垂直半径


**SVG 线条**
**`<line>`标签用来创建线条**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<line x1="0" y1="0" x2="300" y2="300"
style="stroke:rgb(99,99,99);stroke-width:2"/>

</svg>
```
- x1属性在x轴定义线条的开始
- y1属性在y轴定义线条的开始
- x2属性在x轴定义线条的结束
- y2属性在y轴定义线条的结束


**SVG 多边形**
**`<polygon>`标签用来创建含有不少于三个边的图形**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polygon points="220,100 300,210 170,250"
style="fill:#cccccc;
stroke:#000000;stroke-width:1"/>

</svg>
```
**points属性定义多边形每个角的x和y坐标**


**SVG 折线**
**`<polyline>`标签创建仅包含直线的形状**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polyline points="0,0 0,20 20,20 20,40 40,40 40,60"
style="fill:white;stroke:red;stroke-width:2"/>

</svg>
```

**SVG 路径**
**`<path>`标签用来定义路径**
**下面命令可用于路径数据**
- M = moveto
- L = lineto
- H = horizontal lineto
- V = vertical lineto
- C = curveto
- S = smooth curveto
- Q = quadratic Belzier cuve
- T = smooth quadratic Belzier curveto
- A = elliptical Arc
- Z = closepath
**以上命令允许小写字母，大写表示绝对定位，小写表示相对定位**

---

## SVG 滤镜
**在SVG中，可用的滤镜有：**
- feBlend
- feColorMatrix
- feComponentTransfer
- feComposite
- feConvolveMatrix
- feDiffuseLighting
- feDisplacementMap
- feFlood
- feGaussianBlur
- feImage
- feMerge
- feMorphology
- feOffset
- feSpecularLighting
- feTile
- feTurbulence
- feDistantLight
- fePointLight
- feSpotLight


**SVG 高斯滤镜**
**SVG 高斯模糊**
**必须在`<defs>`标签中定义SVG滤镜**
**高斯模糊**
**`<filter>`标签用来定义SVG滤镜,`<filter>`标签必须嵌套在`<defs>`标签内，`<defs>`标签是definitions的缩写**
```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<filter id="Gaussian_Blur">
<feGaussianBlur in="SourceGraphic" stdDeviation="3" />
</filter>
</defs>

<ellipse cx="200" cy="150" rx="70" ry="40"
style="fill:#ff0000;stroke:#000000;
stroke-width:2;filter:url(#Gaussian_Blur)"/>

</svg>
```
- `<filter>` 标签的 id 属性可为滤镜定义一个唯一的名称（同一滤镜可被文档中的多个元素使用）
- filter:url 属性用来把元素链接到滤镜。当链接滤镜 id 时，必须使用 # 字符
- 滤镜效果是通过 `<feGaussianBlur>` 标签进行定义的。fe 后缀可用于所有的滤镜
- `<feGaussianBlur>` 标签的 stdDeviation 属性可定义模糊的程度
- in="SourceGraphic" 这个部分定义了由整个图像创建效果

---

## SVG 渐变

**SVG 线性渐变**
**渐变是一种颜色到另一种颜色的平滑过渡，另外，可以把多个颜色的过渡应用在同一个元素上**
**在SVG中，有两种主要的渐变类型**
- 线性渐变
- 放射性渐变

**线性渐变**
**`<linearGradient>`用来定义线性渐变，必须嵌套在`<defs>`内部，`<defs>`标签是definitions的缩写，对诸如渐变之类的特殊元素进行定义**
**线性渐变可被定义为水平、垂直或角行的渐变**
- 当y1和x2相等，而x1和x2不同时，可创建水平渐变
- 当x1和x2相等，而y1和y2不同时，可创建垂直渐变
- 当x1和x2不同，而x1和x2不同时，可创建角形渐变

```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">
<stop offset="0%" style="stop-color:rgb(255,255,0);
stop-opacity:1"/>
<stop offset="100%" style="stop-color:rgb(255,0,0);
stop-opacity:1"/>
</linearGradient>
</defs>

<ellipse cx="200" cy="190" rx="85" ry="55"
style="fill:url(#orange_red)"/>

</svg>
```

- `<linearGradient>` 标签的 id 属性可为渐变定义一个唯一的名称
- fill:url(#orange_red) 属性把 ellipse 元素链接到此渐变
- `<linearGradient>` 标签的 x1、x2、y1、y2 属性可定义渐变的开始和结束位置
- 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 `<stop>` 标签来规定。offset 属性用来定义渐变的开始和结束位置。


**SVG 放射性渐变**
**`<radialGradient>`标签必须嵌套在`<defs>`中**

```svg
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<radialGradient id="grey_blue" cx="50%" cy="50%" r="50%"
fx="50%" fy="50%">
<stop offset="0%" style="stop-color:rgb(200,200,200);
stop-opacity:0"/>
<stop offset="100%" style="stop-color:rgb(0,0,255);
stop-opacity:1"/>
</radialGradient>
</defs>

<ellipse cx="230" cy="200" rx="110" ry="100"
style="fill:url(#grey_blue)"/>

</svg>
```
**`<radialGradient>` 标签的 id 属性可为渐变定义一个唯一的名称，fill:url(#grey_blue) 属性把 ellipse 元素链接到此渐变，cx、cy 和 r 属性定义外圈，而 fx 和 fy 定义内圈 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 `<stop>`标签来规定。offset 属性用来定义渐变的开始和结束位置。**


---

## SVG 元素
**SVG 元素**
|元素|描述|
|-------|:-------|
|a	|定义超链接|
|altGlyph|	允许对象性文字进行控制，来呈现特殊的字符数据（例如，音乐符号或亚洲的文字）|
|altGlyphDef|	定义一系列象性符号的替换（例如，音乐符号或者亚洲文字）|
|altGlyphItem	|定义一系列候选的象性符号的替换|
|animate|	随时间动态改变属性|
|animateColor|	规定随时间进行的颜色转换|
|animateMotion|	使元素沿着动作路径移动|
|animateTransform|	对元素进行动态的属性转换|
|circle|	定义圆|
|clipPath| 
|color-profile|	规定颜色配置描述|
|cursor|	定义独立于平台的光标|
|definition-src|	定义单独的字体定义源|
|defs|	被引用元素的容器|
|desc|	对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示。|
|ellipse|	定义椭圆|
|feBlend|	SVG 滤镜。使用不同的混合模式把两个对象合成在一起。|
|feColorMatrix|	SVG 滤镜。应用matrix转换。|
|feComponentTransfer|	SVG 滤镜。执行数据的 component-wise 重映射。|
|feComposite|	SVG 滤镜。|
|feConvolveMatrix|	SVG 滤镜。|
|feDiffuseLighting|	SVG 滤镜。|
|feDisplacementMap|	SVG 滤镜。|
|feDistantLight|	SVG 滤镜。 Defines a light source|
|feFlood| SVG 滤镜。|
|feFuncA |SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncB|	SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncG|	SVG 滤镜。feComponentTransfer 的子元素。|
|feFuncR|	SVG 滤镜。feComponentTransfer 的子元素。|
|feGaussianBlur|	SVG 滤镜。对图像执行高斯模糊。|
|feImage|	SVG 滤镜。|
|feMerge|	SVG 滤镜。创建累积而上的图像。|
|feMergeNode|	SVG 滤镜。feMerge的子元素。|
|feMorphology|	SVG 滤镜。 对源图形执行"fattening" 或者 "thinning"。|
|feOffset	|SVG 滤镜。相对与图形的当前位置来移动图像。|
|fePointLight	|SVG 滤镜。|
|feSpecularLighting|	SVG 滤镜。|
|feSpotLight|	SVG 滤镜。|
|feTile	|SVG 滤镜。|
|feTurbulence|	SVG 滤镜。|
|filter| 滤镜效果的容器。|
|font |定义字体。|
|font-face|	描述某字体的特点。|
|font-face-format|	 
|font-face-name	| 
|font-face-src	 |
|font-face-uri	| 
|foreignObject	| 
|g|	用于把相关元素进行组合的容器元素。|
|glyph|	为给定的象形符号定义图形。|
|glyphRef|定义要使用的可能的象形符号。|
|hkern|	 
|image	 
|line|	定义线条。|
|linearGradient	|定义线性渐变。|
|marker	 |
|mask|	 
|metadata|	规定元数据。|
|missing-glyph	 |
|mpath|	 
|path|	定义路径。|
|pattern|	 
|polygon|	定义由一系列连接的直线组成的封闭形状。|
|polyline|	定义一系列连接的直线。|
|radialGradient	|定义放射形的渐变。|
|rect|	定义矩形。|
|script|	脚本容器。（例如ECMAScript）|
|set|	为指定持续时间的属性设置值|
|stop|	 
|style|	可使样式表直接嵌入SVG内容内部。|
|svg|	定义SVG文档片断。|
|switch|	 
|symbol	|
|text|	 
|textPath|	 
|title|	对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示。|
|tref	| 
|tspan|	 
|use	|
|view	 
|vkern	| 
