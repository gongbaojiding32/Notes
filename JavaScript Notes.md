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

* 加法运算符：x + y
* 减法运算符： x - y
* 乘法运算符： x * y
* 除法运算符：x / y
* 指数运算符：x ** y
* 余数运算符：x % y
* 自增运算符：++x 或者 x++
* 自减运算符：--x 或者 x--
* 数值运算符： +x
* 负数值运算符：-x

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

``` js
var x = 1; -
x //-1
    -
    (-x) //1
```

**上面代码最后一行圆括号不能少，否则会变成自减运算符**
**数值运算符和负数值运算符都会返回一个新的值，而不会改变原始变量的值**

**指数运算符**
**指数运算符( `**` )完成指数运算，前一个运算子是底数，后一个运算子是指数**

``` js
2 ** 4 //16
```

**注意，指数运算符是右结合，而不是左结合，即多个指数运算符连用时，先进性最右边的计算**

``` js
//相当于2 ** (3 ** 2)
2 ** 3 ** 2
//512
```

**上面代码中，由于是指数运算符是右结合，所以先计算第二个指数运算符，而不是第一个**

**赋值运算符**
**最常见的赋值运算符(=)**
**负值运算符还可以与其他运算符结合，形成变体，如下是与算术运算符的结合**

``` js
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

``` js
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

* `>` 大于运算符
* `<` 小于运算符
* `<=` 小于或等于运算符
* `>=` 大于或等于运算符
* `==` 相等运算符
* `===` 严格相等运算符
* `!=` 不相等运算符
* `!==` 严格不相等运算符

**相等比较和非相等比较，两者规则不一样，对于非相等比较，算法是先看两个运算子是否都是字符串，如果是的，就按照字典顺序比较（实际上是比较 Unicode 码点）；否则，将两个运算子都转成数值，再比较数值的大小。**

**非相等运算符：字符串的比较**

``` js
'cat' > 'dog' //false
'cat' > 'catalog' //false
```

**JavaScript 引擎内部首先比较首字符的 Unicode 码点。如果相等，再比较第二个字符的 Unicode 码点，以此类推。**

``` js
'cat' > 'Cat' //true
```

**上面代码中，小写c的Unicode码点(99)大于大写C的Unicode码点(67), 所以返回true**

**非相等运算符：非字符串的比较**
**如果两个运算子中，至少有一个不是字符串，需要分成以下两种情况**
**(1)原始类型值**
**如果两个运算子都是原始类型的值，则现在转成数值再比较**

``` js
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

``` js
1 > NaN //false
1 <= NaN //false
'1' > NaN //false
    '1' <= NaN //false
NaN > NaN //false
NaN <= NaN //false
```

**(2)对象**
**如果运算子是对象，会转为原始类型的值，再进行比较**
**对象转为原始类型的值，算法是先调用valueOf方法，如果返回的还是对象，再接着调用toString方法**

``` js
var x = [2];
x > '11' //true
//等同于[2].valueOf().toString() > '11'
//即 '2' > '11'

x.valueOf = function() {
    return '1'
};
x > '11' //false
//等同于[2].valueOf() > '11'
//即 '1' > '11'
```

**两个对象之间的比较也是如此**

``` js
[2] > [1] //true
//等同于[2].valueOf().toString() > [1].valueOf().toString()
//即'2' > '1'
[2] > [11] //true
//等同于[2].valueOf().toString() > [11].valueOf().toString()
//即'2' > '11'
{
    x: 2
} >= {
    x: 1
} //true
//等同于{x:2}.valueOf().toString()>={x:1}.valueOf.toString()
//即'[object Object]' >= '[object Object]'
```

**严格相等运算符**
**JavaScript提供两种相等运算符： `==` 和 `===` **
** `==` 比较两个值是否相等**
** `===` 比较两个值是否为"同一个值"，如果两个值不是同一类型， `===` 直接返回false, 而 `==` 会将两个值转换成同一个类型，再用 `===` 进行比较**

`===` 算法
**(1)不同类型的值**
**两个值类型不同，直接返回false**

``` js
1 === "1" //false
true === 'true' //false
```

**(2)同一类的原始类型值**
**同一类型的原始类型的值(数值、字符串、布尔值)比较时，值相同就返回true，值不同就返回false**

``` js
1 === 0x1 //true
```

**上面代码比较的是十进制的1和十六进制的1，因为类型和值都相同，所以返回true**

**注意NaN与任何值都不相等(包括自身)，另外正0等于负0**

``` js
NaN === NaN //false
    +
    0 === -0 //true
```

**(3)复合类型值**
**两个复合类型(对象、数组、函数)的数据比较时，不是比较值是否相等，而是比较它们是否指向同一个地址**

``` js
{} === {} //false
[] === [] //false
(function() {} === function() {}) //false
```

**上面代码分别比较两个空对象，两个空数组，两个空函数，结果都不相等，原因是对于复合类型的值， `===` 比较的它们是否引用同一个内存地址，而运算符两边的空对象、空数组、空函数的值，都存放在不同的内存地址，结果当然是false**

**如果两个变量引用同一个对象，则它们相等**

``` js
var v1 = {};
var v2 = v1;
v1 === v2 //true
```

**注意，对于两个对象的比较， `===` 比较的是地址, 而大于或小于运算符比较的是值**

``` js
var obj1 = {};
var obj2 = {};

obj1 > obj2 //false
obj1 < obj2 //false
obj1 === obj2 //false

//上面三个比较，前两个比较的是值，最后一个比较的是地址，所以都返回false
```

**(4)undefined和null**
**undefined和null与自身严格相等**

``` js
undefined === undefined //true
null === null //true
```

**由于变量声明后默认值是undefined，因此两个只声明未赋值的变量是相等的**

``` js
var v1;
var v2;
v1 === v2 //true
```

**严格不相等运算符**
** `！==` 的算法是先求严格相等运算符的结果，再返回相反值**

``` js
1 !== '1' //true
    //等同于
    !(1 === '1')
```

**相等运算符**
**(1)原始类性值**

``` js
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

'' == false // true
    // 等同于 Number('') === Number(false)
    // 等同于 0 === 0

    '1' == true // true
// 等同于 Number('1') === Number(true)
// 等同于 1 === 1

'\n  123  \t' == 123 // true
// 因为字符串转为数字时，省略前置和后置的空格
```

**(2)对象与原始类性值比较**

``` js
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

``` js
false == null //false
false == undefined //false

0 == null //false
0 == undefined //false

undefined == null //true
//undefined和null相互比较结果为true
```

**(4)相等运算符的缺点**

``` js
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

**上面这些表达式都不同于直觉，容易出错，不建议使用 `==` ，最好只使用 `===` **

**不相等运算符**
** `!=` 的算法是求相等运算符的结果，然后返回相反值**

``` js
1 != '1' //false

    //等同于
    !(1 == '1')
