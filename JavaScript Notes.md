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

**函数的重复声明, 如果同一个函数被多次声明，后面的声明就会覆盖前面的声明**

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

``` js
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

``` js
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
**虽然arguments很想数组，但它是一个对象，数组专有的方法(比如slice和forEach), 不能再arguments对象上使用**
**解决方法是将arguments转为真正的数值，下面是两种常用的转换方法**

``` js
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

``` js
function createIncrementor(start) {
    return function() {
        return start++;
    };
}

var inc = createIncrementor(5);

inc() // 5
inc() // 6
inc() // 7
```

**闭包的另一个用处，是封装对象的私有属性和私有方法**

``` js
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

``` js
// 写法一
var tmp = newData;
processData(tmp);
storeData(tmp);

// 写法二
(function() {
    var tmp = newData;
    processData(tmp);
    storeData(tmp);
}());
```

**上面代码中，写法二比写法一更好，因为完全避免了污染全局变量。**

**eval命令**
**eval命令接收一个字符串作为参数，并将这个字符串当作语句执行**
**放在eval中的字符串，应该有独立存在的意义，不能用来与eval以外的命令配合使用**

**eval的别名调用**
**凡是使用别名执行eval，eval内部一律是全局作用域**

---

### 数组

**数组(array)是按次序排列的一组值，每个值得位置都有编号(从0开始), 整个数组用方括号表示**
`var arr = ['a','b','c'];` 
**任意类型的数据，都可以放入数组**
**数组本质上是一种特殊的对象， `typeof` 运算符会返回数组的类型是object**
**数组成员只能用arr[]方括号表示**

**length属性 返回数组的成员数量**
**清空数组的一个有效方法，就是将length属性设为0**

**in运算符**
**检查某个建明是否存在的运算符，适用于对象，也适用于数组**
**若数组某个位置为空，in运算符返回false**

** `for....in` 循环和遍历数组**
** `for...in` 不仅会遍历数组所有的数字键，还会遍历非数字键，不推荐使用 `for....in` 遍历数组**
**数组遍历可以使用 `for` 循环或 `while` 循环**
**数组的forEach方法，也可以用来遍历数组**

**数组的空位**
**数组空位可读取，返回undefined**
**length属性不过滤空位，使用length属性遍历数组是要注意**
**数组某个位置是空位，与某个位置是undefined，是不一样的，如果是空位，使用数组的 `forEach` 方、 `for...in` 结构、以及Object.keys方法进行遍历，空位会被跳过**
**如果某个位置是undefined，遍历时候不会被跳过**
**空位数组没有这个元素，不会遍历到，undefined则表示数组有这个元素，遍历不会跳过**

**类似数组的对象(array-like-object)**
**如果一个对象的所有键名都是正整数或零，并有length属性，那么这个对象就很像数组**
**对象obj没有数组的push方法，使用会报错**
**典型的类似数组的对象是函数arguments对象，以及大多数DOM元素集，还有字符串，例**

``` js
// arguments对象
function args() {
    return arguments
}
var arrayLike = args('a', 'b');

arrayLike[0] // 'a'
arrayLike.length // 2
arrayLike instanceof Array // false

// DOM元素集
var elts = document.getElementsByTagName('h3');
elts.length // 3
elts instanceof Array // false

    // 字符串
    'abc' [1] // 'b'
'abc'.length // 3
    'abc'
instanceof Array // false
```

**数组的slice方法可以将类似数组的对象变成真正的数组**
**除了转为真正的数组，类似数组的对象还有一个方法可以使用数组的方法，就是通过 `call()` 吧数组的方法放到对象上面, 例**

``` js
// forEach 方法
function logArgs() {
    Array.prototype.forEach.call(arguments, function(elem, i) {
        console.log(i + '. ' + elem);
    });
}

// 等同于 for 循环
function logArgs() {
    for (var i = 0; i < arguments.length; i++) {
        console.log(i + '. ' + arguments[i]);
    }
}

//字符串也是类似数组的对象
Array.prototype.forEach.call('abc', function(chr) {
    console.log(chr);
});
// a
// b
// c
```

---

## 运算符
**JavaScript提供10种算术运算符，用来完成基本的算术运算**
- 加法运算符：x + y
- 减法运算符： x - y
- 乘法运算符： x * y
- 除法运算符：x / y
- 指数运算符：x ** y
- 余数运算符：x % y
- 自增运算符：++x 或者 x++
- 自减运算符：--x 或者 x--
- 数值运算符： +x
- 负数值运算符：-x

