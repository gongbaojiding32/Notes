# 11th Dec JavaScript 笔记

## 语法

每个语句以;结尾，语句块{}。

## 注释

//单行注释
/* */多行注释

## 数据类型

1.Number
2.字符串 用''或""括起来的任意文本
3.布尔值 true false
4.&&运算是与运算 只有所有都尉true,&&运算结果才是true
5.||运算式或运算，只有其中一个为true,||运算结果就是true
6.!运算是非运算，true变false，false变true
7.比较运算符，JavaScript中监视使用===比较
8.另一个例外NaN这个特殊Number与所有其它值都不想等，包括它自己，唯一能判断NaN的方法十通过isNaN()函数
9.最后要注意的是浮点数的相等比较，要比较两个浮点数是否相等，只能计算她们之差的绝对值，看是否小于摸个阈值：Math.asb(1/3-(1-2/3))0.0000001; //true
10.null和undefined，null表示一个空的值，undefined表示未定义，大多数情况下，我们都应该用null,undefined仅仅在判断函数参数是否传递的情况下有用

## 数组

数组[] 元素之间用,分隔，另一种常见数组的方法通过Array()函数实现，例如：new Array(1,2,3); 出于代码的可读性，建议使用[] 索引起始值为0

## 对象

JavaScript对象是一组由键-值组成的无序集合，例如；

```js
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
```

要获取一个对象的属性，用对象变量.属性名的方式：person.name; // 'Bob' person.zipcode; // null

## 变量

变量的概念基本上和初中代数的方程变量是一致的，只是在计算机程序中，变量不仅可以是数字，还可以是任意数据类型。

变量在JavaScript中就是用一个变量名表示，变量名是大小写英文、数字、$和_的组合，且不能用数字开头。变量名也不能是JavaScript的关键字，如if、while等。申明一个变量用var语句，比如：

```js
var a; // 申明了变量a，此时a的值为undefined
var $b = 1; // 申明了变量$b，同时给$b赋值，此时$b的值为1
var s_007 = '007'; // s_007是一个字符串
var Answer = true; // Answer是一个布尔值true
var t = null; // t的值是null
```

在JavaScript中，使用等号=对变量进行赋值。可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量，但是要注意只能用var申明一次，例如：

```js
var a = 123; // a的值是整数123
a = 'ABC'; // a变为字符串
```

请不要把赋值语句的等号等同于数学的等号。比如下面的代码：

```js
var x = 10;
x = x + 2;
```

## strict模式

JavaScript在设计之初，为了方便初学者学习，并不强制要求用var申明变量。这个设计错误带来了严重的后果：如果一个变量没有通过var申明就被使用，那么该变量就自动被申明为全局变量：`i = 10; // i现在是全局变量`
启用strict模式的方法是在JavaScript代码的第一行写上：`'use strict';`
这是一个字符串，不支持strict模式的浏览器会把它当做一个字符串语句执行，支持strict模式的浏览器将开启strict模式运行JavaScript。

## 字符串

1.JavaScript的字符串就是用''或""括起来的字符表示。

如果'本身也是一个字符，那就可以用""括起来，比如"I'm OK"包含的字符是I，'，m，空格，O，K这6个字符。

如果字符串内部既包含'又包含"怎么办？可以用转义字符\来标识，比如：'I\'m \"OK\"!'; 表示的字符串内容是：I'm "OK"!
转义字符\可以转义很多字符，比如\n表示换行，\t表示制表符，字符\本身也要转义，所以\\表示的字符就是\。

ASCII字符可以以\x##形式的十六进制表示，例如：'\x41'; // 完全等同于 'A'
还可以用\u####表示一个Unicode字符：'\u4e2d\u6587'; // 完全等同于 '中文'

2.多行字符串
由于多行字符串用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用反引号表示：
`这是一个
多行
字符串`;
3.模板字符串
要把多个字符串连接起来，可以用+号连接：

```js
var name = '小明';
var age = 20;
var message = '你好, ' + name + ', 你今年' + age + '岁了!';
alert(message);
```