```

**布尔运算符**
**布尔运算符用于将表达式转为布尔值，包含四个运算符**

* 取反运算符：!
* 且运算符：&&
* 或运算符：||
* 三元运算符：?:

**取反运算符(!)**
** `!` 用于将布尔值变为相反值，即true变成false，false变成true**
**以下六个值取反后为true，其他都为false**

* undefined
* null
* false
* 0
* NaN
* 空字符串('')

``` js
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

``` js
!!x
//等同于
Boolean(x)
//两次取反就是将一个值转为布尔值的简便写法
```

**且运算符(&&)**
** `&&` 用于多个表达式的求值**

``` js
't' && '' // ""
't' && 'f' // "f"
't' && (1 + 2) // 3
'' && 'f' // ""
'' && '' // ""

var x = 1;
(1 - 1) && (x += 1) // 0
x // 1
```

**上面代码最后一个例子，由于且运算符的第一个运算子的布尔值为false，则直接返回它的值0, 而不再对第二个运算子求值，所以X的值没变**

**跳过第二个运算子的机制被称为短路，例**

``` js
if (i) {
    doSomething();
}

//等价于
i && doSomething();
```

**后一种不易看出目的，也不易除错，谨慎使用**
**&&运算符可多个连用，, 返回第一个布尔值为false的值，如果所有布尔值为true, 则返回最后一个表达式的值**

``` js
true && 'foo' && '' && 4 && 'foo' && true
//''

1 && 2 && 3
//3
```

**或运算符(||)**
**如果第一个运算子的布尔值为true，则返回第一个运算子的值，且不再对第二个运算子求值，如果第一个运算子的布尔值为false，则返回第二个运算子的值**

``` js
't' || '' //"t"
't' || 'f' //"t"
'' || 'f' //"f"
'' || '' // ""
```

**短路规则同样适用**

``` js
var x = 1;
true || (x = 2) //true
x //1
```

**||运算符可多个连用，这是返回第一个布尔值为true的表达式的值，如果所有表达式都为false，则返回最后一个表达式的值**

``` js
false || 0 || '' || 4 || 'foo' || true
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

* 二进制或运算符（or）：符号为|，表示若两个二进制位都为0，则结果为0，否则为1。
* 二进制与运算符（and）：符号为&，表示若两个二进制位都为1，则结果为1，否则为0。
* 二进制否运算符（not）：符号为~，表示对一个二进制位取反。
* 异或运算符（xor）：符号为^，表示若两个二进制位不相同，则结果为1，否则为0。
* 左移运算符（left shift）：符号为<<，详见下文解释。
* 右移运算符（right shift）：符号为>>，详见下文解释。
* 头部补零的右移运算符（zero filled right shift）：符号为>>>，详见下文解释。

**异或运算有一个特殊运用，连续对两个数a和b进行3次异或运算，a ^= bl; b^ =; a^= b; 可以呼唤它们的值，，使用异或运算可以在不引入临时变量的前提下，互换两个变量的值**

``` js
var a = 10;
var b = 99;

a ^= b, b ^= a, a ^= b;

a //99
b //10 
```

``` js
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
**指数运算符( `**` )也是右结合的**

---

## 语法

**数据类型的转换**
**强制转换主要是用Number()、String()和Boolean()三个函数，手动将各种类型的值，分别转换成数字、字符串或者布尔值**

**Number()函数，可以将任何类型的值转化成数值**
**(1)原始类型值**

``` js
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

``` js
parseInt('42 cats') //42
Number('42 cats') //NaN

//parseInt逐个解析，而Number整体转换
```

**parseInt和Number函数都会自动过滤掉一个字符串前导和后缀的空格**

**(2)对象**
**Number方法的参数是对象时，将返回NaN, 除非是包含单个数值的数值**

``` js
Number({
    a: 1
}) //NaN
Number([1, 2, 3]) //NaN
Number([5]) //5
```

**String()函数可以将任意类型的数值转化成字符串，规则如下**
**(1)原始类型值**

* **数值：** 转为相应的字符串
* **字符串：** 转换后还是原来的值
* **布尔值：** true转为字符串"true", false转为字符串"false"
* **undefined:** 转为字符串"undefined"
* **null：** 转为字符串"null"

**(2)对象**
**String方法的参数如果是对象，返回一个类型字符串，，如果是数组，返回该数组的字符串形式**

1. 调用对象自身的valueOf方法，如果返回原始类型的值，则直接对该值使用Number函数，不再进行后续步骤
2. 如果valueOf方法返回的还是对象，则改为调用对象自身的toString方法，如果toString方法返回的是原始类型的值，则对该值使用Number函数，不再进行后续步骤
3. 如果toString方法返回的是对象，就报错

``` js
String({
    a: 1
}) //"[object Object]"
String([1, 2, 3]) //"1,2,3"
```

**String方法转换规则与Number方法基本相同，只是互换了valueOf方法和toString方法的执行顺序**

1. 先调用对象自身的toString方法，如果返回原始类型的值，则对该值使用String函数，不在进行以下步骤
2. 如果toString方法返回的是对象，再调用原对象的valueOf方法，如果valueOf方法返回原始类型的值，则对该值使用String函数，不再进行以下步骤
3. 如果valueOf方法返回的是对象，就报错

**Boolean()**
**Boolean()函数可以将任意类型的值转为布尔值**
**除了以下五个值的转换结果为false，其他值全为true**

* undefined
* null
* 0(包含-0和+0)
* NaN
* ''(空字符串)

**注意，所有对象(包括空对象)的转换结果都是true, 甚至连false对应的布尔对象new Boolean(false)也是true**
**对象的布尔值为true**

**自动转换**
**第一种情况，不同类型数据的互相运算**
`123 + 'abc' //"123abc"` 

**第二种情况，对非布尔值类型的数据求布尔值**

``` js
if ('abc') {
    console.log('hello')
} //"hello"
```

**第三种情况，对非数值类型的值使用一元运算符(即+和-)**

``` js
+{
    foo: 'bar'
} //NaN
-
[1, 2, 3] //NaN
```

**自动转化具有不确定性，不易出错，建议在预期为布尔值、数值、字符串的地方，使用Boolean、Number和String函数进行显式转换**

**自动转换为布尔值**
**除了以下五个值，其他都是自动转为true**

* undefined
* null
* +0 或 -0
* NaN
* '' (空字符串)

**自动转换为字符串**

**自动转换为数值**

---

## 错误处理机制

**1. Error实例对象**

``` js
var err = new Error("出错了")
err.message //"出错了"
```

**Error实例对象必须有message属性，表示出错是的提示信息**

**2. 原生错误类型**

**2.1 SyntaxError对象**
**SyntaxError对象是解析代码时发生的语法错误**

``` js
//变量名错误
var 1 a;
// Uncaught SyntaxError: Invalid or unexpected token

//缺少括号
console.log 'hello');
// Uncaught SyntaxError: Unexpected string
```

**2.2 ReferenceError对象**
**Reference 对象是引用一个不存在的变量是发生的错误

