# typeof vs instanceof
## typeof
typeof返回的是字符串。
typeof对于原始类型来说，除了null都可以正确判断类型。

`原始类型`: null、undefined、string、number、symbol、boolean
```
typeof 1 // 'number'
typeof '1' // 'string'
typeof undefined // 'undefined'
typeof true // 'boolean'
typeof Symbol() // 'symbol'
typeof null //'object'
```
typeof对于引用类型来说，除了函数显示function其他都判断为object
```
typeof [] // 'object'
typeof {} // 'object'
typeof console.log // 'function'
```
## instanceof
instanceof运算符用于测试构造函数的prototype属性是否出现在对象的原型链中的任何位置。
内部机制是通过原型链来实现的。
```
const Person = function() {}
const p1 = new Person();
p1 instanceof Person // true
// p1.__proto__ === Person.prototype

var str = 'hello world'
str instanceof String // false

var str1 = new String('hello world')
str1 instanceof String // true
```
