# JavaScript
---

## JS三部分组成

**1. ECMAScript**
**2. DOM——文档对象类型**
**文档对象类型(Document Object Model 简称DOM), 是W3C组织推荐的处理可扩展标记语言的标准编程接口。通过DOM提供的接口可以对页面上的各种元素进行操作(大小、位置、颜色等)。**
**3. BOM——浏览器对象类型**
**BOM(Browser Object Model, 简称BOM)是指浏览器对象模型，它提供了独立于内容的、可以与浏览器窗口进行互动对象结构。通过BOM可以操作浏览器窗口，比如弹出框、控制浏览器跳转、获取分辨率等。**

---
**1. 行内式JS**

``` js
< input type = "button"
value = "项目点击完成"
onclick = "alert('形目已完成')>
```

**2. 内嵌式JS**

``` js
< script >
    alert('沙漠骆驼'); <
/script>
```

**3. 外部JS**

``` js
< script src = "文件名.js" > < /script>
```

---
**JS注释**
**1. 单行注释 //**
**2. 多行注释**
`/* */` 

`getElementById()` 是多个JavaScript方法之一

**JavaScript输入输出语句**
**为了方便信息的输入输出，JS中提供了一些输入输出语句，其中常用的语句如下**
|方法|说明|归属|
|-----|:-------:|:-------|
|alert(msg)|浏览器弹出警示框|浏览器|
|console.log(msg)|浏览器控制台输出信息|浏览器|
|prompt(info)|浏览器弹出输入框用户可以输入|浏览器|

**JavaScript显示方案**
**1. 使用window.alert()写入警告框**
**2.document.weote()写入HTML输出**
**3.innerHTML()写入HTML元素**
**4.console.log()写入浏览器控制台**

**JavaScript关键词**
|关键词|描述|
|------|:------|
|break|	终止 switch 或循环。|
|continue|	跳出循环并在顶端开始。|
|debugger|	停止执行 JavaScript，并调用调试函数（如果可用）。|
|do ... while|	执行语句块，并在条件为真时重复代码块。|
|for	|标记需被执行的语句块，只要条件为真。|
|function|	声明函数。|
|if ... else|	标记需被执行的语句块，根据某个条件。|
|return	|退出函数。|
|switch	|标记需被执行的语句块，根据不同的情况。|
|try ... catch|	对语句块实现错误处理。|
|var|	声明变量。|

---

## JavaScript语法

**JavaScript语句定义两种类型的值：混合值和变量值。**
**混合值被称为字节量(literal)。变量值被称为变量。**
**JavaScript字面量**
**书写混合值最重要的规则是：写数值有无小数点均可**
**字符串是文本，由双引号和单引号包围**
**JavaScript变量**
**在编程语言中，变量用于存储数据值。**
**JavaScript使用var关键词来声明变量。**
**=号用于为变量赋值。**

---
**JavaScript运算符**
**JavaScript使用运算符(+-*/)来计算值**
**JavaScript使用赋值运算符(=)向变量赋值**

---
**JavaScript标识符**
**JavaScript 中，首字符必须是字母、下划线（-）或美元符号（$）。**
**连串的字符可以是字母、数字、下划线或美元符号。**
**提示：数值不可以作为首字符。这样，JavaScript 就能轻松区分标识符和数值**

---
**JavaScript对大小写敏感**
**所有JavaScript标识符对大小写敏感。**
**变量lastName和lastname, 是两个不同的变量。**
**JavaScript程序员倾向于使用以小写字母开头的驼峰大小写**
`firstName,lastName,masterCard,interCity` 

---
**JavaScript字符集**
**JavaScript使用Unicode字符集。**

---
**JavaScript算术运算符**
|运算符|描述|
|-----|:-------|
|+ |加法|
|- |减法|
|* |乘法|
|/ |除法|
|% |系数|
|++|递加|
|--|递减|

---
**JavaScript赋值运算符**
|运算符|例子|等同于
|-----|:-------|:-----|
|=|  x = y| x = y|
|+=| x += y| x = x + y|
|-=| x -= y| x = x - y|
|*=| x *= y| x = x * y|
|/=| x /= y| x = x / y|
|%=| x %= y| x = x % y|
**加法赋值运算符（+=）向变量添加一个值。**

