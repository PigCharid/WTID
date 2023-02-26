# 01_语法与基本变量

## 一、认识JavaScript

### 1.1 ECMAScript（ES）

之前在学习的时候经常会看到JS、ES、TS，导致理解有些混乱，ES是标准，JS和TS分别是不同的实现，为什么又会出现TS，等后面学习的时候搞明白。

1997 年，欧洲计算机制造商协会（ECMA）颁布了 JavaScript 的标准，命名为 ECMAScript。

> ECMAScript 简称 ES，JavaScript 简称 JS。

- JavaScript 实现了 ECMAScript

- ECMAScript 规范了 JavaScript



### 1.2  JavaScript 体系

目前要先学习的就是ES5，然后再学习ES6，学习ES6主要是搞明白它在ES5的基础上的变动。

- 语言核心
  - ES5（现阶段学习目标）
  - ES6（后期学习目标）、ES7、ES8、ES9、……
- DOM（操纵 HTML）
- BOM（操作 浏览器）



## 二、书写的位置

通过 `script` 标签将 JavaScript 代码引入到 HTML 中，有两种方式：

### 2.1 内部方式

### 2.2 外部方式

注意：通过外部引用的话，不要在js标签里面再写js代码，不会被执行

推荐使用外部方式写js代码，这样能够清晰的把逻辑控制和页面区分开。

### 2.3其他说明

js代码是从上往下执行，如果出现了错误，下面的js代码就不会再继续执行，同时，一般页面的js都放在底部，一般是需要等页面加载完以后再加载js代码



## 三、输出和输入

### 3.1 输出

目前js的输出方式一共有三种，弹窗、页面、控制台

* alert

在浏览器（JavaScript 引擎 例如：Chrome V8）解析到 JS 文件中的 alert() 语句时，便会中断 JS 脚本的执行，同时弹出警告框，直到用户单击确定后，才继续执行后续的 JS 脚本

* document.write

在页面上直接输出，一般用的不多

* console.log

在控制台进行输出，调试的时候经常用



### 3.2 输入

输入在开发的时候几乎用不上，就是给给输入框，如果需要用户输入的话，表单类元素用的比较多

* prompt



## 四、常量

概念：使用 const 声明的变量称为“常量”。

使用场景：当某个变量永远不会改变的时候，就可以使用 const 来声明，而不是let。

命名规范：和变量一致

~~~javascript
const PI = 3.14
~~~

>注意： 常量不允许重新赋值,声明的时候必须赋值（初始化）



## 五、变量

### 5.1 变量的定义

目前定义变量的方式有三种：var、let和const

* var

定义的变量可以全局使用，目前已经不建议使用这种方式定义变量

* let

根据变量定义的位置判断变量的作用域，变量的定义可以使用这个

* const

consth是用来定义常量的，不变的量都可以用const定义，需要在定义的时候赋予初值。

但是const定义的数组和对象可以修改数组或者变量的属性



### 5.2 严格模式

> **使用 strict 严格模式**
>
> JavaScript 在设计之初，为了方便初学者学习，并不强制要求用 `var` 申明变量。这个设计错误带来了严重的后果：如果一个变量没有通过 `var` 申明就被使用，那么该变量就自动被申明为全局变量：
>
> ```javascript
> i = 10; // i 现在是全局变量
> ```
>
> 在同一个 HTML 页面的不同的 JavaScript 文件中，如果都不用 `var` 申明，恰好都使用了变量 `i`，将造成变量 `i` 互相影响，产生难以调试的错误结果。
>
> 使用 `var` 申明的变量则不是全局变量，它的范围被限制在该变量被申明的 JS 文件或函数体内（函数的概念将稍后讲解），同名变量在不同的函数体内互不冲突。
>
> 为了修补 JavaScript 这一严重设计缺陷，ECMA 在后续规范中推出了 strict 模式，在 strict 模式下运行的 JavaScript 代码，强制通过 `var` 申明变量，未使用 `var` 申明变量就使用的，将导致运行错误。
>
> 启用 strict 模式的方法是在 JavaScript 代码的第一行写上：
>
> ```javascript
> "use strict";
> ```
>
> 这是一个字符串，不支持 strict 模式的浏览器会把它当做一个字符串语句执行，支持 strict 模式的浏览器将开启 strict 模式运行 JavaScript。
>
> ```javascript
> "use strict";
> abc = "Hello, world";
> console.log(abc);
> // 如果浏览器支持 strict 模式，
> // 下面的代码将报 ReferenceError 错误：Uncaught ReferenceError: abc is not defined
> ```
>
> 不用 `var` 申明的变量会被视为全局变量，为了避免这一缺陷，所有的 JavaScript 代码都推荐使用 strict 模式。
>
> 提示：`"use strict"`语句可以放在 JS 代码的任意一行上，并且它只对它所在作用域下方的代码起作用。



### 5.3 同时申明多个变量

js支持同时什么多个变量

```javascript
let a = 0, b = 1, c = 2;	// 建议每行只声明一个变量
```



### 5.4 推荐的变量命名风格

- 小驼峰命名法：`mathTestScore` （吐血推荐）
- C 风格变量命名法：`math_test_score`

> 补充：
>
> - 驼峰命名法：Java、JavaScript
> - 下划线命名法：C、C++、Python、Golang、SQL



# 02_数据类型

## 一、数据类型简介和检测

### 1.1 JavaScript 中两大数据类型

**（1）基本数据类型**

> JS 没有字符型，JS 的 String 是基本类型！

- Number
- String
- Boolean
- Undefined
- Null

**（2）复杂数据类型**

- Object
- Array
- Function
- RegExp（正则表达式）
- Date
- Map
- Set
- Symbol
- ……

### 1.2 typeof 运算符

使用 `typeof` 运算符可以检测值或者变量的类型。

> typeof 是一个运算符，而不是内置函数，所以不用加 `()`，如果加了也不会报错，但是并不推荐。

> 从以上测试也可以看出，JS 是一个弱类型的语言，变量值是什么类型，那么变量就是什么类型，而不用显式地指出类型。



## 二、数字类型

### 2.1 一切数都是数字类型

在 JS 中，所有数字不分大小、不分整浮、不分正负，都是数字类型。

```javascript
typeof 925; // number
typeof 0.5; // number
typeof -24; // number
```

### 2.2 特性

（1）小数点前面小数点可以省略

（2）科学计数法

（3）不同进制的数字

* 二进制数值以 `0b` 开头

```javascript
0b10;	// 2
0b1111;	// 15
```

* 八进制数值以 `0` 开头

```javascript
017;	// 15
```

* 十六进制数值以 `0x` 开头

```javascript
0xf;	// 15
```

（4）一个特殊的数字型值 NaN

`NaN` 是 “not a number” 的意思，即 “不是一个数”，但它是一个数字类型的值。

```javascript
typeof NaN;	// number
```

- 0 除以 0 的结果是 NaN，事实上，在数学运算中，若结果不能得到数字，其结果往往都是 NaN
- NaN 有一个 “奇怪” 的性质：不自等（这个知识点将在后续课程中讲解）

```javascript
0 / 0;	// NaN
5 - 3;	// 2
"我" - "你";	// NaN
"我" * "你";	// NaN
"我" / "你";	// NaN
"我" + "你";	// "我你"
NaN == NaN;   // false
```

> 再次强调：NaN 是一个值（特殊的值），不是类型。
>
> 唯一能判断 `NaN` 的方法是通过 `isNaN()` 函数：
>
> ```javascript
> isNaN(NaN); // true
> ```



## 三、String字符串类型

### 3.1 字符串的表示

通过单引号（ `''`） 、双引号（ `""`）或反引号包裹的数据都叫字符串，单引号和双引号没有本质上的区别，推荐使用单引号。

注意事项：