``` js
//使用一个不存在的变量
unknowVariable
// Uncaught ReferenceError: unknownVariable is not defined
```

**另一种触发场景式，将一个值分配给无法分配的对象，比如对函数的运行结果或者this赋值**

``` js
//等号左侧不是变量
console.log() = 1
//Uncaught ReferenceError: Invalid left-hand side in assignment

//this 对象不能手动赋值
this = 1
//ReferenceError: Invalid left-hand side in assignment
```

**2.3 RangeErroe对象**
**RangeError对象是一个值超出有效范围是发生的错误，主要有几种情况，一是数组长度为负数，而是Number对象的方法参数超出范围，以及函数堆栈超过最大值**

``` js
//数组长度不得为负数
new Array(-1)
//Uncaught RangeError: Invalid array length
```

**2.4 TypeError对象**
**TypeError对象是变量或参数不是预期类型时发生的错误，比如，对字符串，布尔值，数值等原始类型的值使用new命令，就会抛出这种错误，因为new命令的参数应该是一个构造函数**

``` js
new 123
// Uncaught TypeError: number is not a func
var obj = {}；
obj.unknowMethod()
// Uncaught TypeError: obj.unknownMethod is not a function
```

**2.5 URIError对象**
**URIError对象是URI相关函数的参数不正确时抛出的错误，主要涉及 `encodeURI()` 、 `decodeURI()` 、 `encodeURIComponent()` 、 `decodeURIComponent()` 、 `escape()` 和 `unescape()` 这六个函数

``` js
decodeURI('%2')
//URIError:URI malformed
```

**2.6 EvalError对象**
**eval函数没有被正确执行时，会抛出EvalError错误，该错误类型已不再使用，只是为保证与以前代码兼容，才继续保留**

**2.7 总结

``` js
var err1 = new Error('出错了！');
var err2 = new RangeError('出错了，变量超出有效范围！');
var err3 = new TypeError('出错了，变量类型无效！');

err1.message // "出错了！"
err2.message // "出错了，变量超出有效范围！"
err3.message // "出错了，变量类型无效！"
```

**3. 自定义错误**

``` js
function UserError(message) {
    this.message = message || '默认信息';
    this.name = 'UserError';
}
UserError.prototype = new Error();
UserError.prototype.constructor = UserError;
```

**定义了一个错误对象UserError, 让它继承Error对象，然后就可以生产这种自定义类型的错误**

``` js
new UserError('这是自定义的错误！');
```

**4.throw 语句**
**throw语句的作用是手动中断程序，抛出一个错误**

``` js
if (x <= 0) {
    throw new Error('x必须为正数');
}
// Uncaught ReferenceError: x is not defined
```

**上面代码，如果x小于等于0，就手动抛出一个错误，告诉用户x的值不正确，整个程序会在这里中断执行，throw抛出的错误是它的参数，这是一个Error实例**

**throw也可以抛出自定义错误**

``` js
function UserError(message) {
    this.message = message || '默认信息';
    this.name = 'UserError';
}
throw new UserError("出错了！");
// Uncaught UserError {message: "出错了！", name: "UserError"}
```

**上面代码，throw抛出的是一个UserError实例**

**实际上，throw可以抛出任何类型的值**

``` js
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
    toString: function() {
        return 'Error!';
    }
};
// Uncaught {toString: ƒ}
```

**5.try... catch结构**

``` js
try {
    f();
} catch (e) {
    //处理错误
}
```

**6.finally代码块**
**try... catch结构允许在最后添加一个finally代码块，表示不管是否出现错误，都必须在最后进行的语句**
**下面例子反映了try... catch... finally这三者之间的执行顺序**

``` js
function f() {
    try {
        console.log(0);
        throw 'bug';
    } catch (e) {
        console.log(1);
        return true; //这句原本会延迟到finally代码块结束后再执行
        console.log(2); //不会执行
    } finally {
        console.log(3);
        return false; //这句会覆盖掉前面那句return
        console.log(4); //不会执行
    }
    console.log(5); //不会运行
}
var result = f();
//0
//1
//3
result
//false
```

``` js
function f() {
    try {
        throw '出错了！';
    } catch (e) {
        console.log('捕捉到内部错误');
        throw e; // 这句原本会等到finally结束再执行
    } finally {
        return false; // 直接返回
    }
}

try {
    f();
} catch (e) {
    // 此处不会执行
    console.log('caught outer "bogus"');
}

//  捕捉到内部错误
//上面代码中，进入catch代码块之后，一遇到throw语句，就会去执行finally代码块，其中有return false语句，因此就直接返回了，不再会回去执行catch代码块剩下的部分了。
```

---

## 编程风格 

**缩进**
**行首的空格和Tab键，都可以产生缩进效果**

**区块**
**建议总是用大括号表示区块**
**表示区块起首的大括号，不需另起一行**

**圆括号**
**一种是表示函数的调用，另一种表示表达式的组合**
**可以使用空格，区分两种不同的括号**
**1. 表示函数调用时，函数名与左括号之间没有空格**
**2. 表示函数定义时，函数名与左括号之间没有空格**
**3. 其他情况，前面位置的语法元素与左括号之间，都有一个空格**

**行尾的分号不要省略**
** `do...while` 循环是有分号的**

``` js
do {
    a--;
} while (a > 0); //分号不能省略
```

**函数表达式要使用分号**

``` js
var f = function f() {

};
```

**如果continue、break、return和throw这四个语句后，直接跟着换行符，则会自动添加分号，如果return语句返回的是一个对象的字面量，起首的大括号一定要写在同一行**

**全局变量**
**全局变量对于代码的模块化和重复使用，非常不利**
**不得不使用全局变量，可以考虑大写字母表示变量名，容易看出**

**变量声明**
**JavaScript会自动将变量声明提升到代码块的头部，最好把变量声明都放在代码块的头部**
**函数内部的变量声明，都应该放在函数的头部**

**with语句，可以减少代码的书写，但不建议使用**

**相等和严格相等**

``` js
0 == '' // true
1 == true // true
2 == true // false
0 == '0' // true
false == 'false' // false
false == '0' // true
' \t\r\n ' == 0 // true
```

**建议不要使用相等运算符( `==` ), 只使用严格相等运算符( `===` )**

**语句的合并，不要讲不通目的的语句，合并成一行**

**自增和自减运算符**

``` js
++x
//等同于
x += 1;
```

**建议自增( `++` )和自减( `--` )运算符尽量使用 `+=` 和 `-+` 代替**

** `switch...case` 结构**
** `switch...case` 结构要求，每一个case的最后一行必须是break语句，否则会接着运行下一个case，会造成代码冗长**

``` js
function doAction(action) {
    switch (action) {
        case 'hack':
            return 'hack';
        case 'slash':
            return 'slash';
        case 'run':
            return 'run';
        default:
            throw new Error('Invalid action.');
    }
}
```

**上面代码改写成对象结构**

