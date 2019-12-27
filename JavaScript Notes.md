## JavaScript 笔记

### 数据类型概述

**1. 简介**
**JavaScript数据类型共六种**

* **数值(number)：整数和小数**
* **字符串(string): 文本**
* **布尔值(boolean): 表示真伪的两个特殊值，即true和false**
* **undefined: 表示"未定义"或"不存在"**
* **null: 表示空值**
* **对象(object): 各种值组成的集合**

**下列运算符会返回布尔值**

* **前置逻辑运算符： `!` (Not)**
* **相等运算符： `===` , `!==` , `==` , `!=` **
* **比较运算符： `>` , `>=` , `<` , `<=` **

**有六个值被转为false**

* **undefined**
* **null**
* **false**
* **0**
* **NaN**
* **""或''(空字符串)**

**空数组[]和空对象{}对应的布尔值，都是true**

**对象是最复杂的数据类型，又可以分成三个子类型**

* **狭义的对象(object)**
* **数组(array)**
* **函数(function)**

**2.typeof运算符**
**JavaScript有三种方法确定一个值是什么类型**

*`typeof`**运算符**
*`instanceof`**运算符，它可以区分数组和对象**
*`Object.prototype.toString`**方法**

---

### 数值

**1. 概述**
**1.1整数和浮点数**

**1.2数值精度**
**大于2的53次方以后，多出来的有效数字(最后三位的111)都会无法保存，变成0**

**1.3数值范围**
**如果一个数大于等于2的1024次方，就会正向溢出，即JavaScript无法表示，会返回Infinity**
**JavaScript提供Number对象的MAX_VALUE和MIN_VALUE属性，返回可以表示的最大值和最小值**

**2. 数值的表示法**
**可用字面形式直接表示，比如35(十进制)和0xFF(十六进制)，也可以用科学计数法表示**

**3. 数值的进制**
**有四种表示方法：十进制、十六进制、八进制、二进制**

* **十进制：没有前导0的数值**
* **八进制：有前缀0o或0O的数值，或者有前导0、且只用到0-7的八个阿拉伯数字的数值。**
* **十六进制：有前缀0x或0X的数值。**
* **二进制：有前缀0b或0B的数值。**

**4. 特殊数值**
**4.1正零和负零**
**几乎所有场合，正零和负零都会被当作正常的0。唯一有区别的场合是，+0或-0当作分母，返回的值是不相等的。**
`(1 / +0) === (1 / -0) // false` 
**是因为除以正零得到+Infinity，除以负零得到-Infinity，这两者是不相等的**

**4.2NaN**
**(1)含义**
**NaN是特殊值，表示非数字(Not a Number)**
**(2)运算规则**
**NaN不等于任何值，包括它本身**
**数组的indexOf方法对NaN不成立**
**NaN在布尔运算时被当做false**
**NaN与任何数的运算，得到都是NaN**

**4.3 Infinity**
**(1)含义**
**Infinity表示无穷，两种场景，一种是正的数值太大，或一个负的数值太小，无法表示，另一种是非0数值除以0，得到Infinity**
**Infinity大于一切数值(除了NaN), -Infinity小于一切数值(除了NaN)**
**Infinity与NaN比较，总返回false**
**(2)运算规则**
**Infinity的四则运算，符合无穷的数学计算规则**

``` js
5 * Infinity // Infinity
5 - Infinity // -Infinity
Infinity / 5 // Infinity
5 / Infinity // 0
```

``` js
0 * Infinity // NaN
0 / Infinity // 0
Infinity / 0 // Infinity
```

``` js
Infinity + Infinity // Infinity
Infinity * Infinity // Infinity
```

``` js
Infinity - Infinity // NaN
Infinity / Infinity // NaN
```

``` js
Infinity - Infinity // NaN
Infinity / Infinity // NaN
```

``` js
undefined + Infinity // NaN
undefined - Infinity // NaN
undefined * Infinity // NaN
undefined / Infinity // NaN
Infinity / undefined // NaN
```

**5. 与数值相关的全局方法**
**5.1 parseInt()**
**(1)基本用法**
**parseInt()方法用于将字符串转为整数**
**(2)进制转换**
**parseInt()方法还可以接受第二个参数（2到36之间），表示被解析的值的进制，返回该值对应的十进制数。默认情况下，parseInt()的第二个参数为10，即默认是十进制转十进制。**

**5.2 parseFloat()**
**parseFloat()方法用于将一个字符串转为浮点数**
**如果字符串包含不能转为浮点数的字符，则不再进行往后转换，返回已经转好的部分，如果参数不是字符串，或者字符串的第一个字符不能转化为浮点数，则返回NaN**
**parsefloat()会将空字符串转为NaN**