1. 无论单引号或是双引号必须成对使用
2. 单引号/双引号可以互相嵌套，但是不以自已嵌套自已
3. 必要时可以使用转义符 `\`，输出单引号或双引号

### 3.2 字符串操作

（1）字符串的拼接

直接用加好就可以进行字符串的拼接

（2）空字符串

空字符串和其他类型相加

（3）字符串的 length 属性

> 通过对 String 类型 “打点” 的方式，可以调用其内置属性。
>
> > 注意：在 JS 中，String 是基本类型，之所以 String 可以 “打点” 调用属性和方法，那是因为 JS 的解释器会自动将基本类型包装成对应的对象类型。

字符串的 length 属性表示字符串的长度。

```javascript
"我喜欢JS".length;	// 5
"我喜欢JS，我也喜欢NODE".length;	// 14
"".length;	// 0
```

（4）字符串的常用方法

> 通过对 String 类型 “打点” 的方式，可以调用其内置方法。

“方法” 就是能够打点调用的函数，字符串类型有丰富的内置方法。

| 方法            | 功能             |
| --------------- | ---------------- |
| `charAt()`      | 得到指定位置字符 |
| `substring()`   | 提取子串         |
| `substr()`      | 提取子串         |
| `slice()`       | 提取子串         |
| `toUpperCase()` | 将字符串变为大写 |
| `toLowerCase()` | 将字符串变为小写 |
| `indexOf()`     | 检索字符串       |
| `trim()`        | 删除首尾空格     |
| `trimStart()`   | 删除首部空格     |
| `trimEnd()`     | 删除尾部空格     |

* `charAt()`

> 超出范围的输出空字符 `""`。

* `substring()`、`substr()` 和 `slice()` 

  * substring()

  `substring(a, b)` 方法得到从 a 开始到 b 结束（不包括 b 处）的子串** `[a, b)`

  > 编程语言的区间一般都是：左闭右开

  ```javascript
  "我喜欢JS，我也喜欢NODE".substring(3, 5);		// "JS"
  "我喜欢JS，我也喜欢NODE".substring(10, 14);		// "NODE"
  "我喜欢JS，我也喜欢NODE".substring(10, 99);		// "NODE"
  "我喜欢JS，我也喜欢NODE".substring(-1, 4);		// "我喜欢J"
  ```

  > 超出范围的部分，取到端点字符。

  substring(a, b) 方法如果省略第二个参数，返回的子串会一直到字符串的结尾

  ```javascript
  "我喜欢JS，我也喜欢NODE".substring(6);		// "我也喜欢NODE"
  ```

  substring(a, b) 中，a 可以大于 b，数字顺序将自动调整为小数在前

  > 应该没有人会这样用

  ```javascript
  "我喜欢JS，我也喜欢NODE".substring(3, 5);		// "JS"
  "我喜欢JS，我也喜欢NODE".substring(5, 3);		// "JS"
  ```

  

  * substr()

  将得到从 a 开始的长度为 b 的子串

  ```javascript
  "我喜欢JS，我也喜欢NODE".substr(3, 2);		// "JS"
  ```

  substr(a, b) 中，b 可以省略，表示到字符串结尾

  ```javascript
  "我喜欢JS，我也喜欢NODE".substr(3);		// "JS，我也喜欢NODE"
  ```

  substr(a, b) 中，a 可以是负数，表示倒数位置

  > 倒数第一位为 -1，而不是 -0

  ```javascript
  "我喜欢JS，我也喜欢NODE".substr(-4, 2);		// "NO"
  ```

   

  * `slice(a, b)`

  > slice：切片，主要用来切取字符串，所以切片结束位置要比起始位置大，要不返回空串

  slice(a, b) 的参数 a 可以是负数（与 substring(a, b) 的区别）

  ```javascript
  "我喜欢JS，我也喜欢NODE".slice(-4, -1);		// "NOD"
  // (-4, -1)：从 倒数第4位 到 倒数第1位，不包括 倒数第1位
  ```

  slice(a, b) 中，参数 a 必须小于参数 b，否则便会返回一个空字符串

  ```javascript
  "我喜欢JS，我也喜欢NODE".slice(5, 2);		// ""
  ```




* 大小写转化
  - `toUpperCase()` 转为大写
  - `toLowerCase()` 转为小写



* 位置检索

`indexOf()` 方法返回某个指定的字符串值在字符串中首次出现的位置，区分大小写

如果要检索的字符串没有出现，则返回 `-1`



* `trim()`、`trimStart()`、`trimEnd() `方法

  * trim()
  删除首尾空格

  * trimStart()
	  删除首部空格
	
	* trimEnd()
	
	  删除尾部空格

## 四、Boolean类型

在计算机领域，几乎所有的 “真” 和 “假” 都归为布尔类型值。

布尔类型值只有两个：`true` 和 `false`，分别表示 `真` 和 `假`。

```javascript
typeof true;	// boolean
typeof false;	// boolean
```

> 布尔类型在 关系运算 和 逻辑运算 中广泛运用。

```javascript
3 < 5;	 // true
5 > 3; 	 // true
5 >= 100; // false
```

> 注意：在 JS 中，1 可以 “代表” true，0或-0 可以 “代表” false，原理是类型的自动转换，但非常不建议以数字来代替布尔值！



## 五、Undefined 类型

一个没有赋值的变量的默认值是 `undefined`，而 undefined 的类型也是 undefined。

即：undefined 既是类型，又是值（且这种类型只有它自身一个值）。

```javascript
typeof undefined;	// undefined
```

> 实际开发中，一般不会给某个变量赋值为 undefined，但是我们会检查一个变量的值是否为 undefined。

> 在变量声明提升的时候，会出现 undefined，要注意！



## 六、Null 类型

`null` 表示 “空”，可以理解为它是 “空对象”。

当我们需要将对象销毁、数组销毁或者删除事件监听时，通常将它们设置为 null。

```javascript
box.onclick = null;
// 删除点击事件
```

用 typeof 检测 null 结果为 `object`。

```javascript
typeof null;	// object
```

> 狭义上，null 可以理解为 “空对象”，这样可以合理的解释为什么 null 的类型为 object。
>
> 但是准确的来说，null 不是一个 “对象”，它是一个独立的 “基本数据类型”。



## 七、数据类型转化

### 7.1隐式转化

某些运算符被执行时，系统内部自动将数据类型进行转换，这种转换称为隐式转换





### 7.2显示转化

（1）转化成number

* `Number()` 函数是 JS 内置函数。

> 由于 Number() 属于内置构造函数，所以 Number() 的首字母 N 要大写	

* 字符串——>数字	

* 布尔值——>数字
* undefined和null——>数字



* `parseInt()` 函数的功能是将 `字符串` 或 `浮点数` 转为 `整数`

  * 自动截掉第一个非数字字符之后的所有字符

  ```javascript
  parseInt('3.14');		  // 3
  parseInt('-3.14');		  // -3
  parseInt('3周吉瑞.14');	// 3
  parseInt(3.14);		  	  // 3
  parseInt(-3.14);		  // -3
  ```

  - 所有文字都将被截掉
  - 如果字符串以非数字开头，则转为 NaN
  - 不存在 “四舍五入”
  - true、false、undefined、null 转为 NaN

  > 之所以会出现这种情况的原因是，parseInt() 的原理是，先将参数转换为字符串，再将字符串转为整数。
  >
  > 所以，true 等会先被转为 `'true'`。

  ```javascript
  parseInt(true);			// NaN
  parseInt(false);		// NaN	
  parseInt(undefined);	// NaN
  parseInt(null);			// NaN
  ```

  > parseInt() 函数的特性会用于处理数字的净化。
  >
  > ```javascript
  > parseInt('24px');	// 24
  > // 去除了单位，保留数值！
  > ```




* parseFloat() 

`parseFloat()` 函数的功能是将字符串转为浮点数。

> 绝大部分原理与 parseInt() 类似



（2）转化成string

* String() 函数

`String()` 函数是 JS 内置函数。

> 由于 String() 属于内置构造函数，所以 String() 的首字母 S 要大写

数字——>字符串

变为 “长得相同” 的字符串。

科学计数法和非 10 进制数字会转为 10 进制的标准值。

```javascript
String(123);		// '123'
String(123.4);		// '123.4'
String(2e3);		// '2000'
Stiing(NaN);		// 'NaN'
String(Infinity);	// 'Infinity'
String(0xf);		// '15'
```

布尔值——>字符串

变为 “长得相同” 的字符串。

```javascript
String(true);		// 'true'
String(false);		// 'false'
```

undefined 和 null——>字符串

变为 “长得相同” 的字符串。

```javascript
String(undefined);	// 'undefined'
String(null);		// 'null'
```



* toString() 方法

`toString()` 是几乎所有值都有的方法，功能是将值转为字符串。

> 纯数字不能直接 “打点” 调用 toString() 方法，要把纯数字用 `()` 包裹起来，此时 JS 会提升该数字为一个对象（包装为对象）。



（3）其他值——>布尔值

`Boolean()` 函数是 JS 内置函数。

> 由于 Boolean() 属于内置构造函数，所以 Boolean() 的首字母 B 要大写。

* 数字——>布尔值

0 和 NaN 转为 `false`，其他数字都转为 `true`，字符串有长度就true

```javascript
Boolean(123);			// true
Boolean(0);				// false
Boolean(NaN);			// false
Boolean(Infinity);		// true
Boolean(-Infinity);		// true
```

> Infinity 属性用于存放表示正无穷大的数值。

* 字符串——>布尔值

空字符串变为 `false`，其他都转为 `true`。

```javascript
Boolean('');				// false
Boolean('abc');				// true
Boolean('false');			// true
```

* undefined和null——>布尔值

转为 false。

```javascript
Boolean(undefined);				// false
Boolean(null);					// false
```



## 八、复杂数据类型简介

除基本类型值外，JS 的世界中还有复杂数据类型。

举例：

```javascript
[1, 2, 3]

{ a: 1, b: 2 }

function() {
}
```

> 在 JS 中普通类型也可以包装为复杂类型（对象）
>
> ```javascript
> str01 = "zjr";
> str02 = new String("zjr");
> str03 = String("zjr");
> console.log(typeof str01);		// string
> console.log(typeof str02);		// object
> console.log(typeof str03);		// string
> console.log(str01 === str02);	// false
> console.log(str02 === str03);	// false
> console.log(str01 === str03);	// true
> // Number、Boolean 同理
> ```

复杂数据类型都是 “引用类型”（type: object），将在后续课程中介绍

## 九、基本类型值和引用类型值

|            | 当 var a = b 变量传值时                          | 当用 == 或 === 比较时                                        |
| ---------- | ------------------------------------------------ | ------------------------------------------------------------ |
| 基本类型值 | 内存中产生新的副本                               | 比较值是否相等（由于是赋值所以类型肯定相同，=== 无需考虑类型是否相等） |
| 引用类型值 | 内存中不产生新的副本，而是让新变量指向同一个对象 | 比较内存地址是否相等，即：比较是否是同一个对象（由于是赋值所以类型肯定相同，=== 无需考虑类型是否相等） |

```javascript
// 基本类型值
var a = 3;
var b = a;
a++;
console.log(a);		// 4
consloe.log(b);		// 3
```

```javascript
// 引用类型值
var arr1 = [1, 2, 3, 4];
var arr2 = arr1;
arr1.push(5);
console.log(arr1);	// [1, 2, 3, 4, 5]
console.log(arr2);	// [1, 2, 3, 4, 5]
```

- 基本类型：`number`、`boolean`、`string`、`undefined`、`null`
- 引用类型：`array`、`object`、`function`、`regexp`、……

【内存】

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/05【JS数组】/mark-img/78d2f78a614042ef998a91c992154d7e.png" style="zoom:50%;" />

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/05【JS数组】/mark-img/9dfcfceed30440c290efc2ec3226919b.png" style="zoom:50%;" />

【相等 `==` 判断时的区别】

- 基本类型进行相等 `==` 判断时，会比较 “值” 是否相等
- 引用类型进行相等 `==` 判断时，会比较 “址” 是否相等，也就是说它会比较是否为内存中的同一个东西

```javascript
3 == 3;		// true
3 === 3;		// true
[1, 2, 3] == [1, 2, 3];	// false
[1, 2, 3] === [1, 2, 3];	// false
[] == [];	// false
[] === [];	// false