``` js
function doAction(action) {
    var actions = {
        'hack': function() {
            return 'hack';
        },
        'slash': function() {
            return 'slash';
        },
        'run': function() {
            return 'run';
        }
    };

    if (typeof actions[action] !== 'function') {
        throw new Error('Invalid action.');
    }

    return actions[action]();
}
```

**建议 `switch...case` 结构可以用对象结构代替**

**console对象与控制台**
**1.console对象**
**常见用途有两个**

* 调式程序，显示网页代码运行时的错误信息
* 提供了一个命令行接口，用来与网页代码互动

**开发者工具顶端多个面板**

* **Elements:**查看网页的HTML源码和CSS代码
* **Resources:**查看网页加载的各种资源文件（比如代码文件、字体文件 CSS 文件等），以及在硬盘上创建的各种内容（比如本地缓存、Cookie、Local Storage等）。
* **Network:**查看网页的HTTP通信情况
* **Sources:**查看网页加载的脚本源码
* **Timeline:**查看网页的性能情况，比如CPU和内存消耗
* **Console：**用来运行JavaScript命令

**2.console对象的静态方法**
**2.1 `console.log()` , `console,info()` , `console.debug()` **
** `console.log()` 用于在控制台输出信息，可以接受一个或多个参数，将它们连接起来输出**
** `console.log` 方法会自动在每次输出的结尾，添加换行符**

``` js
console.log('%s + %s = %s', 1, 1, 2)
//1+1=2
```

**如上代码，如果第一个参数是格式字符串，console.log方法讲依次用后面的参数替换占位符，然后在进行输出**
**console.log方法支持以下占位符，不同数据类型的数据必须使用对应的占位符**

* %s 字符串
* %d 整数
* %i 整数
* %f 浮点数
* %o 对象的链接
* %c CSS格式字符串

``` js
var number = 11 * 9;
var color = 'red';

console.log('%d %s balloons', number, color);
//99 red balloons
```

**使用%c占位符时，对应的参数必须是CSS代码，用来输出内容进行CSS渲染**

**console.log方法的两种参数格式，可以结构一起使用**

``` js
console.log('%s + %s', 1, 1, '=2')
//1+1=2
```

**如果参数是一个对象, console.log会显示对象的值**

**console.info用法和console.log一样，只不过console.info方法会在输出信息的前面，加上一个蓝色图标**

**console.debug方法与console.log方法类似，会在控制台调试信息，但只有在打开显示级别在verbose的情况下，才会显示**

**console对象的所有方法，都可以被覆盖**

``` js
['log', 'info', 'warn', 'error'].forEach(function(method) {
    console[method] = console[method].bind(
        console,
        new Date().toISOString()
    );
});

console.log("出错了！")
//2019-12-31T02:22:58.781Z 出错了！
```

**2.2 `console.warn()`  `console.error()` **
**warn方法和error方法也是在控制台输出信息, warn方法输出信息时，在最前面加一个黄色三角，表示警告；error方法输出信息时，在最前面加一个红色的叉，表示出错，同时，还会高亮显示输出文字和错误发生的栈**
**log方法是写入标准输出, warn方法和error方法是写入标准错误**

**2.3 console.table()**
**对于某些复合类型的数据，console.table方法可以将其转为表格显示**

``` js
var languages = [{
        name: "JavaScript",
        fileExtension: ".js"
    },
    {
        name: "TypeScript",
        fileExtension: ".ts"
    },
    {
        name: "CoffeeScript",
        fileExtension: ".coffee"
    }
];

console.table(languages);
```

**2.4 console.count()**
**count次数用于计数，输出它被调用了多少次**

**2.5 console.dir()、console.dirxml()方法**
**dir方法用来检查一个对象进行检查，并以易于阅读和打印的格式显示**

``` js
console.log({
    f1: 'foo',
    f2: 'bar'
})
// Object {f1: "foo", f2: "bar"}

console.dir({
    f1: 'foo',
    f2: 'bar'
})
// Object
//   f1: "foo"
//   f2: "bar"
//   __proto__: Object
```

**dir方法输出的结果，比log方法更易读，信息也更丰富**
**该方法对于输出DOM对象非常有用，因此会显示DOM对象的所有属性**

**dirxml方法用于以目录树的形式，显示DOM节点**

**如果参数不是DOM节点，而是普通JavaScript对象，console.dirxml等同于console.dir**

``` js
console.dirxml([1, 2, 3])
//等同于
console.dir([1, 2, 3])
```

**2.6 `console.assert()` **
**console.assert方法主要用于程序运行过程中，进行条件判断，如果条件不满足，就显示一个错误，但不中断程序运行，这样就相当于提示用户，内部状态不正确**

**接受两个参数，第一个参数是表达式，第二个参数是字符串，只有当第一个参数为false，才会提示有错误，在控制台输出第二个参数，否则不会有任何结果**

``` js
console.assert(false, '判断条件不成立')
//Assertion failed:判断条件不成立

//相当于
try {
    if (!false) {
        throw new Errow('判断条件不成立');
    }
} catch (e) {
    console.error(e);
}
```

**2.7 `console.time()` , `console.timeEnd()` **
**这两个方法用于计时，可以算出一个操作所花费的准确时间**

``` js
console.time('Array initialize');

var array = new Array(1000000);
for (var i = array.length - 1; i >= 0; i--) {
    array[i] = new Object();
};

console.timeEnd('Array initialize');
//Array initialize: 233.745849609375ms
```

**time方法表示计时开始，timeEnd方法表示计时结束，它们的参数是计时器的名称，调用timeEnd方法之后，控制台会显示“计时器名称：所耗费的时间**

**2.8 `console.group()` , `console.groupEnd()` , `console.groupCollapsed()` **
**console.group和console.groupEnd两个方法将显示的信息分组，只在输出大量信息时使用，分在一组的信息，可以用鼠标折叠/展开**

``` js
console.group('一级分组');
console.log('一级分组的内容');

console.group('二级分组');
console.log('二级分组的内容');

console.groupEnd(); //二级分组结束
console.groupEnd(); //一级分组结束
```

**console.groupCollapsed方法与console.group方法类似, 唯一区别是该组的内容，在第一次显示时是收起的(collapsed), 而不是展开的**

``` js
console.groupCollapsed('Fetching Data');

console.log('Request Sent');
console.error('Error:Sevver not responding(500)');

console.groupEnd();
```

**2.9 `console.trace()` , `console.clear()` **
**console.trace方法显示当前执行代码在堆栈中的调用路径**

``` js
console.trace()
// console.trace()
//   (anonymous function)
//   InjectedScript._evaluateOn
//   InjectedScript._evaluateAndWrap
//   InjectedScript.evaluate
```

**console.clear方法用于清除当前控制台的所有出输出，将光标回置到第一行，如果用户选中了控制台的"Preserve log"选项，console.clear方法将不起作用**

**3. 控制台命令行API**
**(1)$_属性返回上一个表达式的值**

``` js
2 + 2
//4
$_
//4
```

