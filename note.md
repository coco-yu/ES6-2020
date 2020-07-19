## let
    允许会计作用域的任意嵌套
    外层作用域无法获取内层作用域的变量
    内层作用域可以定义外层作用域的同名变量
    函数本身的作用域在其所在的块级作用域之内

## 严格模式
    严格模式通过抛出错误来消除一些原有的静默错误
    严格模式修复了一些导致javascript引擎难以执行优化的缺陷，有时候相同的代码严格模式要比非严格模式运行的更快
    严格模式禁用了在ECMAScript的未来版本中可能会定义的一些语法

## var let const区别
    var定义的变量没有块的概念，可以跨块访问，不能跨函数访问，有变量提升，可重复声明。
    let定义的变量，只能在块作用域里访问，不能跨块访问，也不能跨函数访问，不可重复声明（在编译阶段就会检测），没有变量提升。
    let声明的变量只在块级作用域内生效，不存在变量提升、而是绑定在暂时性死区。
    或者说let变量提升了，但是在let声明变量前不能使用该变量，这种特性叫暂时性死区
    如果有重复的变量，let会在编译阶段报错。

## 全局变量
    ES5声明方式：var  function
    ES6声明方式：let const import class var function
    浏览器环境中顶层对象是window,Node种是global
    ES5中顶层对象的属性等价于全局变量
    ES6中var function声明的全局变量依然是顶层对象的属性、
    let const class声明的全局变量不属于顶层对象的属性

## this
    当前函数的this是在被调用的时候才确定的
    如果当前的执行上下文处于调用栈的栈顶，这个时候变量对象变成了活动对象
    this指针才能确定
    非严格模式下函数直接执行，没有调用者，this是window或者global
    严格模式下函数直接调用、没有调用者，this是null或者undefined
    如果事件绑定的时候， this就是绑定的元素

## call apply bind原理
    call的原理：
    (function(prototype) {
        function call2(context, ...args) {
            context.getName = this;
            context.getName(...args);
            delete context.getName;
        }
        prototype.call2 = call2;
    })(Function.prototyps);
    getName.call(obj)

## 存放方式
    基本类型存放在栈里
    引用类型存放在堆里

## 基本类型喝引用类型的区别
    基本类型只是一个值
    引用类型是若干个属性的集合

## 私有属性、共有属性
    私有属性放在this,公共属性放在prototype