**1. 算术运算符**
**加法运算符**
**JavaScript允许非数值相加，例**

``` js
true + true // 2
1 + true // 2
```

**上面代码中，第一行是两个布尔值相加，第二行是数值与布尔值相加。这两种情况，布尔值都会自动转成数值，然后再相加。**
**两个字符串相加，加法运算符就会变成连接运算符，返回一个新的字符串，将两个原字符串连接在一起**
**由于加法运算符存在重载，可能执行两种运算，使用时要注意**
**除了加法运算符，其他算数运算符(减法、乘法和除法)都不会发生重载，规则是：所有运算子一律转为数值，再进行相应的数学运算，例**

``` js
1 - '2' // -1
1 * '2' // 2
1 / '2' // 0.5
```

**上面代码中，减法、除法和乘法运算符，都是将字符串自动转为数值，然后再运算。**

**对象的相加**
**如果运算子是对象，必选转为原始类型的值，然后再相加**

``` js
var obj = {
    p: 1
};
obj + 2 //"[object Object]2"
```

**上面代码中，对象obj转成原始类型的值是[object Object]，再加2就得到了上面的结果。**
**对象转为原始类型的值，规则如下**
**首先，自动调用对象的valueOf()方法**

``` js
var obj = {
    p: 1
};
obj.valueOf(); //{p:1}
```

**对象的valueOf()方法总是返回对象自身，这是在调用对象的toString方法，将其转为字符串**

``` js
var obj = {
    p: 1
};
obj.valueOf().toString() //"[object Object]"
```

**对象的toString方法默认返回[object Object], 所以就得到了最前面的那个例子的结果**

``` js
var obj = {
    valueOf: function() {
        return 1;
    }
};

obj + 2 // 3
```

**上面代码中，我们定义obj对象的valueOf方法返回1，于是obj + 2就得到了3。这个例子中，由于valueOf方法直接返回一个原始类型的值，所以不再调用toString方法**

``` js
//toString方法例子
var obj = {
    toString: function() {
        return 'hello';
    }
};

obj + 2 // "hello2"
```

**有一个特例，如果一个运算子是一个Date对象的实例，那么会优先执行toString方法**

``` js
var obj = new Date();
obj.valueOf = function() {
    return 1
};
obj.toString = function() {
    return 'hello'
};

obj + 2 //"hello2"
```

**上面代码中，对象obj是一个Date对象的实例，并且自定义了valueOf方法和toString方法，结果toString方法优先执行。**

**余数运算符**
** `%` 返回前一个运算子背后一个运算子除，所得的余数**

``` js
12 % 5 //2
```

**需要注意，运算结果的正负号由第一个运算子的正负号决定**

``` js
-1 % 2 // -1
1 % -2 // 1
```

**为得到正确的余数值，可以使用绝对函数值**

``` js
//错误写法
function isOdd(n) {
    return n % 2 == 1;
}
isOdd(-5); //false
isOdd(-4); //false

//正确写法
function isOdd(n) {
    return Math.abs(n % 2) == 1;
}
isOdd(-5) //true
isOdd(-4) //false
```

**余数运算符还可以用于浮点数的运算，但是，由于浮点数不是精确的值，无法得到完全准确的结果**

**自增和自减运算符**

``` js
var x = 1;
++x; //2
x //2

--x //1
x //1
```

``` js
var x = 1;
var y = 1;

x++ //1
++y //2
```

**自增和自减运算符有一个注意的地方，就是放在变量之后，会先返回变量操作之前的值，再进行自增/自减操作，放在变量之前，会先进行自增/自减操作，再返回变量操作后的值**

**数值运算符，负数值运算符**
**数值运算符(+)同样使用加号，但它是一元运算符(只需要一个操作数)，而加法运算符是二元运算符(需要两个操作数)**
**数值运算符的作用在于可以将任何值转为数值(与Number函数的作用相同)**

**负值运算符(-)，同样具有将一个值转为数值的功能，只不过得到的值正负相反，连用两个福数值运算符，等同于数值运算符**

```js
var x = 1;
-x//-1
-(-x)//1
```

**上面代码最后一行圆括号不能少，否则会变成自减运算符**
**数值运算符和负数值运算符都会返回一个新的值，而不会改变原始变量的值**


**指数运算符**
**指数运算符(`**`)完成指数运算，前一个运算子是底数，后一个运算子是指数**

