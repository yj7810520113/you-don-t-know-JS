 最小特权原则：在不影响功能的前提下，变量尽可能存在于子作用域中。

## 函数作用域：

```
var a=2;
function foo(){
    var a=3;
    console.log(a);//3
}
foo();
console.log(a);//2
```

上面的例子中，内部变量和函数的定义隐藏了起来，外部的作用域无法访问包装在函数内部的任何内容。

```
var a=2;
    var a=3;
    console.log(a);//3
})();
console.log(a);//2
/*
 *(function(){})()过程：函数被包含在()内部，因此成为了一个表达式，通过在末尾加上另外一个()可以立即执行这个函数，即第一个()将函数变为表达式，第二个()执行了这个函数
 *(function(){}())和(function(){})()功能完全相同
 */
```

上面的例子中，函数被当做表达式（判断是函数声明还是表达式的方法：function是声明中的第一个词，就是函数声明，否则为表达式）。

####  函数声明和函数表达式之间的区别：

第一个代码中，foo被绑定在其所在的作用域中，第二个代码片段foo被绑定在函数表达式自身的函数中而不是在所在的作用域中。

## \(function\(\){}\)\(\)用法：

### 1.当做函数调用并传递参数进去

```
var a=2;
(function(golbal){
    var a=3;
    console.log(a);//3
    console.log(global.a);//2
})(window)
console.log(a);//2
```

#### 2.解决undefined标识符的默认值被错误覆盖导致的异常？

```
undefined = true; // 给其他代码挖了一个大坑！绝对不要这样做！
(function IIFE( undefined ) {
    var a;
    if (a === undefined) {
    console.log( "Undefined is safe here!" );
}
})();
```

#### 3.倒置代码的运行顺序，将需要运行的函数放在第二位，在立即执行函数执行之后当做参数传递进去，在UMD项目中广泛使用

```
var a = 2;
(function IIFE( def ) {
    def( window );
})(function def( global ) {
    var a = 3;
    console.log( a ); // 3
    console.log( global.a ); // 2
});
```





```

```

 





 