var arr = [1, 2, 3];
arr == arr;		// true
var arr2 = arr;
arr == arr2;	// true，这里比较的是 arr 与 arr2 中保存的地址是否相等
arr === arr2;	// true，由于类型相同，所以这里比较的也是 arr 与 arr2 中保存的地址是否相等
```





# 03_表达式和操作符

## 一、算术表达式

### 1.1 算术运算符

| 意义 | 运算符 |
| ---- | ------ |
| 加   | `+`    |
| 减   | `-`    |
| 乘   | `*`    |
| 除   | `/`    |
| 取余 | `%`    |

> 推荐一律使用 `()` 来强制规定优先级！

`+` 有 “加法” 和 “连字符” 两种作用，如果 `+` 的某一边是字符串那么就为 ”连字符“，否则为 ”加法“。 

### 1.2 精度丢失问题

在 JS 中，有些小数的数学运算不是很精准。

```javascript
0.1 + 0.2;	// 0.30000000000000004
```

JS 使用了 IEEE754 二进制浮点数算术标准，这会使一些个别的小数运算产生 “丢失精度” 问题。

注意：不是所有的小数运算都会出现精度问题，只是少数部分。

> 几乎所有的高级语言都使用了 IEEE754 二进制浮点数算术标准。
>
> IEEE754 二进制浮点数算术标准是计算机底层编译标准，了解即可！

【解决办法】

在进行小数运算时，要调用数字的 `toFixed()` 方法保留指定的小数位数。

> `toFixed()` 括号内接受一个保留小数位数的参数。 

```javascript
(0.1 + 0.2).toFixed(2);				// '0.30'，默认得到一个字符串值
Number((0.1 + 0.2).toFixed(2));		 // 0.3
```

>  `toFixed()` 遵循 “四舍五入” 原则。
>
>  ```javascript
>  (0.9945).toFixed(3);	// "0.995"
>  ```

>最后要注意浮点数的相等比较：
>
>```javascript
>1 / 3 === (1 - 2 / 3); // false
>```
>
>这不是 JavaScript 的设计缺陷。浮点数在运算过程中会产生误差，因为计算机无法精确表示无限循环小数。要比较两个浮点数是否相等，只能计算它们之差的绝对值，看是否小于某个阈值：
>
>```javascript
>Math.abs(1 / 3 - (1 - 2 / 3)) < 0.0000001; // true
>```

> 还有一种解决技巧，就是将浮点数转换为整数进行计算：
>
> ```javascript
> 0.1 + 0.2;	// 0.30000000000000004
> (0.1 * 10 + 0.2 * 10) / 10;	// 0.3
> ```

### 1.3 幂和开根号

JS 中没有提供幂运算、开根号的运算符，需要使用 Math 对象的相关方法进行计算。

`Math.pow(a, b)`：求 a 的 b 次方。

`Math.sqrt(a)`：求 a 的平方根。

```javascript
Math.pow(2, 3);		// 8
Math.pow(3, 2);		// 9
Math.sqrt(81);		// 9
Math.sqrt(-81);		// NaN
```

### 1.4 向上取整和向下取整

`Math.ceil()`：向上取整。

`Math.floor()`：向下取整。

`Math.round()`：把一个数字舍入为最接近的整数（“四舍六入”，“五不一定”）

> 注意：向上、向下的标准是：X轴正方向为上！
>
> 负 ———— 0 ————> 正

```javascript
Math.ceil(2.4);			// 3
Math.floor(2.4);		// 2

Math.ceil(-2.4);		// -2
Math.floor(-2.4);		// -3

Math.ceil(2);			// 2
Math.floor(2);			// 2		
```



## 二、关系表达式

### 2.1 关系运算符

| 意义       | 运算符 |
| ---------- | ------ |
| 大于       | `>`    |
| 小于       | `<`    |
| 大于或等于 | `>=`   |
| 小于或等于 | `<=`   |
| 等于       | `==`   |
| 不等于     | `!=`   |
| 全等于     | `===`  |
| 不全等于   | `!==`  |

### 2.2 相等和全等

两个等号 `==` 运算符，不考虑值的类型，它会进行**隐式转换**后比较**值的字面量**是否相等。

三个等号 `===` 运算符，不仅比较**值**是否相同，也比较**类型**是否相同。

```javascript
5 == '5';		// true
5 === '5';		// false
```

```javascript
1 == true;			// true
1 === true;			// false

0 == false;			// true
0 === false; 		// false

0 == undefined;		// false
0 === undefined;	// false

undefined == null;	// true
undefined === null;	// false
```

> null 和 undefined 用 == 进行比较涉及隐式强制类型转换，ES5 规范中规定。
>
> === 比较为 false，是因为 null 与 undefined 类型不同。
>
> 建议没有特殊情况请一律使用 ===

### 2.3 NaN不自等

NaN 作为一个特殊的数字类型值，它在用 `==` 比较的时候也有特殊的结果。

```javascript
NaN == NaN;			// false
NaN	=== NaN;		// false
```

【如何判断某变量值为 NaN】

`isNaN()` 函数可以用来判断变量值是否为 NaN。

```javascript
isNaN(NaN);		// true
isNaN(5);		// false
isNaN("5");		// false
```

> 但 isNaN() 也不好用，它的机理是：只要该变量传入 Number() 的执行结果是 NaN，则 isNaN() 函数都会得到 true。
>
> 对于，undefined 和 null，这种情况一般来说需要先进行单独判断，再进行 isNaN 判断。
>
> ```javascript
> isNaN(undefined);	// true
> isNaN('3天');	   // true
> isNaN(null);		// false
> ```



### 2.4 JS中没有连比

例如：`3 <= a <= 15` 的写法是错误的，应该为：`a >= 3 && a <= 15`。



## 三、逻辑表达式

### 3.1 逻辑运算符

| 意义 | 运算符 |
| ---- | ------ |
| 非   | `!`    |
| 与   | `&&`   |
| 或   | `||`   |

### 3.2 非运算

`!` 表示 “非”，也可以称为 “置反运算”。

`!` 是一个 “单目运算符”，只需要一个操作数。

置反运算的结果一定是布尔值。

```javascript
!true;			// false
!false;			// true
!0;				// true
!undefined;		// true
!'';			// true
!' ';			// false
!null;			// true
!'imooc';		// false
```

> `!!` 常用于确定一个值的布尔属性。
>
> ```javascript
> !!true;		// true
> !!0;		// false
> !!'';		// false
> !!' ';		// true
> !!'imooc';	// true
> ```

### 3.3 与或运算

`&&` 是 “双目运算符”。

核心：`全真为真、有假即假`。

`||` 是 “双目运算符”。

核心：`全假为假、有真即真`。

### 3.4 短路运算

`&&` 与 `||`，都属于 “短路运算符”。

**（1）`&&` 短路运算**

由于 `&&` 运算的核心是：“全真为真、有假即假”，所以：

- 如果 `a && b` 中 `a` 为真，那么该表达式的值由 `b` 决定（计算 a 又计算 b）
- 如果 `a && b` 中 `a` 为假，那么该表达式的值由 `a` 决定（只计算 a）

```javascript
3 && 6;				// 6
undefined && 15;	// undefined
15 && undefined;	// undefined
null && 2;			// null
'' && 16;			// ''
NaN && undefined;	// NaN
```

**（2）`||` 短路运算**

由于 `||` 运算的核心是：“全假为假、有真即真”，所以：

- 如果 `a || b` 中 `a` 为真，那么该表达式的值由 `a` 决定（只计算 a）
- 如果 `a || b` 中 `a` 为假，那么该表达式的值由 `b` 决定（计算 a 又计算 b）

```javascript
3 || 6;				// 3
0 || 6;				// 6
null || undefined;	// undefined
'a' || 'b';			// 'a'
NaN || null;		// null
```



### 3.5 逻辑运算的优先级

优先级：`!` > `&&` > `||`

```javascript
!true || true;		// true
3 && 4 || 5 && 6；  // 4
```

> 推荐使用 `()` 来规定优先级。

## 四、赋值表达式

### 4.1 赋值运算符

| 意义     | 运算符                       |
| -------- | ---------------------------- |
| 赋值     | `=`                          |
| 快捷赋值 | `+=`、`-=`、`*=`、`/=`、`%=` |
| 自增运算 | `++`                         |
| 自减运算 | `--`                         |

### 4.2 赋值运算产生值

赋值运算也产生值，等号后面的值将作为 “赋值运算的值”。

```javascript
var a;
console.log(a = 4);		// 4
```

这就意味着，可以连续使用赋值运算符。

```javascript
var a, b, c;
a = b = c = 15;
console.log(a);		// 15
console.log(b);		// 15
console.log(c); 	// 15
```

> 在实际开发中不建议使用连续赋值！

### 4.3 自增自减运算

`a++`：先用再加；`++a`：先加再用。

`a--`：先用再减；`--a`：先减再用。



## 五、模板字符串

> 模版字符串是只在字符串中可以使用变量，动态的获取值
>
> 用法就是${变量名}

也支持拼接字符串



## 六、三元运算符

> 语法：条件表达式 ? 表达式1 : 表达式2

可以进行嵌套，条件表达式 ? 表达式1 : (条件表达式 ? 表达式2 : 表达式3)





# 04_JS流程控制

## 一、if-else条件语句



## 二、switch 选择语句

- 与其他高级语言不同，在 JS 中 case 后不仅仅只能跟常量值，还可以跟变量和表达式
- 注意 switch 语句的 “开关” 特性（遇见 break 才跳出 switch，否则直接进入下一个 case），合理运用好 break（例如不加 break 可以实现多条 case 共用同一个语句体）
- default 语句不是必须的



## 三、for 循环语句

在 JS 中，支持在 “初次表达式” 中声明变量并赋值。

【for ... in 循环】

`for` 循环的一个变体是 `for ... in` 循环，它可以把一个对象的所有属性依次循环出来：

```javascript
var o = {
    name: "Jerry",
    age: 20,
    city: "Beijing"
};