```js
2 ** 4 //16
```

**注意，指数运算符是右结合，而不是左结合，即多个指数运算符连用时，先进性最右边的计算**

```js
//相当于2 ** (3 ** 2)
2 ** 3 ** 2
//512
```

**上面代码中，由于是指数运算符是右结合，所以先计算第二个指数运算符，而不是第一个**

**赋值运算符**
**最常见的赋值运算符(=)**
**负值运算符还可以与其他运算符结合，形成变体，如下是与算术运算符的结合**

```js
//等同于 x = x + y
x += y

// 等同于 x = x - y
x -= y

// 等同于 x = x * y
x *= y

// 等同于 x = x / y
x /= y

// 等同于 x = x % y
x %= y

// 等同于 x = x ** y
x **= y
```

**下面是与位运算符的结合**

```js
// 等同于 x = x >> y
x >>= y

// 等同于 x = x << y
x <<= y

// 等同于 x = x >>> y
x >>>= y

// 等同于 x = x & y
x &= y

// 等同于 x = x | y
x |= y

// 等同于 x = x ^ y
x ^= y
```

**这些复合的赋值运算符，都是先进行指定运算，然后将得到的值返回给左边的变量**


**比较运算符**
**JavaScript提供了8个比较运算符**
- `>` 大于运算符
- `<` 小于运算符
- `<=` 小于或等于运算符
- `>=` 大于或等于运算符
- `==` 相等运算符
- `===` 严格相等运算符
- `!=` 不相等运算符
- `!==` 严格不相等运算符

**相等比较和非相等比较，两者规则不一样，对于非相等比较，算法是先看两个运算子是否都是字符串，如果是的，就按照字典顺序比较（实际上是比较 Unicode 码点）；否则，将两个运算子都转成数值，再比较数值的大小。**

**非相等运算符：字符串的比较**

```js
'cat' > 'dog' //false
'cat' > 'catalog' //false
```

**JavaScript 引擎内部首先比较首字符的 Unicode 码点。如果相等，再比较第二个字符的 Unicode 码点，以此类推。**

```js
'cat' > 'Cat' //true
```

**上面代码中，小写c的Unicode码点(99)大于大写C的Unicode码点(67),所以返回true**

**非相等运算符：非字符串的比较**
**如果两个运算子中，至少有一个不是字符串，需要分成以下两种情况**
**(1)原始类型值**
**如果两个运算子都是原始类型的值，则现在转成数值再比较**

```js
5 > '4' // true
// 等同于 5 > Number('4')
// 即 5 > 4

true > false // true
// 等同于 Number(true) > Number(false)
// 即 1 > 0

2 > true // true
// 等同于 2 > Number(true)
// 即 2 > 1
```

**字符串和布尔值都会转成数值，再进行比较**

**需要注意与NaN的比较，任何值(包括NaN本身)与NaN比较，返回的都是false**

```js
1 > NaN //false
1 <= NaN //false
'1' > NaN //false
'1'<= NaN //false
NaN > NaN //false
NaN <= NaN //false
```

**(2)对象**
**如果运算子是对象，会转为原始类型的值，再进行比较**
**对象转为原始类型的值，算法是先调用valueOf方法，如果返回的还是对象，再接着调用toString方法**

```js
var x = [2];
x > '11'//true
//等同于[2].valueOf().toString() > '11'
//即 '2' > '11'

x.valueOf = function(){return '1'};
x > '11'//false
//等同于[2].valueOf() > '11'
//即 '1' > '11'
```

**两个对象之间的比较也是如此**

```js
[2] > [1] //true
//等同于[2].valueOf().toString() > [1].valueOf().toString()
//即'2' > '1'
[2] > [11] //true
//等同于[2].valueOf().toString() > [11].valueOf().toString()
//即'2' > '11'
{x:2} >={x:1} //true
//等同于{x:2}.valueOf().toString()>={x:1}.valueOf.toString()
//即'[object Object]' >= '[object Object]'
```

**严格相等运算符**
**JavaScript提供两种相等运算符：`==` 和 `===`**
**`==`比较两个值是否相等**
**`===`比较两个值是否为"同一个值"，如果两个值不是同一类型，`===`直接返回false,而`==`会将两个值转换成同一个类型，再用`===`进行比较**

`===`算法
**(1)不同类型的值**
**两个值类型不同，直接返回false**