---
**JavaScript比较运算符**
|运算符|描述|
|-----|:-------|
|==| 等于|
|===| 等值等型|
|!=	| 不相等|
|!==| 不等值或不等型|
|>| 大于|
|<| 小于|
|>=| 大于或等于|
|<=| 小于或等于|
|?| 三元运算符|

---
**JavaScript逻辑运算符**
|运算符|描述|
|-----|:-------|
|&&| 逻辑与|
|两竖|逻辑或|
|!|逻辑非|

---
**JavaScript类型运算符**
|运算符|描述|
|-----|:-------|
|typeof| 返回变量的类型|
|instanceof| 返回true, 如果对象是对象类型的实例|

---
**JavaScript位运算符**
|运算符|描述|例子|等同于|结果|十进制|
|-----|:-------|:-------|:-----------|------|:-------|
|&|	与|	5 & 1	|0101 & 0001|	0001|	1|
|一竖|	或|	5 或(一竖) 1|	0101 或(一竖) 0001|	0101|	5|
|~|	非|	~ 5|	~0101|	1010|	10|
|^|	异或|	5 ^ 1|	0101 ^ 0001	|0100|	4|
|<<	|零填充左位移|	5 << 1|	0101 << 1|	1010|	10|
|>>|	有符号右位移|	5 >> 1|	0101 >> 1|	0010|	2|
|>>>|	零填充右位移|	5 >>> 1|	0101 >>> 1|	0010|	2|

---
**JavaScript算术运算符**
|运算符|描述|
|-----|:-------|
|+|	加法|
|-|	减法|
|*|	乘法|
|**	|幂（ES2016）|
|/|	除法|
|%|	系数|
|++| 递增|
|--| 递减|

---
**原始数据**
**typeof 运算符看返回以下原始类型之一：**
**1.string**
**1.number**
**1.boolean**
**1.undefined**

**复杂数据**
**typeof 运算符可返回以下两种类型之一：**
**1.function**
**2.object**
**typeof 运算符把对象、数组或null返回object**
**typeof 运算符不会把函数返回object**

---
**()运算符调用函数
**toCelsius引用的是函数对象，而toCelsius()引用的是函数结果。

---
**JavaScript对象**
**单一值(porsche)赋给名为car的变量**
`var car = "porsche";` 

**多个值(porsche, 911, white)赋给名为car的变量**
`var car ={type:"porsche",mode:"911",color:"white"};` 
**值以名称：值对的方式来书写(名称和值由冒号分隔)。**
**JavaScript对象是被命名值的容器。**

---

**常见的HTML事件**
|事件|描述|
|-------|:-------|
|onchange| HTML 元素已被改变|
|onclick| 用户点击了 HTML 元素|
|onmouseover| 用户把鼠标移动到 HTML 元素上|
|onmouseout| 用户把鼠标移开 HTML 元素|
|onkeydown| 用户按下键盘按键|
|onload| 浏览器已经完成页面加载|

---

## JS字符串

**特殊字符**
|代码|结果|描述
|-----|:-------|:-------|
|\'	|'|	单引号|
|\"	|"|	双引号|
|双反斜杠| 反斜杠|	反斜杠|

**其他六个JavaScript中有效的转义序列**
|代码|结果|
|-------|:--------|
|\b| 退格键|
|\f| 换页|
|\n| 新行|
|\r| 回车|
|\t| 水平制表符|
|\v| 垂直制表符|

---

**当使用==相等运算符时，相等字符串是相等的**
**当使用 === 运算符时，相等字符串是不相等的，因为 === 运算符需要类型和值同时相等。**
**请注意 `x==y` 与 ` x===y ` 的区别。**
**JavaScript 对象无法进行对比，比较两个 JavaScript 将始终返回 false。**

---

**JS字符串方法**

**1. 字符串长度：lenght属性返回字符串的长度**
**2. 查找字符串中的字符串**
** `indexOf()` 方法返回字符串中定文本首次出现的索引（位置）**
** `lastIndexOf()` 方法返回指定文本在字符串中最后一次出现的索引**
**若未找到文本， `indexOf()` 和 `lastIndexOf()` 均返回 -1。**
**JavaScript从零计算位置**
**检索字符串中的字符串**
** `search()` 方法搜索特定值的字符串，并返回匹配的位置**
**两种方法， `indexOf()` 与 `search()` 是相等的**
**这两种方法是不相等的，区别在于：**
** `search()` 方法无法设置第二个开始位置参数**
** `indexOf()` 无法设置更强大的搜索值(正则表达式)。**