如果有很多变量需要连接，用+号就比较麻烦。ES6新增了一种模板字符串，表示方法和上面的多行字符串一样，但是它会自动替换字符串中的变量：

```js
var name = '小明';
var age = 20;
var message = `你好, ${name}, 你今年${age}岁了!`;
alert(message);
```

3.操作字符串
常见操作如下：

```js
var s = 'Hello, world!';
s.length; // 13
```

要获取字符串某个指定位置的字符，使用类似Array的下标操作，索引号从0开始:

```js
var s = 'Hello, world!';

s[0]; // 'H'
s[6]; // ' '
s[7]; // 'w'
s[12]; // '!'
s[13]; // undefined 超出范围的索引不会报错，但一律返回undefined
```

需要特别注意的是，字符串是不可变的，如果对字符串的某个索引赋值，不会有任何错误，但是，也没有任何效果：

```js
var s = 'Test';
s[0] = 'X';
alert(s); // s仍然为'Test'
```

JavaScript为字符串常用方法
1.toUpperCase()把一个字符串全部变为大写
2.toLowerCase()把一个字符串全部变为小写
3.indexOf()会搜索指定字符串出现的位置
4.substring()返回指定索引区间的子串

## 数组2

JavaScript的Array可以包含任意数据类型，并通过索引来访问每个元素。要取得Array的长度，直接访问length属性
请注意，直接给Array的length赋一个新的值会导致Array大小的变化
Array可以通过索引把对应的元素修改为新的值，因此，对Array的索引进行赋值会直接修改这个Array
请注意，如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化
大多数其他编程语言不允许直接改变数组的大小，越界访问索引会报错。然而，JavaScript的Array却不会有任何错误。在编写代码时，不建议直接修改Array的大小，访问索引时要确保索引不会越界。

indexOf
与String类似，Array也可以通过indexOf()来搜索一个指定的元素的位置:

```js
var arr = [10, 20, '30', 'xyz'];
arr.indexOf(10); // 元素10的索引为0
arr.indexOf(20); // 元素20的索引为1
arr.indexOf(30); // 元素30没有找到，返回-1
arr.indexOf('30'); // 元素'30'的索引为2
```

注意了，数字30和字符串'30'是不同的元素。

slice
slice()就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array：
```js
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']
```

注意到slice()的起止参数包括开始索引，不包括结束索引。

如果不给slice()传递任何参数，它就会从头到尾截取所有元素。利用这一点，我们可以很容易地复制一个Array：

```js
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
var aCopy = arr.slice();
aCopy; // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
aCopy === arr; // false
```

push和pop
push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉

unshift和shift
如果要往Array的头部添加若干元素，使用unshift()方法，shift()方法则把Array的第一个元素删掉

sort
sort()可以对当前Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序

reverse
reverse()把整个Array的元素给掉个个，也就是反转

splice
splice()方法是修改Array的“万能方法”，它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素

concat
concat()方法把当前的Array和另一个Array连接起来，并返回一个新的Array
请注意，concat()方法并没有修改当前Array，而是返回了一个新的Array。
实际上，concat()方法可以接收任意个元素和Array，并且自动把Array拆开，然后全部添加到新的Array里

join
join()方法是一个非常实用的方法，它把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串
如果Array的元素不是字符串，将自动转换为字符串后再连接

多维数组
如果数组的某个元素又是一个Array，则可以形成多维数组，例如：`var arr = [[1, 2, 3], [400, 500, 600], '-'];`

## 对象2

JavaScript规定，访问不存在的属性不报错，而是返回undefined
如果我们要检测对象是否拥有某一属性，可以用in操作符，不过要小心，如果in判断一个属性存在，这个属性不一定是对象的，它可能是对象继承得到的，因为toString定义在object对象中，而所有对象最终都会在原型链上指向object，所以xiaoming也拥有toString属性。
要判断一个属性是否是xiaoming自身拥有的，而不是继承得到的，可以用hasOwnProperty()方法。