for (var key in o) {
    console.log(key + ": " + o[key]);
}
/*
"name: Jerry"
"age: 20"
"city: Beijing"
*/
```

要过滤掉对象继承的属性，用 `hasOwnProperty()` 来实现：

```javascript
var o = {
    name: "Jerry",
    age: 20,
    city: "Beijing"
};

for (var key in o) {
    if (o.hasOwnProperty(key)) {
        console.log(key + ": " + o[key]);
    }
}
/*
"name: Jerry"
"age: 20"
"city: Beijing"
*/
```

由于数组也是对象，而它的每个元素的索引被视为对象的属性，因此，`for ... in` 循环可以直接循环出数组的索引：

```javascript
var a = ['A', 'B', 'C'];

for (var i in a) {
    console.log(i + ": " + a[i]);
}
/*
0: A
1: B
2: C
*/
```

请注意，`for ... in` 对数组的循环得到的索引是 `String` 而不是 `Number`。

## 四、while 循环语句

```javascript
while (判断条件) {
    
}
```

```javascript
do {
    
} while (判断条件);
```

在 while 中，先判断条件，条件满足时再执行语句体。

在 do-while 中，do 内的语句块先执行一次，再判断条件。

## 五、break 和 continue

`break;`：立即终止本层次循环。

`continue;`：立即跳过本层次循环，提前进入本层次的下一次循环。

## 六、label 表达式

`label` 是一个标签，可以使用 `break` 或 `continue` 使程序跳转到这个标签处执行（执行：`break` 或 `continue`），从而改变程序的执行流程。

```javascript
// 注意：label 不是一个特定的关键字，可以随便取名
label: for (var i = 0; i < 10; i++) {
    for (var j = 0; j < 10; j++) {
        if (i + j === 6) {
            console.log("j=" + j);
            break label;
        }
    }
    console.log("i=" + i);
}
/*
j=6
*/
```

```javascript
label: for (var i = 0; i < 10; i++) {
    for (var j = 0; j < 10; j++) {
        if (i + j === 6) {
            console.log("j=" + j);
            continue label;
        }
    }
    console.log("i=" + i);
}
/*
j=6
j=5
j=4
j=3
j=2
j=1
j=0
i=7
i=8
i=9
*/
```

```javascript
// label + break 配合可以用在循环外
label: {
    if (1 > 0) {
        console.log("1");
        break label;
    }
    console.log("2");
}
/*
1
*/
```



# 05_数组

## 一、数组的定义和使用

### 1.1 数组的定义

（1）方括号定义法

（2）new 定义法

> 推荐：方括号定义法！
>
> - 如果是定义时就要指定数组的值，那么建议使用：`var arr = ['A', 'B', 'C', 'D'];`
> - 如果是定义时还不指定数组的值，那么建议使用：`var arr = [];`



### 1.2 访问数组项

（1）方式

（2）下标越界

（3）数组长度

（4）修改数组

更改的数组项超过了 `length-1`，则会创造该项。

> JS 数组是可以动态扩容的！

（5）数组的遍历

for in

（6）数组的检测

`Array.isArray()` 方法可以用来检测数组，返回一个布尔值。

> isArray() 不兼容 IE678，所以后面课程中，还将介绍使用 “鸭式辨型” 检测方法。

```javascript
Array.isArray([1, 2, 3]);		// true
Array.isArray([]);				// true
```



## 二、数组常用的方法

### 2.1 push() 方法

### 2.2 pop() 方法

### 2.3 unshift()() 方法

### 2.4 shift()() 方法

### 2.5 splice() 方法

### 2.6 slice() 方法

### 2.7 join() 和 split()方法

### 2.8 字符串和数组更多相关性

字符串也可以使用 `[下标]` 的形式访问某个字符，等价于 `charAt()` 方法。

> 在对字符串中的字符进行遍历时不用转为数组，直接利用 [下标] 即可。
>
> 字符串的一些算法问题，会转为数组解决！

```javascript
'我爱前端'[0];			// "我"
'我爱前端'[1];			// "爱"
'我爱前端'.charAt(0);	// "我"
```

```javascript
var str = '我爱前端';
for (var i = 0; i < str.length; i++) {
    console.log(str[i]);
}
```

### 2.9 concat() 方法

`concat()` 方法可以合并连接多个数组（以返回值的形式）。

`concat()` 方法不会改变原数组。

### 2.10 reverse() 方法

`reverse()` 方法用来将一个数组中的全部项顺序置反。



### 2.11 indexOf() 和 includes()  方法

`indexOf()` 方法的功能是搜索数组中的元素，并返回它所在的位置，如果元素不存在，则返回 -1。

`includes()` 方法的功能是判断一个数组是否包含一个指定的值，返回一个布尔值。



### 2.12 sort() 方法

数组有 `sort()` 方法可以用于数组的排序，但是涉及到函数的相关知识，在函数一节课进行介绍。



### 2.13 数组去重和随机样本

【数组去重】

题目：去掉数组中的重复项。

思路：准备一个空结果数组，遍历原数组，如果遍历到的项不在结果数组中，则推入结果数组。

```javascript
var arr = [1, 1, 1, 2, 2, 3, 3, 3, 2, 1];
var resultArr = [];
for (var i = 0; i < arr.length; i++) {
    if (!resultArr.includes(arr[i])) {
        resultArr.push(arr[i]);
    }
}
console.log(resultArr);
```

【随机样本】

题目：请随机从原数组中取 3 项。

思路：准备一个空结果数组，遍历原数组，随机选择一项，推入结果数组，并且将这项在原数组中删除。

```javascript
var arr = [3, 6, 10, 5, 8, 9];
var resultArr = [];
for (var i = 0; i < 3; i++) {
    var n = parseInt(Math.random() * arr.length);
    resultArr.push(arr[n]);
    arr.splice(n, 1);
}
console.log(resultArr);
```

### 2.14 有关数组在 ES6 中的增强

数组在 ES6 中新增了较多的新方法，将在 ES6 相关课程中介绍。



# 06_函数

## 一、函数的定义和使用

### 1.1定义

（1）函数声明

```javascript
function fun() {
    // 函数语句块
}
```

（2）函数表达式

```javascript
var fun = function() {
    // 函数语句块
};
```

### 1.2定义



## 二、函数的参数和返回值

- 圆括号中定义 “形式参数”
- 调用函数时传入 “实际参数”

> “形式参数” 和 “实际参数” 是彼此独立的，除了传递值之外，互不干扰！

> 注意：JS 只有 “值传递” 没有 “引用传递”，对于复杂类型的传递，传递的不是引用，而是那个变量里面的值（引用的地址）。
>
> 引用传递：修改形参，实参也会改变。JS 中复杂类型的实参是个地址值不需要改变，也改变不了，改变的是地址所指向的堆中的复杂类型的具体值，此处具有迷惑性，要加以辨别。



## 三、JS内置 sort() 方法的优化

## 四、闭包

 ### 4.1 什么是闭包

函数的返回值是一个对象的话，那就是一个闭包，闭包有很多在编程中可以用的点

不要滥用闭包，容易造成内存泄漏

## 五、匿名函数

### 5.1 用于闭包

### 5.2用于立即执行函数









# 07_对象

## 一、认识对象

### 1.1 对象的语法

k 和 v 之间用冒号分隔，每组 `k:v` 之间用逗号分隔，最后一个 `k:v` 对后可以不书写逗号。

```javascript
var obj = {
    k: v,
    K: v,
    K: v,
    K: v
};
```

### 1.2 属性是否加引号

如果对象的属性键名不符合 JS 标识符命名规范，则这个键名必须用引号包裹。

> 注意：对象中的 key 本身就是字符串格式，只是符合 JS 标识符命名规范的可以省略引号！

```javascript
var xiaoming = { 
    name: '小明',
    age: 12,
    sex: '男',
    hobbys: ['足球', '游泳', '编程'],
    'favorite-book': '舒克和贝塔'
    // 属性名中有短横，不符合JS标识符命名规范，属性名必须用引号包裹。
};
```

> 建议不要使用不规范的命名方式

### 1.3 属性的访问

可以用“点语法”访问对象中指定键的值。

```javascript
xiaoming.name;		// '小明'
xiaoming.age;		// 12
xiaoming.hobbys;	// ['足球', '游泳', '编程'] 
```

如果属性名不符合 JS 标识符命名规范，则必须用方括号的写法来访问。

> 方括号 `[]` 中只能是字符串类型！
>
> 任何对象的属性名都可以通过 `[]` 来访问，只要把属性名写为字符串的形式。

```javascript
xiaoming['favorite-book'];	// '舒克和贝塔'
```

如果属性名以变量形式存储，则必须使用方括号形式。

```javascript
var obj = {
    a: 1,
    b: 2,
    c: 3
};

