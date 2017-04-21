# 作用域和RHS、LHS

RHS：目的是获取变量的值，对于不存在变量会抛出ReferenceError异常；对于变量的不合理操作如引用不存在的属性会抛出TypeError

LHS：目的是对变量进行赋值，对于严格模式中，查找变量失败会抛出ReferenceError异常

#### example:

```
function foo(a){
    var b=a;
    return a+b
}
var c=foo(2);
```

 LHS：有3次

 c=、a=、b=

RHS：有4次

 b=a、a...、...b、foo\(2\)