**5.3 isNaN()**
**isNaN()方法用来判断一个值是否为NaN**
**isNaN()只对数值有效，如果传入其他值，会被先转为数值，例如，传入字符串的时候，字符串会被先转出NaN, 所以最后返回true，isNaN为true的值，有可能不是NaN, 而是一个字符串**
**对于对象和数组，isNaN()也返回true**
**对于空数组和只有一个数值成员的数组，isNaN()返回false**
**判断NaN更可靠的方法是，利用NaN为唯一不等于自身的值这个特点，进行判断**

**5.4 isFinite()**
**isFinite()方法返回一个布尔值，表示某个值是否为正常的值**
**除了Infinity、-Infinity、NaN和undefined这几个值会返回false, isFinite对于其他的数值都会返回true**

---

### 字符串

**转义**

* \0 ：null（\u0000）
* \b ：后退键（\u0008）
* \f ：换页符（\u000C）
* \n ：换行符（\u000A）
* \r ：回车键（\u000D）
* \t ：制表符（\u0009）
* \v ：垂直制表符（\u000B）
* \' ：单引号（\u0027）
* \" ：双引号（\u0022）
* \\(双反斜杠) ：反斜杠（\u005C）

上面这些字符前面加上反斜杠，都表示特殊含义

**反斜杠还有三种特殊用法**
**(1) \HHH**
**反斜杠后面紧跟三个八进制数（000到377），代表一个字符。HHH对应该字符的 Unicode 码点，比如\251表示版权符号。显然，这种方法只能输出256种字符。**

**(2) \xHH**
**\x后面紧跟两个十六进制数（00到FF），代表一个字符。HH对应该字符的 Unicode 码点，比如\xA9表示版权符号。这种方法也只能输出256种字符。**

**(3)\uXXXX**
**\u后面紧跟四个十六进制数（0000到FFFF），代表一个字符。XXXX对应该字符的 Unicode 码点，比如\u00A9表示版权符号。**

**例子**

``` js
'\251' // "©"
'\xA9' // "©"
'\u00A9' // "©"

'\172' === 'z' // true
'\x7A' === 'z' // true
'\u007A' === 'z' // true
```

**length属性 返回字符串的长度**

**Base64 转码**
**JavaScript原生提供两个Base64相关的方法**

* **byoa(): 任意值转为Base64的编码**
* **atob(): Base64编码转为原来的值**

---

### 对象

**对象就是一组"键值对"(key-value)的集合，是一种无序的复合数据集合**
**表达式还是语句？**
`{foo：123}` 
**JavaScript引擎读到上面代码可能会有两种含义，第一种，这是一个表达式，表示一个包含foo属性的对象；第二种可能是，这是一个语句，表示一个代码区块, 里面有一个标签foo，指向表达式123**
**为避免这种歧义，JavaScript引擎的做法是遇到这种情况，无法确定是对象还是代码块，一律解释为代码块**

**属性**
**1. 属性的读取**
**读取对象的属性，有两种方法，一种是使用点运算符，还有一种是使用方括号运算符[]**
**如果使用[]运算符，键名必须放在引号里面，否则会被当作变量处理**
**数字键可以不加引号，会自动转成字符串**
**数值键不能使用点运算符(因为会被当成小数点)，只能使用方括号运算符**

**2. 属性的赋值**
**点运算符和[]运算符，不仅可以用来读取值，还可以用来赋值**
**下面代码中，分别使用点运算符和[]运算符，对属性赋值**

``` js
var obj = {};

obj.foo = 'Hello';
obj['bar'] = 'World';
```

**3. 属性的查看**
**查看一个属性本身所有的属性，可以使用Object.keys方法**

**4. 属性的删除：delete命令**
**delete命令用于删除对象的属性，删除生工后返回true**
**注意, 删除一个不存在的属性，delete不报错，而且返回true**
**只有一种情况，delete命令会返回false，那就是该属性存在，且不得删除**

**5. 属性是否存在：in运算符**
**in运算符用于检查对象是否包含某个属性**

**6. 属性的遍历：for... in循环**
** `for...in` 循环有两个使用注意点**

* **它遍历的是对象所有可遍历的属性，会跳过不可遍历的属性**
* **它不仅遍历对象自身的属性，还遍历继承的属性**

**with语句(不建议使用)**
**with语句格式如下**

``` js
with(对象) {
    语句;
}
```

**注意，如果with区块内部有变量的赋值操作，必须是当前对象已经存在的属性，否则会创造一个当前作用域的全局变量**

### 函数

**JavaScript有三种声明函数的方法**
**(1)function命令 function命令后面是函数名，函数名后面是一对圆括号，里面传入函数的参数，函数体具体放在大括号里**

``` js
function print(s) {
    console.log(s);
}
```

**(2)函数表达式**
**除了用function命令声明函数，还可以采用变量赋值的写法**

``` js
var print = function(s) {
    console.log(s);
};
```

**(3)function构造函数(基本不用)**
**第三种声明的方式是Funciton构造函数**