var key = 'b';
console.log(obj.key);	// undefined
console.log(obj[key]);	// 2
```

### 1.4 属性的更改

直接使用赋值运算符重新对某属性赋值即可更改属性。

```javascript
var obj = {
    a: 10
};
obj.a = 30;
obj.a++;
```

### 1.5 属性的创建

如果对象本身没有某个属性值，则用点语法赋值时，这个属性会被创建出来。

```javascript
var obj = {
    a: 10
};
obj.b = 40;
```

```javascript
var obj = {
    a: 10
};
obj['zjr-b'] = 40;
```

### 1.6 属性的删除

如果要删除某个对象的属性，需要使用 delete 操作符。

```javascript
var obj = {
    a: 1,
    'zjr-b': 2
};
delete obj.a;
delete obj['zjr-b'];
```



## 二、对象方法

### 2.1 认识方法

如果某个属性值是函数，则它也被称为对象的 “方法”。

```javascript
var xiaoming = {
    name: '小明',
    age: 12,
    sex: '男',
    hobbys: ['足球', '游泳', '编程'],
    'favorite-book': '舒克和贝塔',
    // sayHello方法
    sayHello: function () {
		console.log('你好我是小明，今年12岁，我是个男生');
	}
};
```

### 2.2 方法的调用

使用 “点语法” 可以调用对象的方法。

```javascript
xiaoming.sayHello();
```

### 2.3 方法和函数

方法也是函数，只不过方法是对象的 “函数属性”，它需要用对象打点调用。

在正式学习了什么是 “方法” 之后，就能深入理解之前我们学习的一些函数的书写形式了，比如：

```javascript
console.log();
Math.ceil();
```

### 2.4 对象的遍历

和遍历数组类似，对象也可以被遍历，遍历对象需要使用 for...in... 循环。

使用 for...in... 循环可以遍历对象的每个键。

在后续的 ES6 相关课程中，还会学习新的对象遍历的方式。

【for...in...循环】

```javascript
// k: 循环变量，它会依次成为对象的每一个键
// obj: 要遍历的对象
for (var k in obj) {
    console.log('属性' + k + '的值是' + obj[k]);
}
```

【案例】

```javascript
var obj = {
    a: 11,
    b: 22,
    c: 88
};
for (var k in obj) {
    console.log('对象obj的属性' + k + '的值是' + obj[k]);
}

/*
对象obj的属性a的值是11
对象obj的属性b的值是22
对象obj的属性c的值是88
*/
```

```javascript
var zjr = {
    name: 'jerry',
    love: [180, 18, 1800000],
    home: {
        mm: 'glp',
        bb: 'zyj'
    }
};

for (var i in zjr) {
    console.log(i);
    console.log(typeof i);
}

/*
name
string
string
love
string
object
home
string
object
*/
```

> for...in... 循环中，每一个迭代值是对应值的字符串形式。

## 三、对象的深浅克隆

### 3.1 复习基本类型值和引用类型值

还记得我们之前学习过的基本类型值和引用类型值吗？

|            | 举例                                | 当 var a = b 变量传值时                          | 当用 == 比较时                             | 当用 === 比较时                            |
| ---------- | ----------------------------------- | ------------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| 基本类型值 | 数字、字符串、布尔、undefined、null | 内存中产生新的副本                               | 比较值是否相等                             | 类型相等的前提下，比较值相等               |
| 引用类型值 | 对象、数组等                        | 内存中不产生新的副本，而是让新变量指向同一个对象 | 比较内存地址是否相同，即比较是否为同一对象 | 比较内存地址是否相同，即比较是否为同一对象 |

> 对于引用类型的比较来说：== 与 === 是没有区别的！

```javascript
var a = {};
var b = {};
var c = a;

console.log(a == b);	// false
console.log(a === b);	// false
console.log(a == c);	// true
console.log(a === c);	// true
```

### 3.2 对象是引用类型值

对象是引用类型值，这意味着：

不能用 `var obj2 = obj1` 这样的语法克隆一个对象。

使用 == 或者 === 进行对象的比较时，比较的是它们是否为内存中的同一个对象，而不是比较值是否相同。

【案例】

```javascript
// 例子1
var obj1 = {
    a: 1,
    b: 2,
    c: 3
};
var obj2 = {
    a: 1,
    b: 2,
    c: 3
};
console.log(obj1 == obj2);      // false
console.log(obj1 === obj2);     // false

console.log({} == {});          // false
console.log({} === {});         // false

// 例子2
var obj3 = {
    a: 10
};
var obj4 = obj3;
obj3.a++;
console.log(obj4);              // {a: 11}
console.log(obj3 == obj4);      // true
console.log(obj3 === obj4);		// true
```

### 3.3 对象的浅克隆

复习什么是浅克隆：只克隆对象的 “表层”，如果对象的某些属性值又是引用类型值，则不进一步克隆它们，只是传递它们的引用。

使用 for...in... 循环即可实现对象的浅克隆。

【案例】

```javascript
var obj1 = {
    a: 1,
    b: 2,
    c: [44, 55, 66]
};

// var obj2 = obj1;  这不是克隆，千万不能这样！！！！

// 实现浅克隆
var obj2 = {};
for (var k in obj1) {
    // 每遍历一个 k 属性，就给 obj2 也添加一个同名的 k 属性
    // 值和 obj1 的 k 属性值相同
    obj2[k] = obj1[k];
}

// 为什么叫浅克隆呢？比如 c 属性的值是引用类型值，那么本质上 obj1 和 obj2 的 c 属性是内存中的同一个数组，并没有被克隆分开。
obj1.c.push(77);
console.log(obj2);                  // obj2 的 c 属性这个数组也会被增加 77 数组
console.log(obj1.c == obj2.c);      // true，true 就证明了数组是同一个对象
```

### 3.4 对象的深克隆

复习什么是深克隆：克隆对象的全貌，不论对象的属性值是否又是引用类型值，都能将它们实现克隆。

和数组的深克隆类似，对象的深克隆需要使用递归。

面试时经常会考察深克隆算法，必须掌握。

【案例】

```javascript
var obj1 = {
    a: 1,
    b: 2,
    c: [33, 44, {
        m: 55,
        n: 66,
        p: [77, 88]
    }]
};

// 深克隆
function deepClone(o) {
    // 要判断 o 是对象还是数组
    if (Array.isArray(o)) {
        // 数组
        var result = [];
        for (var i = 0; i < o.length; i++) {
            result.push(deepClone(o[i]));
        }
    } else if (typeof o == 'object') {
        // 对象
        var result = {};
        for (var k in o) {
            result[k] = deepClone(o[k]);
        }
    } else {
        // 基本类型值
        var result = o;
    }
    return result;
}

var obj2 = deepClone(obj1);
console.log(obj2);

console.log(obj1.c == obj2.c);      // false

obj1.c.push(99);
console.log(obj2);                  // obj2 不变的，因为没有“藕断丝连”的现象

obj1.c[2].p.push(999);
console.log(obj2);                  // obj2 不变的，因为没有“藕断丝连”的现象
```



## 四、认识上下文

### 4.1 什么是上下文

垃圾分类，`这` 是非常好的习惯，值得表扬。

随手关灯，`这` 是非常好的习惯，值得表扬。

课后复习，`这` 是非常好的习惯，值得表扬。

早睡早起，`这` 是非常好的习惯，值得表扬。

### 4.2 函数的上下文

函数中可以使用 this 关键字，它表示函数的上下文。

与中文中 “这” 类似，函数中的 this 具体指代什么必须通过**调用函数时的 “前言后语”** 来判断。

> 注意：准确的来说，应该叫 “方法的上下文”，因为这里主要指的是对象方法里的上下文 this

### 4.3 函数中的 this

```javascript
var xiaoming = {
    nickname: '小明',
    age: 12,
    sayHello: function () {
        console.log('我是' + this.nickname + '，我' + this.age + '岁了');
    }
};
xiaoming.sayHello();

// 我是小明，我12岁了
```

```javascript
var xiaoming = {
    nickname: '小明',
    age: 12,
    sayHello: function () {
        console.log('我是' + this.nickname + '，我' + this.age + '岁了');
    }
};
var sayHello = xiaoming.sayHello;	// 将函数“提”出来，单独存为变量
sayHello();		// 直接圆括号调用这个函数，而不是对象打点调用了

// 我是undefined，我undefined岁了
```

### 4.4 函数的上下文由调用方式决定

**同一个函数，用不同的形式调用它，则函数的上下文不同。**

- 情形1：对象打点调用函数，函数中的 this 指代这个打点的对象

```javascript
xiaoming.sayHello();
```

- 情形2：圆括号直接调用函数，函数中的 this 指代 window 对象

```javascript
var sayHello = xiaoming.sayHello;
sayHello();
```

【案例】

```javascript
var obj = {
    a: 1,
    b: 2,
    fn: function() {
        console.log(this.a + this.b);
        /*
        请问，这里的两个 this 指代什么？
        正确答案：不知道！
        原因：函数只有被调用时，它的上下文才能被确定。
        */
    }
};

obj.fn();	// 3

var fn = obj.fn;	// 提炼的是函数本身，而不是函数执行结果，所以不能加()
fn();			   // NaN（undefined+undefined=NaN）
```

> 宏观上可以把 “谁调用，上下文就是谁” 作为评判方法，如果没有明确的调用者，那么就是 Window。

## 五、上下文规则

### 5.1 函数的上下文由调用函数的方式决定

函数的上下文（this 关键字）由调用函数的方式决定，function 是 “运行时上下文” 策略。

函数如果不调用，则不能确定函数的上下文。

### 5.2 规则1

**规则1：对象打点调用它的方法函数，则函数的上下文是这个打点的对象。**

```javascript
对象.方法()
```

【规则1题目举例 - 第1小题】 

```javascript
function fn() {
    console.log(this.a + this.b);
}