**(2)$0-$4**
**控制台保存了最近5个Elements面板选中的DOM元素，$0表示倒数一个(最近一个)，$1代表倒数第二个，以此类推直到$4**

**(3)$(selector)**
**$(selector)返回第一个匹配的元素，等同于document.querrySelector()，注意如果页面脚本对$有定义，则会覆盖原始的定义，比如，页面有jQuery，控制台执行$(sekector)就会采用jQuery的实现，返回一个数组**

**(4)$$(selector)返回选中的DOM对象，等同于document.quertSelectorAll**

**(5)$x(path)方法返回一个数组，包含匹配特定XPath表达式的所有DOM元素**

``` js
$x("//p[a]")
//上面代码返回所有包含a元素的p元素
```

**(6)inspect(object)**
**inspect(object)方法打开相关面板，并选中相应的元素，显示它的细节，DOM元素在Elements面板中显示，比如inspect(document)会在 Elements 面板显示document元素。JavaScript 对象在控制台面板Profiles面板中显示，比如inspect(window)。**

**(7)getEventListeners(object)方法返回一个对象，该对象的成员为object登记了回调函数的各种事件(比如click或keydown), 每个事件对应一个数组，数组成员为该事件回调函数**

**(8)keys(object), values(object)**
**keys(object)方法返回一个数组，包含object的所有键名**
**values(object)方法返回一个数组，包含object的所有键值**

**(9) `monitorEvents(object[,events])` , `unmonitorEvents(object[,events])` **
** `monitorEvents(object[,events])` 方法监听特定对象上发生的特定事件，事件发生时，会返回一个Event对象，包含该事件的相关信息，unmonitorEvents方法用于停止监听**
**monitorEvents允许监听同一大类的事件，所有时间可以分成四个大类**

* mouse："mousedown", "mouseup", "click", "dblclick", "mousemove", "mouseover", "mouseout", "mousewheel"
* key："keydown", "keyup", "keypress", "textInput"
* touch："touchstart", "touchmove", "touchend", "touchcancel"
* control："resize", "scroll", "zoom", "focus", "blur", "select", "change", "submit", "reset"

**(10)其他方法**
**命令行API还提供以下方法**

* clear(): 清除控制台的历史
* copy(object): 复制特定DOM元素的剪贴板
* dir(object): 显示特定对象的所有属性，是console.dir方法的别名
* dirxml(object)：显示特定对象的XML形式，是console.dirxml方法的别名

**4.debugger语句**
**debugger语句用于除错，作用是设置断点**

``` js
for (var i = 0; i < 5; i++) {
    console.log(i);
    if (i === 2) debugger;
}
//代码打印出0,1,2后,就会暂停，自动打开源码界面，等待进一步处理
```

---

## 标准库

**1. 概述**
**JS所有其他对象都继承自Object对象，那些对象都是Object的实例**
**Object对象的原生方法分成两类：Object本身的方法与Object的实例方法**
**(1)Object对象本身的方法就是直接定义在Object对象的方法**
`Object print = function(o){console.log(o)};` 
**上面代码，print方法就是直接定义在Object对象上**
**(2)Object的实例方法就是定义在Object原型对象Object.prototype 上的方法，它可以被Object实例直接使用**

``` js
Object.prototype.print = function() {
    console.log(this);
};
var obj = new Object();
obj.print(); //Object
```

**凡是定义在Object.prototype对象上的属性和方法，将被所有实例对象共享**

**2. Object()**
**Object本身是一个函数，如果参数为空(或者为undefined或null)，Object()返回一个空对象**
**如果参数是原始类型的值，Object方法将其转为对应的包装对象的实例**

**3. Object构造函数**
**Object不仅可以当作工具函数使用，还可以当作构造函数使用，即前面可以使用new命令**
**Object构造函数的首要用途，是直接通过它来生成新对象**
`var obj = new Object();` 
**注意 `var obj = new Object();` 与字面量的写法 `var obj = {}` 是等价的，后者是前者的一种简便写法**

**4. Object的静态方法 指部署在Object对象自身的方法**
**4.1 `Object.keys()` , `Object.getOwnPropertyNames()` 都是用来遍历对象的属性**
**Object.keys方法的参数是一个对象，返回一个数组，该数组的成员都是该对象自身的(不是继承的)所有属性名**
**Object.getOwnPropertyNames方法与Object.keys方法类似, 涉及枚举属性时，结果会不一样，Object.keys方法只返回可枚举的属性，Object.getOwnPropertyNames方法返回不可枚举的属性名**
**一般情况，都是用Object.keys方法遍历对象的属性**

**4.2其他方法**
**(1)对象属性模型的相关方法**

* Object.getOwnPropertyDescriptor()：获取某个属性的描述对象。
* Object.defineProperty()：通过描述对象，定义某个属性。
* Object.defineProperties()：通过描述对象，定义多个属性。

**(2)控制对象状态的方法**

* Object.preventExtensions()：防止对象扩展。
* Object.isExtensible()：判断对象是否可扩展。
* Object.seal()：禁止对象配置。
* Object.isSealed()：判断一个对象是否可配置。
* Object.freeze()：冻结一个对象。
* Object.isFrozen()：判断一个对象是否被冻结。

**(3)原型链相关方法**

* Object.create(): 该方法可以指定原型对象和属性，返回一个新的对象
* Object.getPrototypeOf(): 获取对象的Prototype对象

**5. Object的实例方法**
**Object实例对象的方法，主要有以下6个**

* Object.prototype.valueOf(): 返回当前对象对应的值
* Object.prototype.toString(): 返回当前对象对应的字符串形式
* Object.prototype.toLocaleString(): 返回当前对象对应的本地字符串形式
* Object.prototype.hasOwnProperty(): 判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性
* Object.prototype.isPrototypeOf(): 判断当前对象是否为另一个对象的原型
* Object.prototype.propertyIsEnnumerable()：判断某个属性是否可枚举

---

**属性描述对象**
**1. 概述**
**属性描述对象提供6个元属性
**(1)value**
**value是该属性的属性值，默认为undefined**
**(2)writable**
**writable是一个布尔值，表示属性值(value)是否可改变(是否可写)，默认为true**
**(3)enumerable**
**enumerable是一个布尔值，表示该属性是否可遍历，默认为true, 如果设为false，会是某些操作(for..in循环, Object.keys())跳过该属性**
**(4)configurable**
**configurable是一个布尔值，表示可适配性，默认为true，如果设为false，将阻止某些操作改写该属性，比如无法删除该属性，也不得改变该属性的属性描述对象(value属性除外)，configurable属性控制力描述对象的可写性**
**(5)get**
**get是一个函数，表示该属性的取值函数(getter), 默认为undefined**
**(6)set**
**set是一个函数，表示该属性的存在函数(setter), 默认为undefined**

**2. Object.getOwnPropertyDescriptor()方法可以获取属性描述对象, 它的第一个参数是目标对象，第二个参数是一个字符串，对应目标对象的某个属性名**
**Object.getOwnPropertyDescriptor()方法只能用于对象自身的属性，不能用于继承的属性**