``` js
var add = new Function() {
    'x';
    'y';
    'return x+y';
};

//等同于
function add(x, y) {
    return x + y;
}
```

**函数的重复声明,如果同一个函数被多次声明，后面的声明就会覆盖前面的声明**

**圆括号运算符，return语句和递归**
**函数体内部的return语句，表示返回。JavaScript 引擎遇到return语句，就直接返回return后面的那个表达式的值，后面即使还有语句，也不会得到执行。也就是说，return语句所带的那个表达式，就是函数的返回值。return语句不是必需的，如果没有的话，该函数就不返回任何值，或者说返回undefined。**
**函数可以调用自身，这就是递归(recursion)**

**在JavaScript中函数为第一等公民**

**函数名的提升**
**如果同时采用function命令和赋值语句声明同一个函数，最后总是采用赋值语句的定义**


**函数的属性和方法**
**1.name属性 返回函数的名字，如果是通过变量复制定义的函数，那么name属性返回变量名**
**2.length属性 返回函数预期传入的参数个数，即函数定义之中的参数个数**
**3.toString()方法返回一个字符串，内容是函数的源码**

**函数作用域**
**作用域指的是变量存在的范围，在ES5的规范中，JavaScript只有两种作用域：一种是全局作用域，变量在整个程序中一直存在，所有地方都可以读取；另一种势函数作用域，变量只在函数内部存在**

**函数内部的变量提升**
**var 命令声明的变量，不管在什么位置，变量声明都会被提升到函数体的头部**

**函数本身的作用域 就是其声明时所在的作用域，与其所在的作用域无关**

**参数**
**函数运行的时候，有时需要提供外部数据，不同的外部数据会得到不同的结果，这种外部数据就叫参数**

```js
function square(x) {
  return x * x;
}

square(2) // 4
square(3) // 9
```
**上式的x就是square函数的参数。每次运行的时候，需要提供这个值，否则得不到结果。**

**参数的省略 函数参数不是必须的，JavaScript允许参数省略**

**传递方式 是传值传递 ，在函数体内修改参数值，不会影响到函数外部**

**同名参数**
**如果同名的参数，则取最后出现的那个值**

**arguments对象**
**由于JavaScript允许有不定数目的参数，所以需要一种机制，可以在函数体内部读取所有参数，这就是arguments对象的由来**
**arguments对象包含了函数运行时的所有参数，arguments[0]就是第一个参数，arguments[1]就是第二个参数，以此类推，这个对象只有在函数体内部，才可以使用**
**严格模式下，arguments对象与函数参数不具有联动关系，也就是说，修改arguments对象不会影响到实际的函数参数，例如**

```js
var f = function(a, b) {
  'use strict'; // 开启严格模式
  arguments[0] = 3;
  arguments[1] = 2;
  return a + b;
}

f(1, 1) // 2
```
**通过arguments对象的length属性，可判断函数调用时到底带几个参数**

**与数组的关系**
**虽然arguments很想数组，但它是一个对象，数组专有的方法(比如slice和forEach),不能再arguments对象上使用**
**解决方法是将arguments转为真正的数值，下面是两种常用的转换方法**

```js
var args = Array.prototype.slice.call(arguments);

// 或者
var args = [];
for (var i = 0; i < arguments.length; i++) {
  args.push(arguments[i]);
}
```

**callee属性(不建议使用)**
**arguments对象滴啊有一个callee属性，返回它所对应的原函数**

**闭包**
**闭包是JavaScript的一个难点，也是特色，很多高级应用都要依靠闭包实现**
**理解闭包，首先必须理解变量作用域**
**闭包最大的用处有两个，一个是可以读取函数内部的变量，另一个就是始终保持在内存中，即闭包可以使得它诞生环境一直存在，请看下面例子**

```js
function createIncrementor(start) {
  return function () {
    return start++;
  };
}

var inc = createIncrementor(5);

inc() // 5
inc() // 6
inc() // 7
```
**闭包的另一个用处，是封装对象的私有属性和私有方法**

```js
function Person(name) {
  var _age;
  function setAge(n) {
    _age = n;
  }
  function getAge() {
    return _age;
  }

  return {
    name: name,
    getAge: getAge,
    setAge: setAge
  };
}

var p1 = Person('张三');
p1.setAge(25);
p1.getAge() // 25
```
**闭包不能滥用，否则会造成网页的性能问题**

**立即调用的函数表达式(IIFE)**

```js
// 写法一
var tmp = newData;
processData(tmp);
storeData(tmp);

// 写法二
(function () {
  var tmp = newData;
  processData(tmp);
  storeData(tmp);
}());
```
**上面代码中，写法二比写法一更好，因为完全避免了污染全局变量。**

**eval命令**
**eval命令接收一个字符串作为参数，并将这个字符串当作语句执行**
**放在eval中的字符串，应该有独立存在的意义，不能用来与eval以外的命令配合使用**