var obj = {
    a: 66,
    b: 33,
    fn: fn
};

obj.fn();	// 99	
// 构成 对象.方法() 的形式，适用规则1
```

【规则1题目举例 - 第2小题】

```javascript
var obj1 = {
    a: 1,
    b: 2,
    fn: function() {
        console.log(this.a + this.b);
    }
};

var obj2 = {
    a: 3,
    b: 4,
    fn: obj1.fn		// obj2中的fn方法指向了obj1中的fn方法，即：fn方法在内存中只有一份但是被两次指向
};

obj2.fn();	// 7
// 构成 对象.方法() 的形式，使用规则1
```

【规则1题目举例 - 第3小题】

```javascript
function outer() {
    var a = 11;
    var b = 22;
    return {
        a: 33, 
        b: 44, 
        fn: function () {
            console.log(this.a + this.b);
        }
    };
}

outer().fn();	// 77
// outer()返回一个对象
// 对象.fu()
// 构成 对象.方法() 的形式，适用规则1
```

【规则1题目举例 - 第4小题】

```javascript
funtion fun() {
    console.log(this.a + this.b);
}
var obj = {
    a: 1,
    b: 2,
    c: [{
        a: 3,
        b: 4,
        c: fun
    }]
};
var a = 5;
obj.c[0].c();	// 7	
// obj.c[0]是 {a:3, b:4, c:fun}
// 所以实际上是 {a:3, b:4, c:fun}.c();
// 构成 对象.方法()的形式，适用规则1
```

### 5.3 规则2

**规则2：圆括号直接调用函数，则函数的上下文是 window 对象。**

> 如果是 strict 严格模式下，圆括号直接调用函数，则函数的上下文是 undefined
>
> （在非严格模式下 undefined 会转换为 window）

```javascript
函数()
```

【规则2题目举例 - 第1小题】

```javascript
var obj1 = {
    a: 1,
    b: 2,
    fn: function() {
        console.log(this.a + this.b);
    }
};

var a = 3;
var b = 4;

var fn = obj1.fn;	// 将函数的引用交给变量存储
fn();	// 7
// 构成函数()的形式，适用规则2
```

【规则2题目举例 - 第2小题】

```javascript
function fun() {
    return this.a + this.b;
}
var a = 1;
var b = 2;
var obj = {
    a: 3,
    b: fun(),	// fun函数的执行结果赋给b，适用规则2，b = 1+2
    fun: fun	// fun函数的引用
};
var resulr = obj.fun();		// 适用规则1
console.log(result);	// 6
```

### 5.4 规则3

**规则3：数组（类数组对象）枚举出函数进行调用，上下文是这个数组（类数组对象）。**

```javascript
数组[下标]()
```

【规则3题目举例 - 第1小题】

```javascript
var arr = ['A', 'B', 'C', function() {
    console.log(this[0]);
}];
arr[3]();	// A
// 适用规则3
```

【类数组对象】

什么是类数组对象：所有键名为自然数序列（从0开始），且有 length 属性的对象。

arguments 对象是最常见的类数组对象，它是函数的实参列表。

【规则3题目举例 - 第2小题】

```javascript
function fun() {
    arguments[3]();	// 适用规则3
}
fun('A', 'B', 'C', function() {
    console.log(this[1]);
});
// B
```

### 5.5 规则4

**规则4：IIFE 中的函数，上下文是 window 对象。**

```javascript
(function() {
 })();
```

【规则4题目 - 举例】

```javascript
var a = 1;
var obj = {
    a: 2,
    fun: (function() {
          var a = this.a;
          return function() {
    	  	  console.log(a + this.a);	// 1 + 2
		  }
     })()	// 适用规则4
};
obj.fun();	// 适用规则1
// 3
```

### 5.6 规则5

**规则5：定时器、延时器调用函数，上下文是 window 对象。**

```javascript
setInterval(函数, 时间);
setTimeout(函数, 时间);
```

【规则5题目举例 - 第1小题】

```javascript
var obj = {
    a: 1,
    b: 2,
    fun: function() {
    	console.log(this.a + this.b);
	}
}
var a = 3;
var b = 4;

setTimeout(obj.fun, 2000);	// 7
// 适用规则5
```

【规则5题目举例 - 第2小题】

```javascript
var obj = {
    a: 1,
    b: 2,
    fun: function() {
        console.log(this.a + this.b);
    }
}
var a = 3;
var b = 4;
setTimeout(function() {
		obj.fun(); // 输出3，适用规则1，原因：此时setTimeout没有直接调用obj.fun()，而是直接调用了匿名函数
}, 2000);
```

### 5.7 规则6

**规则6：事件处理函数的上下文是绑定事件的 DOM 元素。**

```javascript
DOM元素.onclick = function() {
};
```

【规则6 - 小案例1】

请实现效果：点击哪个盒子，哪个盒子就变红，要求使用同一个事件处理函数实现。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            float: left;
            border: 1px solid #000;
            margin-right: 10px;
        }
    </style>
</head>
<body>
<div id="box1"></div>
<div id="box2"></div>
<div id="box3"></div>

<script>
    function setColorToRed() {
        this.style.backgroundColor = 'red';
    }

    var box1 = document.getElementById('box1');
    var box2 = document.getElementById('box2');
    var box3 = document.getElementById('box3');

    box1.onclick = setColorToRed;
    box2.onclick = setColorToRed;
    box3.onclick = setColorToRed;
</script>
</body>
</html>
```

【规则6 - 小案例2】

请实现效果：点击哪个盒子，哪个盒子在 2000 毫秒后就变红，要求使用同一个事件处理函数实现。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            float: left;
            border: 1px solid #000;
            margin-right: 10px;
        }
    </style>
</head>
<body>
<div id="box1"></div>
<div id="box2"></div>
<div id="box3"></div>

<script>
    function setColorToRed() {
        // 备份上下文（因为：定时器、延时器调用函数，上下文是 window 对象，所以要先备份上下文，用self或that或_this）
        var self = this;
        // 变法让定时器、延时器中不出现 this 这个关键字
        setTimeout(function () {
            self.style.backgroundColor = 'red';
        }, 2000);
    }

    var box1 = document.getElementById('box1');
    var box2 = document.getElementById('box2');
    var box3 = document.getElementById('box3');

    box1.onclick = setColorToRed;
    box2.onclick = setColorToRed;
    box3.onclick = setColorToRed;
</script>
</body>
</html>
```



## 六、call和apply

### 6.1 call和apply能指定函数的上下文

```javascript
function sum() {
    alert(this.chinese + this.math + this.english);
}

var xiaoming = {
    chinese: 80,
    math: 95,
    english: 93
};
```

将 xiaoming 变为 sum() 的上下文就可以了。

`sum.call(xiaoming);` 或 `sum.apply(xiaoming);`

- `函数.call(上下文);`
- `函数.apply(上下文);`

```javascript
function sum() {
    console.log(this.chinese + this.math + this.english);
}

var xiaoming = {
    chinese: 80,
    math: 95,
    english: 93
};

sum.call(xiaoming);		// 268
sum.apply(xiaoming);	// 268
```

> 当然直接利用规则1方法也行：
>
> ```javascript
> function sum() {
> 	alert(this.chinese + this.math + this.english);
> }
> 
> var xiaoming = {
> 	chinese: 80,
> 	math: 95,
> 	english: 93,
> 	sum: sum
> };
> 
> xiaoming.sum();
> ```

### 6.2 call和apply的区别（参数形式不同）

```javascript
function sum(b1, b2) {
    alert(this.c + this.m + this.e + b1 + b2);
}

var xiaoming = {
    c: 80,
    m: 95,
    e: 93
};

sum.call(xiaoming, 5, 3);		// 276 call 必须要用逗号罗列参数
sum.apply(xiaoming, [5, 3]);	// 276 apply 必须要把参数写到数组中
```

### 6.3 到底使用call还是apply？

```javascript
function fun1() {
    fun2.apply(this, arguments);	// arguments 是数组，只能用 apply
	// 因为 fun1 是用 () 直接调用的，所以 fun1 的上下文 this 为 window 对象
    // 当然，这里之所以写 this 是因为必须要有一个上下文指定，所以就写个 this 代替
}

function fun2(a, b) {
    console.log(a + b);
}

fun1(33, 44);	// 77
```

### 6.4 上下文规则总结

| 规则               | 上下文          |
| ------------------ | --------------- |
| `对象.函数()`      | 对象            |
| `函数()`           | window          |
| `数组[下标]()`     | 数组            |
| `IIFE`             | window          |
| `定时器`           | window          |
| `DOM 事件处理函数` | 绑定 DOM 的元素 |
| `call 和 apply`    | 任意指定        |

> **一句话：函数的上下文只有函数在被执行的时候才会知道。且执行时谁调用的函数，函数的上下文就是谁，否则就是 window 对象。**

## 七、用new操作符调用函数

现在，我们学习一种新的函数调用方式：`new 函数()`

你可能知道 new 操作符和 “面向对象” 息息相关，但是现在我们先不探讨它的 “面向对象” 意义，而是先把用 new 调用函数的执行步骤和它上下文弄清楚。

### 7.1 用new调用函数的四步走

JS 规定，使用 new 操作符调用函数会进行 “四步走”：

1. 函数体内会自动创建出一个空白对象
2. 函数的上下文（this）会指向这个对象
3. 函数体内的语句会执行
4. 函数会自动返回上下文对象，即使函数没有 return 语句

### 7.2 四步走详解

```javascript
function fun() {
    this.a = 3;
    this.b = 5;
}