**3. Object.getOwnPropertyNames()方法返回一个数组，成员是参数对象自身的全部属性的属性名，不管该属性是否可遍历**

**4. Object.defineProperty(), Object.defineProPerties()**
**Object.defineProperty方法接受三个参数**

* object: 属性所在的对象
* propertyName: 字符串，表示属性名
* attributesObject: 属性描述对象

**如果一次性定义或修改多个属性， 可以使用Object.defineProperties()方法**
**一旦定义了取值函数get(或者存值函数set)，就不能将writable属性设为true，或者同时定义value属性，否则会报错**

``` js
var obj = {};
Object.defineProperty(obj, 'foo', {});
Object.getOwnPropertyDescriptor(obj, 'foo')
//{
//  value:undefined,
//  writable:false,
//  enumerable:false,
//  configurable:false
//}
```

**5. Object.prototype.propertyIsEnumerable()方法返回一个布尔值，用来判断某个属性是否可遍历，注意，只能用于判断对象自身的属性，对于继承的属性一律返回false**

**6. 元属性，属性描述对象的各个属性被称为"元属性"**
**6.1 value**
**6.2 wirtable**
**6.3 enumerable**
**6.4 configurable**

**7. 存取器**
**存值函数称为setter, 使用属性描述对象的set属性；取值对象称为getter，使用属性描述对象的get属性**
**注意，取值函数get不能接受参数，存值函数set只能接受一个参数(即属性的值)**

**8. 对象的拷贝**
**可以通过Object.defineProperty方法来拷贝属性**

**9. 控制对象状态**
**9.1 Object.preventExtensions()方法可以得到一个对象无法再添加新的属性**

**9.2 Object.isExtensible()方法用于检查一个对象是否使用了Object.preventExtensions方法, 也就是说，检查是否可以为一个对象添加属性**

**9.3 Object.seal()**
**Object.seal方法使得一个对象既无法添加新的属性，也无法删除旧的属性**

**9.4 Object.isSealed()方法用于检查一个对象是否使用了Object.seal方法**

**9.5 Object.freeze()方法可以使得一个对象无法添加新属性，无法删除旧属性、也无法改变属性的值，使得这个对象实际上变成了常量**

**9.6 Object.isFrozen()方法用于检查一个对象是否使用了Object, freeze方法**
**Object.isFrozen唯一用途是，确认某个对象没有被冻结后，再对它的属性赋值**

**9.7 局限性**
**锁定对象的可写性有一个漏洞: 可以通过改变原型对象，来为对象增加属性，另一个局限是，如果属性值是对象， 上面这些方法只能冻结属性指向的对象，而不能冻结对象本身的内容**

---

**Array对象**

**1. 构造函数**
**Array是JavaScript的原生对象，同时也是一个构造函数，可以用它生成新的数组, 不建议使用它生成新的数组，直接使用数组字面量是更好的做法**

**2. 静态方法**
**2.1 Array.isArray() 方法返回一个布尔值，表示参数是否位数字，可以补足typeof运算符的不足**

**3. 实例方法**
**3.1 valueOf(), toString()**
**valueOf方法是一个所有对象都拥有的方法，表示对该对象求值，不同对象的valueOf方法不尽一致，数组的valueOf方法返回数组本身**
**toString方法也是对象的通用方法，数组的toString方法返回数组的字符串形式**

**3.2 push(), pop()**
**push方法用于在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度，该方法会改变原数组**
**pop方法用于删除数组的最后一个元素，并返回该元素，该方法会改变原数组**
**对空数组使用pop方法，不会报错，但会返回undefined**
**push和pop结合使用，就构成了后进先出的栈结构(stack)**

**3.3 shift(), unshift()**
**shift()方法用于删除数组的第一个元素，并返回该元素，该方法会改变原数组**
**unshift()方法用于在数组的第一个位置添加元素，并返回添加新元素后的数组长度，该方法会改变原数组**
**unshift()方法可以接受多个参数，这些参数都会添加到目标数组的头部**

**3.4 join()方法以指定参数作为分隔符，将所有数组成员连接为一个字符串返回，如果不提供参数，默认用逗号分隔**

``` js
var a = [1, 2, 3, 4];

a.join(' ') // '1 2 3 4'
a.join(' | ') // "1 | 2 | 3 | 4"
a.join() // "1,2,3,4"
```

**如果数组成员是undefined或null或空位，会被转成空字符串**

``` js
[undefined, null].join('#')
//'#'

['a', , 'b'].join('-')
//'a-b'
```

**通过call方法也可用于字符串或类似数组的对象**

**3.5 concat()方法用于多个数组的合并，将新数组的成员，添加到原数组成员的后部，然后返回一个新数组，原数组不变**

``` js
['hello'].concat(['world'])
// ["hello", "world"]

['hello'].concat(['world'], ['!'])
// ["hello", "world", "!"]

[].concat({
    a: 1
}, {
    b: 2
})
// [{ a: 1 }, { b: 2 }]

[2].concat({
    a: 1
})
// [2, {a: 1}]
```

**除了数组作为参数，concat也接受其他类型的值作为参数，添加到目标数组的尾部**

**3.6 reverse()方法用于颠倒排列数组元素，返回改变后的数组，注意，该方法将改变原数组**

**3.7 slice()方法用于提取目标数组的一部分，返回一个新数组，原数组不变**

**splice()方法用于删除原数组的一部分成员，并可以再删除的位置添加新的数组成员，返回值是被删除的元素，该方法会改变原数组**
**splice的第一个参数是删除的起始位置(从0开始), 第二个参数被删除的元素个数，如果后面还有更多的参数，则表示这些就是要被插入新数组的新元素**

**3.9 sort()方法对数组成员进行排序，默认是按照字典顺序排序、排序后，原数组将改变**

**3.10 map()方法将数组的所有成员依次传入参数函数，然后把每一次的执行结果组成一个新数组返回**
**map方法接受一个函数作为参数，该函数调用时，map方法向它传入三个参数：当前成员、当前位置和数组本身**

``` js
[1, 2, 3].map(function(elem, index, arr) {
    return elem * index;
});
// [0, 2, 6]
//上面代码中，map方法的回调函数有三个参数，elem为当前成员的值，index为当前成员的位置，arr为原数组（[1, 2, 3]）。
```

**map方法还可以接受第二个参数，用来绑定回调函数内部的this变量**

``` js
var arr = ['a', 'b', 'c'];
[1, 2] map(function(e) {
    return this[e];
}, arr)
//['b','c']
//上面代码通过map方法的第二个参数，将回调函数内部的this对象，指向arr数组
```

**如果数组有空位，map方法的回调函数在这个位置不会执行，会跳过数组的空位**
**map方法不会跳过undefined和null，但会跳过空位**