```js
1 === "1" //false
true === 'true' //false
```

**(2)同一类的原始类型值**
**同一类型的原始类型的值(数值、字符串、布尔值)比较时，值相同就返回true，值不同就返回false**

```js
1 === 0x1 //true
```

**上面代码比较的是十进制的1和十六进制的1，因为类型和值都相同，所以返回true**

**注意NaN与任何值都不相等(包括自身)，另外正0等于负0**

```js
NaN === NaN //false
+0 === -0 //true
```

**(3)复合类型值**
**两个复合类型(对象、数组、函数)的数据比较时，不是比较值是否相等，而是比较它们是否指向同一个地址**

```js
{} === {} //false
[] === [] //false
(function(){} === function(){}) //false
```

**上面代码分别比较两个空对象，两个空数组，两个空函数，结果都不相等，原因是对于复合类型的值，`===`比较的它们是否引用同一个内存地址，而运算符两边的空对象、空数组、空函数的值，都存放在不同的内存地址，结果当然是false**

**如果两个变量引用同一个对象，则它们相等**

```js
var v1 = {};
var v2 = v1;
v1 === v2 //true
```

**注意，对于两个对象的比较，`===`比较的是地址,而大于或小于运算符比较的是值**

```js
var obj1 = {};
var obj2 = {};

obj1 > obj2 //false
obj1 < obj2 //false
obj1 === obj2 //false

//上面三个比较，前两个比较的是值，最后一个比较的是地址，所以都返回false
```

**(4)undefined和null**
**undefined和null与自身严格相等**

```js
undefined === undefined //true
null === null //true
```

**由于变量声明后默认值是undefined，因此两个只声明未赋值的变量是相等的**

```js
var v1;
var v2;
v1 === v2 //true
```

**严格不相等运算符**
**`！==`的算法是先求严格相等运算符的结果，再返回相反值**

```js
1 !== '1' //true
//等同于
!(1 === '1')
```

**相等运算符**
**(1)原始类性值**

```js
1 == true // true
// 等同于 1 === Number(true)

0 == false // true
// 等同于 0 === Number(false)

2 == true // false
// 等同于 2 === Number(true)

2 == false // false
// 等同于 2 === Number(false)

'true' == true // false
// 等同于 Number('true') === Number(true)
// 等同于 NaN === 1

'' == 0 // true
// 等同于 Number('') === 0
// 等同于 0 === 0

'' == false  // true
// 等同于 Number('') === Number(false)
// 等同于 0 === 0

'1' == true  // true
// 等同于 Number('1') === Number(true)
// 等同于 1 === 1

'\n  123  \t' == 123 // true
// 因为字符串转为数字时，省略前置和后置的空格
```

**(2)对象与原始类性值比较**

```js
// 对象与数值比较时，对象转为数值
[1] == 1 // true
// 等同于 Number([1]) == 1

// 对象与字符串比较时，对象转为字符串
[1] == '1' // true
// 等同于 String([1]) == '1'
[1, 2] == '1,2' // true
// 等同于 String([1, 2]) == '1,2'

// 对象与布尔值比较时，两边都转为数值
[1] == true // true
// 等同于 Number([1]) == Number(true)
[2] == true // false
// 等同于 Number([2]) == Number(true)
```

**(3)undefined和null**

```js
false == null //false
false ==undefined //false

0 == null //false
0 == undefined //false

undefined == null //true
//undefined和null相互比较结果为true
```

**(4)相等运算符的缺点**

```js
0 == '' //true
0 == '0' //true

2 == true //false
2 == false //false

false == 'false' //false
false == '0' //true

false == undefined //false
false == null //false
null == undefined //true

'\t\r\n' == 0 //true
```

**上面这些表达式都不同于直觉，容易出错，不建议使用`==`，最好只使用`===`**

**不相等运算符**
**`!=`的算法是求相等运算符的结果，然后返回相反值**

```js
1 != '1' //false

//等同于
!(1 == '1')
```

**布尔运算符**
**布尔运算符用于将表达式转为布尔值，包含四个运算符**
- 取反运算符：!
- 且运算符：&&
- 或运算符：||
- 三元运算符：?:

**取反运算符(!)**
**`!`用于将布尔值变为相反值，即true变成false，false变成true**
**以下六个值取反后为true，其他都为false**
- undefined
- null
- false
- 0
- NaN
- 空字符串('')