var obj = new fun();
console.log(obj);	// fun { a: 3, b: 5 }
```

**【第一步：函数体内会自动创建出一个空白对象】**

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/734f6064b1274f0ba011d8a7a8e7dfd4.png)

**【第二步：函数的上下文（this）会指向这个对象】**

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/2346ce01c7264015a9890fd2317e01e1.png)

**【第三步：执行函数体中的语句】**

> 之后这个对象就不再是空对象了。

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220211181748464.png)

**【第四步：函数会自动返回上下文对象，即使函数没有 return 语句】**

> 执行结果为：{a: 3, b: 5}

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/3aab18d93cc04d0a82ce3db482135cd1.png)

【案例】

```javascript
function fun() {
    this.a = 3;
    this.b = 6;
    var m = 34;
    if (this.a > this.b) {
        this.c = m;
    } else {
        this.c = m + 2;
    }
}

var obj = new fun();
console.log(obj);

// fun { a: 3, b: 6, c: 36 }
```

### 7.3 上下文规则总结

| 规则              | 上下文           |
| ----------------- | ---------------- |
| `对象.函数()`     | 对象             |
| `函数()`          | window           |
| `数组[下标]()`    | 数组             |
| `IIFE`            | window           |
| `定时器`          | window           |
| `DOM事件处理函数` | 绑定 DOM 的元素  |
| `call和apply`     | 任意指定         |
| `用new调用函数`   | 秘密创建出的对象 |

## 八、构造函数

### 8.1 什么是构造函数

```javascript
// 书写规范：构造函数首字母大写
// 接收三个参数
function People(name, age, sex) {
    // this上绑定三个参数的同名属性
    this.name = name;
    this.age = age;
    this.sex = sex;
}

// 传入三个参数
var xiaoming = new People('小明', 12, '男');
var xiaohong = new People('小红', 10, '女');
var xiaogang = new People('小刚', 13, '男');

console.log(xiaoming);	// People { name: '小明', age: 12, sex: '男' }
console.log(xiaohong);	// People { name: '小红', age: 10, sex: '女' }
console.log(xiaogang);	// People { name: '小刚', age: 13, sex: '男' }
```

- 用 new 调用一个函数，这个函数就被称为 “构造函数”，任何函数都可以是构造函数，只需要用 new 调用它
- 顾名思义，构造函数用来 “构造新对象”，它内部的语句将为新对象添加若干属性和方法，完成对象的初始化
- 构造函数必须用 new 关键字调用，否则不能正常工作，正因如此，开发者约定构造函数命名时首字母要大写

> 注意：一个函数是不是构造函数，要看它是否用 new 调用，而至于名称首字母大写，完全是开发者的习惯约定。

### 8.2 如果不用new调用构造函数

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}

People('小明', 12, '男');
People('小红', 10, '女');
People('小刚', 13, '男');

/* 此时的 this 为 windown 对象，所以下面三条语句会依次给 windown 的三个属性（全局变量）赋值又相互覆盖 */
```

### 8.3 构造函数中的this不是函数本身

> 构造函数中的 this 不是这个函数本身，而是在这个函数中新创建的空白对象。
>
> 四步走原理！！！

### 8.4 为对象添加方法 

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    // 添加方法
    this.sayHello = function() {
        console.log('我是' + this.name + '，我' + this.age + '岁了');
    };
}

var xiaoming = new People('小明', 12, '男');
var xiaohong = new People('小红', 10, '女');
var xiaogang = new People('小刚', 13, '男');
xiaoming.sayHello();
xiaohong.sayHello();
xiaogang.sayHello();

var say = xiaoming.sayHello;
say();

/*
我是小明，我12岁了
我是小红，我10岁了
我是小刚，我13岁了
我是undefined，我undefined岁了（上下文为 window）
*/
```

> 注意：直接将方法写在构造函数中的方式是不妥的，后面会讲解原因。



# 九、类与实例

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/0c5272275c614edaa9bb5698780bffff.png)

【类好比是 “蓝图”】

如同 “蓝图” 一样，类只描述对象会拥有哪些属性和方法，但是并不具体指明属性的值。

【实例是具体的对象】

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/ac0233152c1c4be08ac08fefa0a77e73.png)

【构造函数和 “类”】

- Java、C++ 等是 **“面向对象”** 语言
- JavaScript 是 **“基于对象”** 语言
- JavaScript 中的构造函数可以类比于 OO 语言中的 “类”，写法的确类似，但和真正 OO语言 还是有本质不同，在后续课程还将看见 JS 和其他 OO 语言完全不同的、特有的原型特性。

> JS 构造函数 ≈ OO 语言 “类”
>
> JS 构造函数可以看做是面向对象语言中的 “类”

# 十、prototype和原型链查找

## 10.1 什么是prototype

任何函数都有 prototype 属性，prototype 是英语 “原型” 的意思。

prototype 属性值是个对象，同时该对象默认拥有 constructor 属性并指回函数，constructor 属性是一个函数。

> constructor：制造商

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/52a1d4d63a1f469eb4c3ef508e2de141.png)

```javascript
function sum(a, b) {
    return a + b;
}
console.log(sum.prototype);
console.log(typeof sum.prototype);
console.log(sum.prototype.constructor);
console.log(typeof sum.prototype.constructor);
console.log(sum.prototype.constructor === sum);
/*
{}
object
[Function: sum]
function
true
*/
```

对于普通函数来说的 prototype 属性没有任何用处，而**构造函数的 prototype 属性非常有用**。

**构造函数的 prototype 属性是它的实例的原型**。

## 10.2 构造函数的prototype是实例的原型

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/2d1fb514299f49e69428be08ea7d9b07.png)

`People.prototype` 是 `xiaoming` 的原型。

`__proto__` 属性：Chrome 提出的一个属性（W3C 中没有）。

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex =sex;
}

// 实例化
var xiaoming = new People('小明', 12, '男');
// 测试三角关系是否存在
console.log(xiaoming.__proto__ === People.prototype);	// true
```

## 10.3 原型链查找

JavaScript 规定：实例可以 “打点” 访问**它的原型的属性和方法**，这被称为 “原型链查找”。

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
// 在构造函数的 prototype 上添加 nationality 属性
People.prototype.nationality = '中国';

var xiaoming = new People('小明', 12, '男');
// 实例可以 “打点” 访问原型的属性和方法
console.log(xiaoming.nationality);	// 中国
```

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/332b6b06736d4a59b6f2df9a7f42d52e.png)

【遮蔽效应】

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex =sex;
}
People.prototype.nationality = '中国';

var xiaoming = new People('小明', 12, '男');
console.log(xiaoming.nationality);	// 中国

var tom = new People('汤姆', 10, '男');
tom.nationality = '美国';

// 被遮蔽
console.log(tom.nationality); // 美国
```

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/eb7937d314024951922741fe0b0a3d97.png)

## 10.4 hasOwnProperty

hasOwnProperty 方法可以检查对象是否真正 “自己拥有” 某属性或者方法。

```javascript
xiaoming.hasOwnProperty('name');		// true
xiaoming.hasOwnProperty('age');			// true
xiaoming.hasOwnProperty('sex');			// true
xiaoming.hasOwnProperty('nationality');	 // false（没有的属性或方法及原型上的属性或方法会返回 false）
```

## 10.5 in

in 运算符只能检查某个属性或方法是否可以被对象访问，不能检查是否是自己的属性或方法。

```javascript
'name' in xiaoming			// true
'age' in xiaoming			// true
'sex' in xiaoming			// true
'nationality' in xiaoming	 // true
'love' in xiaoming			// false
```

# 十一、在prototype上添加方法

## 11.1 之前，我们将方法写到了对象身上

在之前的课程中，我们把方法都是直接添加到实例身上：

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.sayHello = function() {	// 方法直接添加到实例身上
        console.log('我是' + this.name);
    }
}
```

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/faf93b02816b4912a72ca2f09ad4760a.png)

把方法直接添加到实例身上的缺点：每个实例和每个实例的方法函数都是内存中不同的函数，造成了内存的浪费。

解决办法：将方法写到 prototype 上。

## 11.2 方法要写到 prototype 上

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/a2ddf61a4d254ed59ee4a5b34b23001a.png)

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex =sex;
}
// 方法要写到 prototype 上
People.prototype.sayHello = function() {
    console.log('我是' + this.name);
}

People.prototype.sleep = function() {
    console.log(this.name + '开始睡觉.zzzz');
}

var xiaoming = new People('小明', 12, '男');
xiaoming.sayHello();	// 我是小明
xiaoming.sleep();		// 小明开始睡觉.zzzz

var tom = new People('汤姆', 10, '男');

// 同一份方法
console.log(xiaoming.sayHello === tom.sayHello);	// true
```

# 十二、原型链的终点

【原型链的终点】

Object 可以看做是所有对象的构造函数。

所以，People.prototype 这个对象可以看做是 Object new 出来的。

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/29344d84587445a3a94a354a95e998d0.png)

```javascript
function People() {
}
var xiaoming = new People();

console.log(xiaoming.__proto__.__proto__ === Object.prototype);		// true

// Object 是原型链的终点
console.log(Object.prototype.__proto__);	// null
```

【关于数组的原型链】

任何数组实际上都是可以看做是 Array 这个构造函数 new 出来的。

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/4605f0ce53db4bf6a87dbb9032487e24.png)

# 十三、继承

## 13.1 两个无关类

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220211233520473.png" style="zoom: 33%;" />

## 13.2 两个有关类

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220211233716935.png" style="zoom:33%;" />

## 13.3 People类和Student类的关系

- People 类拥有的属性和方法 Student 类都有，Student 类还扩展了一些属性和方法。

- Student “是一种” People，两类之间是 "is a kind of" 关系。

- 这就是继承关系：Student 类继承自 Pelple 类。

## 13.4 继承

- 继承描述了两个类之间的 "is a kind of" 关系
- People 是 “父类”（或 “超类”、“基类”），Student 是 “子类”（或 “派生类”）
- 子类丰富了父类，让类描述得更加具体化、更细化

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220211234613187.png" style="zoom:33%;" />