**3.11 forEach()**
**forEach方法与map方法类似，但forEach方法不返回值，只用来操作数据，如果数组遍历目的是为了得到返回值，那么使用map方法，否则使用forEach方法**
**forEach方法无法中断执行，总会将所有成员遍历完，如果希望符合某种条件，就中断遍历，要使用for循环**
**forEach方法不会跳过undefined和null，但会跳过空位**

**3.12 filter()**
**filter()方法用于过滤数组成员，满足条件的成员组成一个新数组返回，其参数是一个函数，所有数组成员依次执行该函数，返回结果为true的成员组成一个新数组返回，该方法不会改变原数组**
**filter方法的参数函数可以接受三个参数：当前成员，当前位置和整个数组**
**filter方法还可以接受第二个参数，用来绑定参数函数内部的this变量**

**3.13 some(), every()**
**两个方法类似断言(assert)，返回一个布尔值，表示判断数组成员是否符合某种条件，该函数接受三个参数(当前成员、当前位置和整个数组)，然后返回一个布尔值**
**some和every方法还可以接受第二个参数，用来绑定参数函数内部的this变量**

**3.14 reduce(), reduceRight()**
**reduce方法和reduceRight方法依次处理数组的每个成员，最终累计为一个值。它们的差别是，reduce是从左到右处理（从第一个成员到最后一个成员），reduceRight则是从右到左（从最后一个成员到第一个成员），其他完全一样。**
**reduce方法和reduceRight方法的第一个参数都是一个函数，该函数接受以下四个参数**
**1. 累积变量，默认为数组的第一个成员**
**2. 当前变量，默认为数组的第二个成员**
**3. 当前位置(从0开始)**
**4. 原数组**
**四个参数中，只有前两个是必须的，后两个可选**

**3.15 indexOf(), lastIndexOf()**
**indexOf方法返回给定元素在数组中第一次出现的位置，如果没有出现则返回-1**
**lastIndexOf方法返回给定元素在数组中最后一次出现的位置，如果没有出现则返回-1**
**注意，两个方法不能用来搜索NaN的位置，即它们无法确定数组成员是否包含NaN**

``` js
[NaN].indexOf(NaN) //-1
[NaN].lastIndexOf(NaN) //-1
```

**两个方法内部，使用严格相等运算符(===)进行比较，而NaN是唯一一个不等于自身的值**

**3.16 链式使用**

``` js
var users = [{
        name: 'tom',
        email: 'tom@example.com'
    },
    {
        name: 'peter',
        email: 'peter@example.com'
    }
];

users
    .map(function(user) {
        return user.email;
    })
    .filter(function(emial) {
        return /^t/.test(email);
    })
    .forEach(function(email) {
        console.log(email);
    });
//"tom@example.com"
//上面代码中，先产生一个所有 Email 地址组成的数组，然后再过滤出以t开头的 Email 地址，最后将它打印出来。
```

---

## 包装对象

**1. 定义**
**所谓包装对象，指的是数值、字符串、布尔值分别相对应的Number、String、Boolean三个原生对象，三个原生对象可以把原生类型的值变成(包装成)对象**

``` js
var v1 = new Number(123);
var v2 = new String('abc');
var v3 = new Boolean(true);

typeof v1 // "object"
typeof v2 // "object"
typeof v3 // "object"

v1 === 123 // false
v2 === 'abc' // false
v3 === true // false
```

**包装对象的设计目的，首先使得"对象"这种类型可以覆盖JavaScript所有的值，整门语言有一个通用的数据模型，其次是使得原始类型的值也有办法调用自己的方法**

**2.实例方法**
**三种包装对象从Object对象继承的方法：valueOf()和toString()**
**2.1 valueOf()方法返回包装对象实例对应的原始类型的值**

```js
new Number(123).valueOf()  // 123
new String('abc').valueOf() // "abc"
new Boolean(true).valueOf() // true
```

**2.2 toString()方法返回对应的字符串形式**

```js
new Number(123).toString() // "123"
new String('abc').toString() // "abc"
new Boolean(true).toString() // "true"
```

**3.原始类型与实例对象的自动转换**

**4.自定义方法**
**除了原生的实例方法，包装对象还可以自定义方法和属性，供类型的值直接调用**

```js
String.prototype.double = function(){
    return this.valueOf()+this.valueOf();
};

'abc'.double()
//abcabc

Number.prototype.doouble = function(){
    return this.valueOf()+this.valueOf();
};

(123).double()//246
//最后123外必须加上圆括号，否则后面的点运算符会被解释成小数点
```

---

## Boolean对象

**1.概述**

```js
if (new Boolean(false)) {
  console.log('true');
} // true

if (new Boolean(false).valueOf()) {
  console.log('true');
} // 无输出
//第一个例子之所以得到true，是因为false对应的包装对象实例是一个对象，进行逻辑运算时，被自动转化成布尔值true（因为所有对象对应的布尔值都是true）。而实例的valueOf方法，则返回实例对应的原始值，本例为false。
```

**Boolean函数的类型转换**

```js
Boolean(undefined) //false
Boolean(null) //false
Boolean(0) // false
Boolean('') // false
Boolean(NaN) // false

Boolean(1) // true
Boolean('false') // true
Boolean([]) // true
Boolean({}) // true
Boolean(function () {}) // true
Boolean(/foo/) // true
```

**使用双重运算符(!)也可以将任意值转为对应的布尔值**

```js
!!undefined // false
!!null // false
!!0 // false
!!'' // false
!!NaN // false

!!1 // true
!!'false' // true
!![] // true
!!{} // true
!!function(){} // true
!!/foo/ // true
```

**一些特殊值，Boolean对象前加不加new，会得到完全相反的结果，要小心**

```js
if(Boolean(false)){
    console.log('true');
}//无输出

if(new Boolean(false)){
    console.log('true');
}//true

if(Boolean(null)){
    console.log('true');
}//无输出

if(new Boolean(null)){
    console.log('true');
}//true
```

---

**Number对象**
**1.概述**
**Number是数值对应的包装对象，即可以作为构造函数，也可以作为工具函数**
**作为构造函数，用于生成为数值的对象**

```js
var n = new Number(1);
typeof n //'object'
//Number对象作为构造函数使用，返回一个值为1的对象
```

**作为工具函数时，可以将任何类型的值转为数值**
`Number(true) //1`

**2.静态属性**
- Number.POSITIVE_INFINITY：正的无限，指向Infinity。
- Number.NEGATIVE_INFINITY：负的无限，指向-Infinity。
- Number.NaN：表示非数值，指向NaN。
- Number.MIN_VALUE：表示最小的正数（即最接近0的正数，在64位浮点数体系中为5e-324），相应的，最接近0的负数为-Number.MIN_VALUE。
- Number.MAX_SAFE_INTEGER：表示能够精确表示的最大整数，即9007199254740991。
- Number.MIN_SAFE_INTEGER：表示能够精确表示的最小整数，即-9007199254740991

**3.实例方法**
**3.1 Number.prototype.toString() 将一个数值转为字符串**
**toString方法只能将十进制的数，转为其他进制的字符串，如果要将其他进制的数，转回十进制，要用parseInt方法**

