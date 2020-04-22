# 从零开始学习web前端
## 从零开始读JavaScript高级程序设计
### JavaScript简介
javascript由核心(ECMAScript)、文档对象模型(DOM)、浏览器对象模型(BOM)
#### 严格模式
`"use strict"; `
#### Undefined类型
Undefined 类型只有一个值，即特殊的 undefined。在使用 var 声明变量但未对其加以初始化时，
这个变量的值就是 undefined，例如：
```javascript 
var message;
alert(message == undefined); //true
```
#### Null类型
Null 类型是第二个只有一个值的数据类型，这个特殊的值是 null。从逻辑角度来看，null 值表
示一个空对象指针，而这也正是使用 typeof 操作符检测 null 值时会返回"object"的原因，如下面
的例子所示：
```js
var car = null;
alert(typeof car); // "object" 
```
如果定义的变量准备在将来用于保存对象，那么最好将该变量初始化为 null 而不是其他值。这样一来，只要直接检查 null 值就可以知道相应的变量是否已经保存了一个对象的引用，如下面的例子所示：
```js
if (car != null){
 // 对 car 对象执行某些操作
} 
```
实际上，undefined 值是ี生自 null 值的，因此 ECMA-262 规定对它们的相等性测试要返回 true：
```js
alert(null == undefined); //true
```
#### Boolean类型
Boolean 类型是 ECMAScript 中使用得最多的一种类型，该类型只有两个字面值：true 和 false。这两个值与数字值不是一回事，因此 true 不一定等于 1，而false 也不一定等于 0。以下是为变量赋Boolean 类型值的例子：
```js
var found = true;
var lost = false; 
```
虽然 Boolean 类型的字面值只有两个，但 ECMAScript 中所有类型的值都有与这两个 Boolean 值等价的值。要将一个值转换为其对应的 Boolean 值，可以调用转型函数 Boolean()，如下例所示：
```js
var message = "Hello world!";
var messageAsBoolean = Boolean(message);
```
#### Number类型
##### NaN
NaN，即非数值（Not a Number）是一个特殊的数值，这个数值用于表示一个本来要返回数值的操作数未返回数值的情况（这样就不会出错误了）。例如，在其他编程语言中，任何数值除以 0都会导致错误，从而停止代码执行。但在 ECMAScript中，任何数值除以 0会返回 NaN，因此不会影响其他代码的执行。

NaN 本身有两个非同寻常的特点。首先，任何涉及 NaN 的操作（例如 NaN/10）都会返回 NaN，这个特点在多步计算中有可能导致问题。其次，NaN 与任何值都不相等，包括 NaN 本身。例如，下面的代码会返回 false：
```js
alert(NaN == NaN); // false
```
针对 NaN 的这两个特点，ECMAScript 定义了 isNaN()函数。这个函数接受一个参数，该参数可以是任何类型，而函数会帮我们确定这个参数是否“不是数值”。isNaN()在接收到一个值之后，会尝试将这个值转换为数值。某些不是数值的值会直接转换为数值，例如字符串"10"或 Boolean 值。而任何不能被转换为数值的值都会导致这个函数返回 true。请看下面的例子：
```js
alert(isNaN(NaN)); //true
alert(isNaN(10)); //false（10 是一个数值）
alert(isNaN("10")); //false（可以转化为数值 10）
alert(isNaN("blue")); //true（不能转为数值）
alert(isNaN(true)); //false（可以转化数值 1）
```
##### 数值转化
有 3 个函数可以把非数值转换为数值：Number()、parseInt()和 parseFloat()。第一个函数，即转型函数 Number()可以用于任何数据类型，而另两个函数则专门用于把字符串转换成数值。这 3 个函数对于同样的输入会有返回不同的结果。
Number()函数的转换规则如下。

- 如果是 Boolean 值，true 和 false 将分别被转换为 1 和 0。

- 如果是数字值，只是简单的传入和返回。

- 如果是 null 值，返回 0。

- 如果是 undefined，返回 NaN。
  
- 如果是字符串，遵循下列规则：
  
    - 如果字符串中只包含数字（包括前面带正号或负号的情况），则将其转换为十进制数值，即"1"会变成 1，"123"会变成 123，而"011"会变成 11（注意：前导的零被忽略了）；
    - 如果字符串中包含有效的๎点格式，如"1.1"，则将其转换为对应的๎点数值（同样，也会忽略前导零）；
    - 如果字符串中包含有效的十六进制格式，例如"0xf"，则将其转换为相同大小的十进制整数值；
    - 如果字符串是空的（不包含任何字符），则将其转换为 0；
    - 如果字符串中包含除上述格式之外的字符，则将其转换为 NaN。
  
- 如果是对象，则调用对象的 valueOf()方法，然后依照前面的规则转换返回的值。如果转换
的结果是 NaN，则调用对象的 toString()方法，然后再次依照前面的规则转换返回的字符
串值。

#### string
数值、布尔值、对象和字符串值（没错，每个字符串也都有一个 toString()方法，该方法返回字符串的一个副本）都有 toString()方法。但 null 和 undefined 值没有这个方法。

在不知道要转换的值是不是 null 或 undefined 的情况下，还可以使用转型函数 String()，这个
函数能够将任何类型的值转换为字符串。String()函数遵循下列转换规则：
- 如果值有 toString()方法，则调用该方法（没有参数）并返回相应的结果
- 如果值是 null，则返回"null"
- 如果值是 undefined，则返回"undefined"
```js
console.log(String(true)) // 'true'
console.log(String(0)) // '0'
console.log(String(null)) // 'null'
console.log(String(undefined)) // 'undefined'
```
### object类型
ECMAScript 中的对象其实就是一组数据和功能的集合。对象可以通过执行 new 操作符后跟要创建
的对象类型的名称来创建。而创建 Object 类型的实例并为其添加属性和（或）方法，就可以创建自定
义对象，如下所示：
```js
var o = new Object()
```
Object 的每个实例都具有下列属性和方法。