## 13.5 JavaScript中如何实现继承

- 实现继承的关键在于：子类必须拥有父类的全部属性和方法，同时子类还应该能够定义自己特有的属性和方法
- 使用 JavaScript 特有的原型链特性来实现继承，是普遍的做法
- 在今后学习 ES6 时，将介绍新的实现继承的方法

## 13.6 通过原型链实现继承

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220212014641115.png)

```javascript
// 父类，人类
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}

People.prototype.sayHello = function () {
    console.log('你好，我是' + this.name + '我今年' + this.age + '岁了');
};
People.prototype.sleep = function () {
    console.log(this.name + '开始睡觉，zzzzz');
};

// 子类，学生类
function Student(name, age, sex ,school, studentNumber) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.school = school;
    this.studentNumber = studentNumber;
}

// 关键语句，实现继承
Student.prototype = new People();

Student.prototype.study = function () {
    console.log(this.name + '正在学习');
}
Student.prototype.exam = function () {
    console.log(this.name + '正在考试，加油！');
}

// 重写、复写（override）父类的 sayHello
Student.prototype.sayHello = function () {
    console.log('敬礼！我是' + this.name + '我今年' + this.age + '岁了');
}

// 实例化
var jerry = new Student('周吉瑞', 21, '清华大学', 2019245424);
jerry.study();
jerry.sayHello();
jerry.sleep();
```

# 十四、面向对象案例

- 面向对象的本质：定义不同的类，让类的实例工作
- 面向对象的优点：程序编写更清晰、代码结构更严密、使代码更健壮更利于维护
- 面向对象经常用到的场合：需要封装和复用性的场合（组件思维）

## 14.1 小案例：红绿灯

页面上做一个红绿灯，点击红灯就变黄，点击黄灯就变绿，点击绿灯就变回红灯。

> 思路：设置一个变量，这个变量可以指示当前是什么灯，然后给红绿灯图片添加点击事件，当被点击时让变量依次从红变黄再从黄变绿，同时修改图片的 src 属性。

如果页面上有 100 个这样的红绿灯呢？

> 思路：利用面向对象解决。
>
> - 使用面向对象编程，就能以 “组件化” 的思维解决大量红绿灯相互冲突的问题
> - 面向对象编程，最重要的就是编写类

【TrafficLight 类】

- 属性：自己的当前颜色 `color`、自己的 DOM 元素 `dom`

- 方法：初始化 `init()`、切换颜色 `changeColor()`、绑定事件 `bindEvent()`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta content="width=device-width, initial-scale=1.0" name="viewport">
    <title>Document</title>
    <style>
        #box img {
            width: 80px;
        }
    </style>
</head>
<body>
<div id="box"></div>

<script>
    // 定义红绿灯类（构造函数）
    function TrafficLight() {
        // 颜色属性，一开始都是红色
        // 红色1、黄色2、绿色3
        this.color = 1;
        // 调用自己的初始化方法
        this.init();
        // 绑定监听
        this.bindEvent();
    }

    // 初始化方法
    TrafficLight.prototype.init = function () {
        // 创建自己的DOM
        this.dom = document.createElement('img');
        // 设置src属性
        this.dom.src = 'images/' + this.color + '.jpg';
        box.appendChild(this.dom);
    }

    // 绑定监听
    TrafficLight.prototype.bindEvent = function () {
        // 备份上下文，这里的this指的是JS的实例
        var self = this;
        // 当自己的dom被点击的时候
        this.dom.onclick = function () {
            // 当被点击的时候，调用自己的changeColor方法
            self.changeColor();
            // 如果在这里直接写this，那么this指向的是dom元素本身（事件处理函数的上下文是绑定事件的 DOM 元素）
        };
    }

    // 改变颜色
    TrafficLight.prototype.changeColor = function () {
        // 改变自己的color属性，从而有一种“自治”的感觉，自己管理自己，不干扰别的红绿灯
        this.color++;
        if (this.color === 4) {
            this.color = 1;
        }
        // 光color属性变化没有用，还要更改自己的dom的src属性
        this.dom.src = 'images/' + this.color + '.jpg';
    }

    // 得到盒子
    var box = document.getElementById('box');

    // 实例化100个
    var count = 100;

    while (count--) {
        new TrafficLight();
    }

</script>

</body>
</html>
```

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/231234234123.gif)

## 14.2 小案例：炫彩小球

【Ball 类】

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220212122635036.png)![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220212122701973.png)

**如何实现多个小球动画？**

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220212122934563.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta content="width=device-width, initial-scale=1.0" name="viewport">
    <title>Document</title>
    <style>
        body {
            background-color: black;
        }

        .ball {
            position: absolute;
            border-radius: 50%;
        }
    </style>
</head>

<body>
<script>
    // 小球类
    function Ball(x, y) {
        // 属性x、y表示的是圆心的坐标
        this.x = x;
        this.y = y;
        // 半径属性
        this.r = 20;
        // 透明度
        this.opacity = 1;
        // 小球背景颜色，从颜色数组中随机选择一个颜色
        this.color = colorArr[parseInt(Math.random() * colorArr.length)];
        // 这个小球的x增量和y的增量，使用do while语句，可以防止dX和dY都是零
        do {
            this.dX = parseInt(Math.random() * 20) - 10;
            this.dY = parseInt(Math.random() * 20) - 10;
        } while (this.dX === 0 && this.dY === 0)

        // 初始化
        this.init();
        // 把自己推入数组，注意，这里的this不是类本身，而是实例
        ballArr.push(this);
    }

    // 初始化方法
    Ball.prototype.init = function () {
        // 创建自己的dom
        this.dom = document.createElement('div');
        this.dom.className = 'ball';
        this.dom.style.width = this.r * 2 + 'px';
        this.dom.style.height = this.r * 2 + 'px';
        this.dom.style.left = this.x - this.r + 'px';
        this.dom.style.top = this.y - this.r + 'px';
        this.dom.style.backgroundColor = this.color;
        // 上树
        document.body.appendChild(this.dom);
    };
    // 更新
    Ball.prototype.update = function () {
        // 位置改变
        this.x += this.dX;
        this.y -= this.dY;
        // 半径改变
        this.r += 0.2;
        // 透明度改变
        this.opacity -= 0.01;
        this.dom.style.width = this.r * 2 + 'px';
        this.dom.style.height = this.r * 2 + 'px';
        this.dom.style.left = this.x - this.r + 'px';
        this.dom.style.top = this.y - this.r + 'px';
        this.dom.style.opacity = this.opacity;

        // 当透明度小于0的时候，就需要从数组中删除自己，DOM元素也要删掉自己
        if (this.opacity < 0) {
            // 从数组中删除自己
            for (var i = 0; i < ballArr.length; i++) {
                if (ballArr[i] === this) {
                    ballArr.splice(i, 1);
                }
            }
            // 还要删除自己的dom
            document.body.removeChild(this.dom);
        }
    };


    // 把所有的小球实例都放到一个数组中
    var ballArr = [];

    // 初始颜色数组
    var colorArr = ['#66CCCC', '#CCFF66', '#FF99CC', '#FF6666',
        '#CC3399', '#FF6600'];

    // 定时器，负责更新所有的小球实例
    setInterval(function () {
        // 遍历数组，调用调用的update方法
        for (var i = 0; i < ballArr.length; i++) {
            ballArr[i].update();
        }
    }, 20);

    // 鼠标指针的监听
    document.onmousemove = function (e) {
        // 得到鼠标指针的位置
        var x = e.clientX;
        var y = e.clientY;

        new Ball(x, y);
    };
</script>
</body>

</html>
```

![](/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/124123412341234123.gif)

# 十五、包装类

- Number()、String()、Boolean() 分别是数字、字符串、布尔值的 “包装类”
- 很多编程语言都有 “包装类” 的设计，包装类的目的就是为了让基本类型值可以从它们的构造函数的 prototype 上获得方法

## 15.1 举例

请看下面的程序：

```javascript
var a = new Number(123);
var b = new String('慕课网');
var c = new Boolean(true);

console.log(a);					// [Number: 123]
console.log(typeof a);			// object
console.log(b);					// [String: '慕课网']
console.log(typeof b);			// object
console.log(c);					// [Boolean: true]
console.log(typeof c);			// object

console.log(5 + a);				// 128
console.log(b.slice(0, 2));		// 慕课
console.log(c && true);			// true

var d = 123;
console.log(d.__proto__ == Number.prototype);	// true

var e = '慕课网';
console.log(e.__proto__ == String.prototype);	// true
```

a、b、c 是基本类型值吗？它们和普通的数字、字符串、布尔值有什么区别？

<img src="/Users/pigcharid/Desktop/I-love-you-3-thousand/我爱你，不止三千遍/JavaScript/09【面向对象】/mark-img/image-20220212162000631.png" style="zoom:50%;" />

## 15.2 总结

- Number()、String() 和 Boolean() 的实例都是 object 类型，它们的 PrimitiveValue 属性存储它们的本身值
- new 出来的基本类型值可以正常参与运算
- 包装类的目的就是为了让基本类型值可以从它们的构造函数的 prototype 上获得方法（打点调用）

> ```javascript
> var d = 123;
> console.log(d.__proto__ == Number.prototype);	// true
> 
> var e = '慕课网';
> console.log(e.__proto__ == String.prototype);	// true
> ```
>
> 从以上代码可以看出，直接定义的基本变量本质也是 new 出来的，所以才可以直接打点调用相关方法。

> 注意：只有 Number()、String()、Boolean() 才是包装类， 而 Array() 不是数组的包装类，因为数组不是基本类型谈不上 “包装类” 这一说法的。