```js
!undefined //true
!null //true
!0 //true
!NaN //true
!"" //true

!54 //false
!'hello' //false
![] //false
!{} //false
```

**如果对于一个值连续做两次取反运算，等于将其转为对应的布尔值，与Boolean函数的作用相同，这是一种常用的类型转换的写法**

```js
!!x
//等同于
Boolean(x)
//两次取反就是将一个值转为布尔值的简便写法
```

**且运算符(&&)**
**`&&`用于多个表达式的求值**

```js
't' && '' // ""
't' && 'f' // "f"
't' && (1 + 2) // 3
'' && 'f' // ""
'' && '' // ""

var x = 1;
(1 - 1) && ( x += 1) // 0
x // 1

```
**上面代码最后一个例子，由于且运算符的第一个运算子的布尔值为false，则直接返回它的值0,而不再对第二个运算子求值，所以X的值没变**

**跳过第二个运算子的机制被称为短路，例**

```js
if(i){
  doSomething();
}

//等价于
i && doSomething();
```

**后一种不易看出目的，也不易除错，谨慎使用**
**&&运算符可多个连用，,返回第一个布尔值为false的值，如果所有布尔值为true,则返回最后一个表达式的值**

```js
true && 'foo' && '' && 4 && 'foo' && true
//''

1 && 2 && 3
//3
```

**或运算符(||)**
**如果第一个运算子的布尔值为true，则返回第一个运算子的值，且不再对第二个运算子求值，如果第一个运算子的布尔值为false，则返回第二个运算子的值**

```js
't' || '' //"t"
't' || 'f' //"t"
'' || 'f' //"f"
'' || '' // ""
```

**短路规则同样适用**

```js
var x = 1;
true || (x = 2) //true
x //1
```

**||运算符可多个连用，这是返回第一个布尔值为true的表达式的值，如果所有表达式都为false，则返回最后一个表达式的值**

```js
false || 0 || '' || 4 || 'foo' ||true
//4

false || 0 || ''
// ' '
```

**||运算符常用于为一个变量设默认值**

```js 
function saveText(text){
  text = text || '';
  //...
}
//或者写成
saveText(this.text || '')
```

**上面代码表示如果函数调用时，没有提供参数，则该参数默认为空字符串**

**三元条件运算**
**如果第一个表达式的布尔值为true，则返回第二个表达式的值，否则返回第三个表达式的体现 例**

```js
't' ? 'hello'  : 'wrold' //"hello"
0 ? 'hello' : "world" //"world*
```

**二进制位运算符**
**二进制运算符用于直接对二进制位进行计算，共7个**
- 二进制或运算符（or）：符号为|，表示若两个二进制位都为0，则结果为0，否则为1。
- 二进制与运算符（and）：符号为&，表示若两个二进制位都为1，则结果为1，否则为0。
- 二进制否运算符（not）：符号为~，表示对一个二进制位取反。
- 异或运算符（xor）：符号为^，表示若两个二进制位不相同，则结果为1，否则为0。
- 左移运算符（left shift）：符号为<<，详见下文解释。
- 右移运算符（right shift）：符号为>>，详见下文解释。
- 头部补零的右移运算符（zero filled right shift）：符号为>>>，详见下文解释。

**异或运算有一个特殊运用，连续对两个数a和b进行3次异或运算，a ^= bl;b^ =;a^= b;可以呼唤它们的值，，使用异或运算可以在不引入临时变量的前提下，互换两个变量的值**

```js
var a = 10;
var b = 99;

a ^= b,b ^= a,a ^= b;

a //99
b //10 
```

```js
//异或运算也可以用来取整
12.9 ^ 0 //12
```

**开关作用**
**位运算符可以用作设置对象属性的开关**

**其他运算符，运算顺序**
**void运算符**
**void运算符的作用是执行一个表达式，然后不返回任何值，或者说返回undefined**

```js 
void 0; //undefined
void (0); //undefined
//建议采用后一种形式，因为void运算符优先性很高，不使用括号，容易造成错误的结果，例如 void 4 +7 实际上等同于 (void 4)+7
```

**逗号运算符**
**逗号运算符用于对两个表达式求值，并返回一个表达式的值**

```js
'a','b' //"b"

var x = 0;
var y = (x++;10);
x //1
y //10
```

**上面代码中，逗号运算符返回后一个表达式的值**

**运算顺序**
**优先级**

**圆括号()可以提高运算的优先级**

