# this
`this`是 JavaScript 语言的一个关键字。

它是函数运行时，在函数体内部自动生成的一个对象，只能在函数体内部使用。
```
function test() {
　this.x = 1;
}
```
函数的不同使用场合，this有不同的值。总的来说，this就是函数运行时所在的环境对象。下面分四种情况，详细讨论this的用法

**以下代码公用函数fun**
### 情况一：纯粹的函数调用
此种情况下，函数被全局调用，this代表全局对象window。
```
function foo() {
  console.log(this.a)
}
var a = 1
foo();//1
```

### 情况二：作为对象方法的调用
这种情况，谁调用了函数，谁就是 this。
```
const obj = {
  a: 2,
  foo: foo
}
obj.foo();//2
```
### 情况三 作为构造函数调用
对于 new 的方式来说，this 被永远绑定在了 c 上面，不会被任何方式改变 this。
```
const c = new foo();//输出 undefined
```
### 情况四 apply 调用
apply()是函数的一个方法，作用是改变函数的调用对象。它的第一个参数就表示改变后的调用这个函数的对象。因此，这时this指的就是这第一个参数。
```
foo.apply(obj);//2
```
### 情况五 箭头函数中的this
箭头函数其实是没有 this 的，箭头函数中的 this 只取决包裹箭头函数的第一个普通函数的 this。
```
function a() {
  return () => {
    return () => {
      console.log(this)
    }
  }
}
console.log(a()()()) ;//window
```