**3. 提取部分字符串**
**1. `slice(start, end)` **
**2. `substring(start, end)` **
**`substr(start, length)`**

** `slice()` 方法，该方法设置两个参数：起始索引(开始位置)，终止索引(结束位置)。**
**如果某个参数为负，则从字符串的结尾开始计数。**
**如果省略第二个参数，则该方法将裁剪字符串的剩余部分**

**4. `substring()` 方法**
** `substring()` 类似于 `slice()` , 不同之处在于 `substring()` 无法接受负的索引。**
**如果省略第二个参数，则该 `substring()` 将裁剪字符串的剩余部分**

**5. `substr()` 方法**
** `substr()` 类似于 `slice()` , 不同之处在于第二个参数规定被提取部分的长度**
**如果省略第二个参数，则该 `substr()` 将裁剪字符串的剩余部分**
**如果收个参数为负，则从字符串的结尾计算位置，第二个参数不能为负，因为它定义的是长度**

**6. 替换字符串内容**
**replace()方法用另一个值替换在字符串中的指定的值**
**默认地，replace()对大小写敏感**
**如需执行大小写不敏感的替换，请使用正则表达式/i(大小写不敏感)**
**正则表达式不带引号。都需替换所有匹配，请使用正则表达式的g标志(用于全局搜索)**

**7. 转换为大写和小写**
**通过 `toUpperCase()` 把字符串转换为大写**
**通过 `toLowerCase()` 把字符串转换为小写**

**8. `contac()` 方法**
** `contact()` 连接两个过多个字符串**
** `contact()` 方法可用于代替加运算符，下面代码是等效的**

``` js
var text = "Hello" + " " + "World!";
var text = "Hello.contact("
","
World!");
```

**9. `String.trim()` **
** `trim()` 方法删除字符串两端的空白符：**
**Internet Explorer 8或更低版本不支持 `trim()` 方法。**
**如需支持IE 8，可以搭配正则表达式使用 `replace()` 方法代替：**

``` js
var str = "       Hello World!        ";
alert(str.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, ''));
```

**10. 提取字符串字符**
**这是两个提取字符串字符的安全方法**
**1.charAt(position)**
**2.charCodeAt(position)**

**charAt()方法**
**charAt()方法返回字符串中指定下标(位置)的字符串**

``` js
var str = "Hello World!";
str.charAt(0); //返回H
```

** `charCodeAt()` 方法**
** `charCodeAt()` 方法返回字符串中指定索引的字符unicode编码：**

``` js
var str = "Hello World";
str.charCodeAt(0); //返回72
```

**11. 把字符串转换为数组**
**可以通过 `split()` 将字符串转换为数组**

``` js
var txt = "a,b,c,d,e"; //字符串
txt.split(","); //用逗号分隔
txt.split(" "); //用空格分隔
txt.split("|"); //用竖线分隔
```

**如果省略分隔符，被返回的数组将包含index[0]中的整个字符串。**
**如果分隔符是"", 被返回的数组将是间隔单个字符的数组**

``` js
var txt = "Hello" //字符串
txt.split(""); //分割为字符
```

---

## JavaScript数值

**JavaScript数值始终是64位的浮点数**
**JavaScript的加法和级联都是用+运算符**
**数字用加法，字符串用级联**

---
**NaN-非数值**
**NaN属于JavaScript保留词，只是某个数不是合法数**
**可以使用JavaScript函数 `isNaN()` 来确定莫格知是否是数**
**如果在数学运算中使用了NaN, 则结果也将是NaN**
** `typeof NaN` 返回number**

---
**Infinity(或-Infinity)是JavaScript在计算书是超出最大可能数范围时返回的值**
**除以0(零)也会生成Infinity**
**Infinity是数： `typeOf Infinity` 返回number**

---
**十六进制**
**JavaScript会把前缀为0x的数值常量解释为十六进制**
`var x = 0xff; //x将是255` 