**左结合与右结合**
**大多数情况，计算顺序从左到右，叫做运算符的左结合**
**少数运算符计算顺序从右到左，叫做运算符的右结合，其中，最主要的是赋值运算符(=)和三元条件运算符(?:)**
**指数运算符(`**`)也是右结合的**

---

## 语法

**数据类型的转换**
**强制转换主要是用Number()、String()和Boolean()三个函数，手动将各种类型的值，分别转换成数字、字符串或者布尔值**

**Number()函数，可以将任何类型的值转化成数值**
**(1)原始类型值**

```js
//数值，转换后还是原来的值
Number(324) //324

//字符串，如果可以被解析为数值，则转换为相应的数字
Number('324') //324

//字符串，如果不可以被解析为数值，则返回NaN
Number('324abc') //NaN

//空字符串为0
Number('') //0

//布尔值，true为1，false转为0
Number(true) //1
Number(false) //0

//undefined:转出NaN
Number(undefined) //NaN

//null:转成0
Number(null) //0
```

**Number函数只要有一个字符无法转成数值，整个字符串就会转为NaN 例**

```js
parseInt('42 cats') //42
Number('42 cats') //NaN

//parseInt逐个解析，而Number整体转换
```

**parseInt和Number函数都会自动过滤掉一个字符串前导和后缀的空格**

**(2)对象**
**Number方法的参数是对象时，将返回NaN,除非是包含单个数值的数值**

```js
Number({a:1}) //NaN
Number([1,2,3])//NaN
Number([5]) //5
```

**String()函数可以将任意类型的数值转化成字符串，规则如下**
**(1)原始类型值**
- **数值：** 转为相应的字符串
- **字符串：** 转换后还是原来的值
- **布尔值：** true转为字符串"true",false转为字符串"false"
- **undefined:** 转为字符串"undefined"
- **null：** 转为字符串"null"

**(2)对象**
**String方法的参数如果是对象，返回一个类型字符串，，如果是数组，返回该数组的字符串形式**
1. 调用对象自身的valueOf方法，如果返回原始类型的值，则直接对该值使用Number函数，不再进行后续步骤
2. 如果valueOf方法返回的还是对象，则改为调用对象自身的toString方法，如果toString方法返回的是原始类型的值，则对该值使用Number函数，不再进行后续步骤
3. 如果toString方法返回的是对象，就报错

```js
String({a:1}) //"[object Object]"
String([1,2,3]) //"1,2,3"
```

**String方法转换规则与Number方法基本相同，只是互换了valueOf方法和toString方法的执行顺序**
1. 先调用对象自身的toString方法，如果返回原始类型的值，则对该值使用String函数，不在进行以下步骤
2. 如果toString方法返回的是对象，再调用原对象的valueOf方法，如果valueOf方法返回原始类型的值，则对该值使用String函数，不再进行以下步骤
3. 如果valueOf方法返回的是对象，就报错


**Boolean()**
**Boolean()函数可以将任意类型的值转为布尔值**
**除了以下五个值的转换结果为false，其他值全为true**
- undefined
- null
- 0(包含-0和+0)
- NaN
- ''(空字符串)

**注意，所有对象(包括空对象)的转换结果都是true,甚至连false对应的布尔对象new Boolean(false)也是true**
**对象的布尔值为true**

**自动转换**
**第一种情况，不同类型数据的互相运算**
`123 + 'abc' //"123abc"`

**第二种情况，对非布尔值类型的数据求布尔值**

```js
if('abc'){
  console.log('hello')
}//"hello"
```

**第三种情况，对非数值类型的值使用一元运算符(即+和-)**

```js
+{foo:'bar'} //NaN
-[1,2,3] //NaN
```

**自动转化具有不确定性，不易出错，建议在预期为布尔值、数值、字符串的地方，使用Boolean、Number和String函数进行显式转换**

**自动转换为布尔值**
**除了以下五个值，其他都是自动转为true**
- undefined
- null
- +0 或 -0
- NaN
- '' (空字符串)

**自动转换为字符串**

**自动转换为数值**

---

## 错误处理机制

**1.Error实例对象**

```js
var err = new Error("出错了")
err.message//"出错了"
```

**Error实例对象必须有message属性，表示出错是的提示信息**

**2.原生错误类型**

**2.1 SyntaxError对象**
**SyntaxError对象是解析代码时发生的语法错误**

```js
//变量名错误
var 1a;
// Uncaught SyntaxError: Invalid or unexpected token

//缺少括号
console.log'hello');
// Uncaught SyntaxError: Unexpected string
```

