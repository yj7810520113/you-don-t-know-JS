词法作用域的作用域是在书写代码时函数声明的位置决定的

## 欺骗词法作用域的方法

 eval和with会在运行时修改或创建新的作用域，以此来欺骗在书写时定义的词法作用域

1.eval\(\)：对包含代码的字符串进行演算，借此来修改已经存在的词法作用域（运行时）

 eval可以在写的代码中用程序生成代码

```
function foo(str,a){
    eval(str);
    console.log(a,b);
}
b=2;
foo('var b=3',1)//1,3
```

2.with\(\)：将一个对象的引用当做作用域来处理，将对象的属性当做作用域的标示符来处理，从而创建了一个新的词法作用域（运行时）

```
function foo(obj){
    with(obj){
        a=2;
    }
}
var o1={
    a=1;
}
var o2={
    b=1;
}
foo(o1);
console.log(o1.a);//2
foo(o2);
console.log(o2.a)//undefined
console.log(a);//2  被泄露到全局作用域上了
```









