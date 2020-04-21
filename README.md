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
`alert(null == undefined); //true`
#### Boolean类型
Boolean 类型是 ECMAScript 中使用得最多的一种类型，该类型只有两个字面值：true 和 false。这两个值与数字值不是一回事，因此 true 不一定等于 1，而false 也不一定等于 0。以下是为变量赋Boolean 类型值的例子：
```js
var found = true;
var lost = false; 
```