**2.2 ReferenceError对象**
**Reference 对象是引用一个不存在的变量是发生的错误

```js
//使用一个不存在的变量
unknowVariable
// Uncaught ReferenceError: unknownVariable is not defined
```

**另一种触发场景式，将一个值分配给无法分配的对象，比如对函数的运行结果或者this赋值**

```js
//等号左侧不是变量
console.log() = 1
//Uncaught ReferenceError: Invalid left-hand side in assignment

//this 对象不能手动赋值
this = 1
//ReferenceError: Invalid left-hand side in assignment
```

**2.3 RangeErroe对象**
**RangeError对象是一个值超出有效范围是发生的错误，主要有几种情况，一是数组长度为负数，而是Number对象的方法参数超出范围，以及函数堆栈超过最大值**

```js
//数组长度不得为负数
new Array(-1)
//Uncaught RangeError: Invalid array length
```

**2.4 TypeError对象**
**TypeError对象是变量或参数不是预期类型时发生的错误，比如，对字符串，布尔值，数值等原始类型的值使用new命令，就会抛出这种错误，因为new命令的参数应该是一个构造函数**

```js
new 123 
// Uncaught TypeError: number is not a func
var obj = {}；
obj.unknowMethod()
// Uncaught TypeError: obj.unknownMethod is not a function
```

**2.5 URIError对象**
**URIError对象是URI相关函数的参数不正确时抛出的错误，主要涉及`encodeURI()`、`decodeURI()`、`encodeURIComponent()`、`decodeURIComponent()`、`escape()`和`unescape()`这六个函数

```js
decodeURI('%2')
//URIError:URI malformed
```

**2.6 EvalError对象**
**eval函数没有被正确执行时，会抛出EvalError错误，该错误类型已不再使用，只是为保证与以前代码兼容，才继续保留**

**2.7 总结

```js
var err1 = new Error('出错了！');
var err2 = new RangeError('出错了，变量超出有效范围！');
var err3 = new TypeError('出错了，变量类型无效！');

err1.message // "出错了！"
err2.message // "出错了，变量超出有效范围！"
err3.message // "出错了，变量类型无效！"
```

**3.自定义错误**

```js
function UserError(message){
  this.message = message||'默认信息';
  this.name = 'UserError';
}
UserError.prototype = new Error();
UserError.prototype.constructor = UserError;
```

**定义了一个错误对象UserError,让它继承Error对象，然后就可以生产这种自定义类型的错误**

```js
new UserError('这是自定义的错误！');
```

**4.throw 语句**
**throw语句的作用是手动中断程序，抛出一个错误**
```js
if(x<=0){
  throw new Error('x必须为正数');
}
// Uncaught ReferenceError: x is not defined
```
**上面代码，如果x小于等于0，就手动抛出一个错误，告诉用户x的值不正确，整个程序会在这里中断执行，throw抛出的错误是它的参数，这是一个Error实例**

**throw也可以抛出自定义错误**

```js
function UserError(message){
  this.message = message||'默认信息';
  this.name = 'UserError';
}
throw new UserError("出错了！");
// Uncaught UserError {message: "出错了！", name: "UserError"}
```

**上面代码，throw抛出的是一个UserError实例**

**实际上，throw可以抛出任何类型的值**

```js
// 抛出一个字符串
throw 'Error！';
// Uncaught Error！

// 抛出一个数值
throw 42;
// Uncaught 42

// 抛出一个布尔值
throw true;
// Uncaught true

// 抛出一个对象
throw {
  toString: function () {
    return 'Error!';
  }
};
// Uncaught {toString: ƒ}
```

**5.try...catch结构**

```js
try{
  f();
}catch(e){
  //处理错误
}
```

**6.finally代码块**
**try...catch结构允许在最后添加一个finally代码块，表示不管是否出现错误，都必须在最后进行的语句**
**下面例子反映了try...catch...finally这三者之间的执行顺序**

```js
function f(){
  try{
    console.log(0);
    throw 'bug';
  }catch(e){
    console.log(1);
    return true;//这句原本会延迟到finally代码块结束后再执行
    console.log(2);//不会执行
  }finally{
    console.log(3);
    return false;//这句会覆盖掉前面那句return
    console.log(4);//不会执行
  }
  console.log(5);//不会运行
}
var result = f();
//0
//1
//3
result
//false
```