---
**数值可以是对象**
**可以通过关键词new定义为对象: `var y = new Number(123)` **
**不要创建数值对象，会拖慢执行速度**
**new关键词是代码复杂化，并产生默写无法预料的结果**
**当使用==相等运算符时，相等的数看上去相等**
**当使用===相等运算符后，相等的数变为不相等，因为===运算符需要类型和值同时相等。**
**JavaScript对象无法进行比较**

---
**JavaScript数值方法**
** `toString()` 以字符串返回数值**
** `toExponential()` 返回字符串值，包含已被四舍五入并使用指数计数法的数字。**
** `toFixed()` 返回字符串值，包含了指定位数小数的数字**
** `toPrecision()` 返回字符串值，包含了指定长度的数字**
** `valueOf()` 以数值返回数值**

**把变量转换为数值**

|方法|描述|
|------|:-------|
| Number() | 返回数字，由其参数转换而来。|
| parseFloat() | 解析其参数并返回浮点数。|
| parseInt() | 解析其参数并返回整数。|

** `Number()` 方法**
** `Number()` 可用于把 JavaScript 变量转换为数值**
**如果无法转换数字，则返回NaN**
**用于日期的 `Numebr()` 方法, 可以把日期转换为数字**

** `parseInt()` 方法**
**parseInt() 解析一段字符串并返回数值。允许空格。只返回首个数字**
**如果无法转换为数值，则返回 NaN**

** `parseFloat()` 方法**
** `parseFloat()` 解析一段字符串并返回数值。允许空格。只返回首个数字**
**如果无法转换为数值，则返回 NaN**

**数值属性**
|属性|描述|
|:-------|:--------:|
|MAX_VALUE| 返回 JavaScript 中可能的最大数。|
|MIN_VALUE|	返回 JavaScript 中可能的最小数。|
|NEGATIVE_INFINITY|	表示负的无穷大（溢出返回）。|
|NaN| 表示非数字值（"Not-a-Number"）。|
|POSITIVE_INFINITY|	表示无穷大（溢出返回）。|

---

## JavaScript数组

**数组元素可以是对象**
**JavaScript变量可以是对象，数组是特殊类型的对象**
**数组属性和方法**
**1.lenght属性**
**length属性返回数组的长度(数组元素的数目)**
**2. `push()` 方法**
**向数组添加新元素的最佳方法是 `push()` 方法**

**数组和对象的区别**
**在JavaScript中， 数组使用数字索引**
**在JavaScript中，对象使用命名索引**
**数组是特殊类型的对象，具有数字索引**

**何时使用数组，何时使用对象**
**JavaScript不支持关联数组**
**如果希望元素名为字符串(文本)则应该使用对象**
**如果希望元素名为数字则应该使用数组**

**避免 `new Array()` **
**没有必要使用JavaScript的内建数组构造器 `new Array()` **
**使用[]取而代之, 例如：**

``` js
var points = new Array(); // 差
var points = []; // 优
```

**如何识别数组**

** `isArray()` 函数解决此问题**

``` js
function isArray(x) {
    return x.constructor.toString().indexOf("Array") > -1;
}
```

**加入参数为数组，则上面的函数始终返回true, 或者更准确的解释是：假如对象原型包含单词 "Array" 则返回 true。**