**3.2 Number.portotype.toFixed() 将一个数转为指定位数的小数，然后返回这个小数对应的字符串**
**toFixed()方法的参数为小数位数，有效范围为0到20，超出范围抛出RangeError错误**
**由于浮点数的原因，小数5的四舍五入是不确定的，使用时要小心**

```js
(10.055).toFixed(2) //10.05
(10.005).toFixed(2) //10.01
```

**3.3 Number.prototype.toExponential()  将一个数转为科学计数法形式**
**toExponential方法的参数是小数点后有效数字的位数，范围为0到20，超出这个范围，会抛出一个 RangeError 错误。**

**3.4 Number.prototype.toPrecision() 将一个数转为指定位数的有效数字**
**该方法的参数为有效数字的位数，范围1到21，超出范围抛出RangeError错误**

**3.5 Number.prototype.toLocalString() 接受一个地区码作为参数，返回一个字符串，表示当前该数字在该地区的书写形式**

```js
(123).toLocaleString('zh-Hans-CN-u-nu-hanidec')
//"一二三"
```

**该方法还可以接受第二个参数配置对象，用来定制指定用途的返回字符串。style属性指定输出样式，默认值是decimal，表示输出十进制形式，如果为percent，表示输出百分数**
**如果style属性为currency,则可以搭配currency属性，输出指定格式的货币字符串形式**

```js
(123).toLocaleString('zh-Hans-CN',{style:'currency',currency:'CNY'})
// "￥123.00
(123).toLocaleString('de-DE',{style:'currency',currency:'EUR'})
// "123,00€"
(123).toLocaleString('de-DE',{style:'currency',currency:'USD'})
// "$123.00"
```

**如果Number.prototype.toLocaleString()省略了参数，则由浏览器自行决定如何处理，通常使用操作系统的地区设定。若该方法使用浏览器不认识的地区码，会抛出一个错误**

**4. 自定义方法**

```js
Number.prototype.add = function (x) {
  return this + x;
};

8['add'](2) // 10


Number.prototype.subtract = function (x) {
  return this - x;
};

(8).add(2).subtract(4)
// 6


//更复杂方法

Number.prototype.iterate = function(){
    var rerult = [];
    for(var i =0;i<=this;i++){
        result.push(i);
    }
    return result;
};
(8).iterate()
//[0,1,2,3,4,5,6,7,8]
```

**注意，数值的自定义方法，只能定义在它的原型对象Number.prototype上面，数值本身是无法自定义属性的**


**String 对象**
**1.概述**
**String对象是JavaScript原生提供的三个包装对象之一，用来生成字符串，可以将任何值转为字符串**

**2. 静态方法**
**2.1 String.fromCharCode() 该方法参数是一个或多个数值，代表Unicode码点，返回值是这些码点组成的字符串**

**3. 实例属性**
**String.prototype.length 返回字符串的长度**

**4. 实例方法**
**4.1 Stirng.prototype.charAt() 返回指定位置的字符，参数从0开始编号的位置**
**如果参数为负数，或大于等于字符串长度，charAt返回空字符串**

**4.2 String.prototype.charCodeAt() 返回字符串指定未知的Unicode码点(十进制表示)，相当于String.fromCHarCode()逆操作**

**4.3 String.prototype.concat() 用于连接两个字符串，返回一个新的字符串，不改变原字符串**

**4.4 String.prototype.slice() 从原字符串取子字符并，不改变原字符串，第一个参数是子字符串开始的位置，第二个参数是字符串的结束位置(不含该位置)**

**4.5 String.prototype.substring() 用于从原字符串取出子字符串并返回，不改变原字符串，，和slice方法横向**

**4.6  String。prototype.substr() 用于从原字符串取出子字符串并返回，不改变原字符串，和slicex相似**

**4.7 String.prototype.indexOf(),String.portotype.lastIndexOf()**
**indexOf方法用于确定一个字符串在另一个字符串中第一次出现的位置，返回结果是匹配开始的位置，如果返回-1，表示不匹配**
**lastIndexOf方法从尾部开始匹配**

**4.8 String.prototype.trim() 用于取出字符串两端的空格，返回一个新字符串，不改变原字符串**
**取出的不仅是空格，还包括制表符(\t,\v),换行符(\n)和回车符(\r)**

**4.9 String.prototype.toLowerCase() 将字符串全部转为小写,String.prototype.toUpperCase() 全部转为大写，都返回一个新字符串，不会改变原字符串**

**4.10 String.prototype.match() 用于确定原字符串是否匹配某个字符串，返回一个数组，成员为匹配的第一个字符串，如果没有找到匹配，则返回null**
**返回的数组还有index和input属性，分别表示匹配字符串开始的位置和原始字符串**

**4.11 String.prototype.search(),String.prototype.replace()**
**search方法基本同于match，但返回值为匹配的第一个的位置，如果如果没有找到匹配返回-1**

**4.12 String.prototype.split() 按照给定规则分割字符串，返回一个由分割出来的子字符串组成的数组**

**4.13 String.prototype.localeCompare() 方法用于比较两个字符串，返回一个整数，如果小于0，表示第一个字符串小于第二个字符串，如果等于0，表示两者相等，如果大于0，表示第一个字符串大于第二个字符串**


**Math对象**
**Math对象提供各种数学功能，该对象不是构造函数，不能生成实例，所有的属性和方法都必须在Math对象上调用**

**1.静态属性**
- Math.E: 常数e
- Math.LN2: 2的自然对数
- Math.LN10: 10的自然对数
- Math.LOG2E: 以2为底的e的对数
- Math.LOG10E: 以10为底的e的对数
- Math.PI: 常数π
- Math.SQRT1_2: 0.5的平方根
- Math.SQRT2:2的平方根

**2.静态方法**
**Math对象提供以下一些静态方法**
- Math.abs(): 绝对值
- Math.ceil():向上取值
- Math.floor():向下取整
- Math.max():最大值 参数为空返回Infinity
- Math.min():最小值 参数为空返回-Infinity
- Math.pow():指数运算
- Math.sqrt():平方根
- Math.log():自然对数
- Math.exp():e的指数
- Math.round():四舍五入
- Math.random():随机数


```js
function ToInteger(x){
    x = Number(x);
    return x < 0 ? Math.ceil(x) : Math.floor(x);
}

ToInteger(3.2) //3
ToInteger(3.5) //3
ToInteger(3.8) //3
ToInteger(-3.2) //-3
ToInteger(-3.5) //-3
ToInteger(-3.8) //-3
```

**三角函数方法**
- Math.sin():返回参数的正弦(参数为弧度值)
- Math.cos():返回参数的余弦(参数为弧度值)
- Math.tan():返回参数的正切(参数为弧度值)
- Math.asin():返回参数的反正弦(返回值为弧度值)
- Math.acos():返回参数的反余弦(返回值为弧度值)
- Math.atan():返回参数的反正切(返回值为弧度值)