**JavaScript数组方法**
**把数组转换为字符串**
**JavaScript方法`toString()把数组转换为数组值(逗号分隔)的字符串**
** `join()` 方法也可以将所有数组元素结合为一个字符串，类似于toString(), 但可以规定分隔符，例如**

``` js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join(" * ");
```

**Popping和Pushing**
**在处理数组是，删除元素和添加新元素是很简单的**
**Popping和Pushing指的是：从数组弹出项目，或向数组推入项目**

**Popping**
** `pop()` 方法从数组中删除最后一个元素**

**Pushing**
** `push()方` 法(在数组结尾处)向数组添加一个新的元素**

**位移元素**
** `shift()` 方法会删除首个数组元素，并把所有其他元素“位移”到更低的索引。**
 ** `unshift()` 方法(在开头)向数组添加新元素，并“反向位移”旧元素：**

 **更改元素**
 **length属性提供了向数组追加新元素的简易方法，例如：**

 

``` js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits[fruits.length] = "Kiwi"; // 向 fruits 追加 "Kiwi"
```

**删除元素**
**可以使用JavaScript delete运算符来删除 delete会在数组留下未定义的空洞，使用 `pop()` 或 `shift()` 取而代之**

**拼接数组**
** `splice()` 方法用于向数组添加新项 例如**

``` js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi");
```

**第一个参数(2)定义了应添加新元素的位置**
**第二个参数(0)定义应删除多少元素**
** `splice()` 方法返回一个包含已删除项的数组**

**使用 `splice()` 删除元素，splice在数组中不留“空洞”的情况下移除元素，例如**

``` js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(0, 1); // 删除 fruits 中的第一个元素
```

**第一个参数(0)定义新元素应该被添加(接入)的位置**
**第二个参数(1)定义应该删除多个元素**

**合并(连接)数组**
** `concat()` 方法通过合并(连接)现有数组来创建一个新数组**
** `concat()` 方法不会更改现有数组，它总是返回一个新数组**
** `concat()` 方法可以使用任意数量的数组参数**

**裁剪数组**
** `slice()` 方法用数组的某个片段切出新数组， `slice()` 方法创建新数组，它不会从源数组中删除任何元素**
** `slice()` 可接受两个参数，比如(1, 3)，该方法会从开始参数选取元素，直到结束参数(不包括)为止**

**所有JavaScript对象都拥有 `toString()` 方法**

---

## 数组排序

** `sort()` 方法是最强大的数组方法之一**

**反转数组**
** `reverse()` 方法反转数组中的元素，它可以降序对数组进行排序**

**比值函数**
**`function(a,b){return a-b}`**
**当 `sort()` 函数比较两个值时，会将值发送到比较函数，并根据所返回的值(负/零或正值)对这些值进行排序**

**以随机顺序排序数组**

``` js
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b) {
    return 0.5 - Math.random()
});
```

**查找最高(或最低)的数组值**
**升序排序 例子：**

``` js
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b) {
    return a - b
});

// 现在 points[0] 包含最低值
// 而 points[points.length-1] 包含最高值
```

**降序排序 例子：**

``` js
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b) {
    return b - a
});

// 现在 points[0] 包含最高值
// 而 points[points.length-1] 包含最低值
```

**`Math.max()`**
**可以使用 `Math.max.apply` 来查找数组中的最高值**
**`Math.max.apply([1, 2, 3]) 等于 Math.max(1, 2, 3)。`**

**`Math.min()`**
**可以使用 `Math.min.apply` 来查找数组中的最低值**
**Math.min.apply([1, 2, 3]) 等于 Math.min(1, 2, 3)。**

**自制查找最大/最小值方法**
**查找最大值Max**

``` js
function myArrayMax(arr) {
    var len = arr.length
    var max = -Infinity;
    while (len--) {
        if (arr[len] > max) {
            max = arr[len];
        }
    }
    return max;
}
```

**查找最小值Min**

``` js
function myArrayMin(arr) {
    var len = arr.length
    var min = Infinity;
    while (len--) {
        if (arr[len] < min) {
            min = arr[len];
        }
    }
    return min;
}
```

**排序对象数组**

``` js
var cars = [{
        type: "Volvo",
        year: 2016
    },
    {
        type: "Saab",
        year: 2001
    },
    {
        type: "BMW",
        year: 2010
    }
];
```

**即使对象拥有不同数据类型的属性，sort() 方法仍可用于对数组进行排序。解决方法是通过比较函数来对比属性值：**
**`cars.sort(function(a, b){return a.year - b.year});`**

---

## JavaScript数组迭代方法

**1. `Array.foreach()` **

**2. `Array.map()` **
** `map()` 方法通过对每个数组元素执行函数来创建新数组**
** `map()` 方法不会对没有值的数组元素执行函数**
** `map()` 方法不会更改原始数组**

**3. `Array.filter()` **
** `filter()` 方法创建一个包含通过测试的数组元素的新数组**

**4. `Array.reduce()` **
** `reduce()` 方法在每个数组元素上运行函数，以生成(减少它)单个值**
** `reduce()` 方法在数组中从左到右工作，另请参见 `reduceRight()` **
** `reduce()` 方法不会减少原始数组**
** `reduce()` 方法能够接受一个初始值**

**5. `Array.reduceRight()` **
** `reduceRight()` 方法在每个数组元素上运行函数，以生成(减少它)单个值。**
** `reduceRight()` 方法在数组中从左到右工作，另请参见reduce()。**
** `reduceRight()` 方法不会减少原始数值**

**6. `Array.every()` **
** `every()` 方法检查所有数组值是否通过测试**

**7. `Array.some()` **
** `some()` 方法检查某些数据值是否通过了测试**

**8. `Array.indexOf()` **
** `indexOf()` 方法在数组中搜索元素值并返回其位置**
**语法**
**`array.indexOf(item,start)`**
| 属性 | 描述 |
|------|:-------:|
|item| 必需，要检索的项目|
|start| 可选，从哪里开始搜索，负值将从结尾开始的给定位置开始，并搜索到结尾|
**如果未找到项目， `Array.indexOf()` 返回-1

**9. `Array.lastIndexOf()` **
** `Array.lastIndexOf()` 与 `Array.indexOf()` 类似，但是从数组结尾处开始搜索**
**语法**
**`array.lastIndexOf(item,start)`**
| 属性 | 描述 |
|------|:-------:|
|item| 必需，要检索的项目|
|start| 可选，从哪里开始搜索，负值将从结尾开始的给定位置开始，并搜索到结尾|

**10. `Array.find()` **
** `find()` 方法返回通过测试函数的第一个数组元素的值**

**11. `Array.findIndex()` **
** `findIndex()` 方法返回通过测试函数的第一个数组元素的索引**

---

## JavaScript日期

**默认情况下，JavaScript将使用浏览器的时区并将日期显示为全文本字符串**
**创建Date对象**
**Date对象由新的Date()构造函数创建**
**4种方法创建新的日期对象**
**1. `new Date()` **
**2. `new Date(year,month,day,hours,minutes,seconds,milliseconds)` **
**1. `new Date(milliseconds)` **
**1. `new Date(date string)` **

** `new Date()` 用当前日期和时间创建新的日期对象**

** `new Date(year, month, ...)` 用指定日期和时间创建新的日期对象。**
**JavaScript从0到11计算月份，1月是0，十二月时11**
**不能省略月份，如果只提供一个参数，则将其视为毫秒**

** `new Date(dateString)` 从日期字符串常见一个新的日期对象**

**`new Date(milliseconds)`**
** `new Date(milliseconds)` 创建一个零时加毫秒的新日期对象**

** `toUTCString()` 方法将日期转换为UTC字符串(一种日期显示标准)**

** `toDateString()` 方法将日期转换为更易读的格式**

**JavaScript日期格式化**
|类型|实例|
|-------|:--------:|
|ISO 日期|	"2018-02-19" （国际标准）|
|短日期	| "02/19/2018" 或者 "2018/02/19"|
|长日期	| "Feb 19 2018" 或者 "19 Feb 2019"|
|完整日期 | "Monday February 25 2015"|

**JavaScript获取日期方法**
| 方法 | 描述 |
|:-------|:--------:|
|getDate()|	以数值返回天（1-31）|
|getDay()|	以数值获取周名（0-6）|
|getFullYear()|	获取四位的年（yyyy）|
|getHours()|	获取小时（0-23）|
|getMilliseconds()|	获取毫秒（0-999）|
|getMinutes()|	获取分（0-59）|
|getMonth()|	获取月（0-11）|
|getSeconds()|	获取秒（0-59）|
|getTime()|	获取时间（从 1970 年 1 月 1 日至今）|


**UTC日期方法**
| 方法 | 描述 |
|:-------|:--------:|
|getUTCDate()|	等于 getDate()，但返回 UTC 日期|
|getUTCDay()|	等于 getDay()，但返回 UTC 日|
|getUTCFullYear()|	等于 getFullYear()，但返回 UTC 年|
|getUTCHours()|	等于 getHours()，但返回 UTC 小时|
|getUTCMilliseconds()|	等于 getMilliseconds()，但返回 UTC 毫秒|
|getUTCMinutes()|	等于 getMinutes()，但返回 UTC 分|
|getUTCMonth()|	等于 getMonth()，但返回 UTC 月|
|getUTCSeconds()|	等于 getSeconds()，但返回 UTC 秒|

