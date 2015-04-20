# Javascript-Sharing

```javascript
var v = function() { return 1; }
var t = function() { return false; }

(function() {
    if(t()) {
        t = function() { return false; }
        v = function() { return 2; }
    }
    
    t = function() { return false };
    
    if(t() && [] == ![]) {
        v = function() { return 3; }
        function t() { return true; }
    }
})();

console.log(v());
```

### JavaScript 中所有变量都是对象，除了两个例外 null 和 undefined

```javascript
false.toString(); // 'false'
[1, 2, 3].toString(); // '1,2,3'

function Foo(){}
Foo.bar = 1;
Foo.bar; // 1

3.toString(); // SyntaxError

//一个常见的误解是数字的字面值（literal）不是对象。这是因为 JavaScript 解析器的一个错误， 
// 它试图将点操作符解析为浮点数字面值的一部分。

(3).toString();
3..toString();
3['toString']();
```

### JavaScript 的对象可以作为哈希表使用，主要用来保存命名的键与值的对应关系
```javascript
var foo = {}; // 一个空对象

// 一个新对象，拥有一个值为12的自定义属性'test'
var bar = {test: 12}; 

var f = function() {};
f.a = 3;//f.a = 3;

var arr = [];
arr.help = 'help'; //help
```

## 访问对象的属性，点操作符或者中括号操作符。
```javascript
var foo = {name: 'kitten'}
foo.name; // kitten
foo['name']; // kitten

var get = 'name';
foo[get]; // kitten

foo.1234; // SyntaxError
//点操作符的属性名是一个有效的变量名， 而中括号则要更宽泛点。
foo['1234']; // works
```

### 删除对象属性
```javascript
var a = {};
a.name = 'hello';
console.log(Object.keys(a));//name
a.name = undefined;
console.log(Object.keys(a));//name

delete a.name;

//但是某些属性是否可以删除是可以定义的
//如var 声明的属性不可以删除
```

### 原型和原型链
```javascript
function Foo() {
    this.value = 42;
}
Foo.prototype = {
    method: function() {}
};
```

### 属性查找

当查找一个对象的属性时，JavaScript 会向上遍历原型链，直到找到给定名称的属性为止。

到查找到达原型链的顶部 - 也就是 Object.prototype - 但是仍然没有找到指定的属性，就会返回 undefined。

## 原型属性

当原型属性用来创建原型链时，可以把任何类型的值赋给它（prototype）。 然而将原子类型赋给 prototype 的操作将会被忽略。

```javascript
function Foo() {}
Foo.prototype = 1; // 无效
```

### 属性查找性能

如果一个属性在原型链的上端，则对于查找时间将带来不利影响。特别的，试图获取一个不存在的属性将会遍历整个原型链。


```javascript
//原型链上的所有属性可能都将被访问。
'name' in o

//唯一不遍历原型链的API
o.hasOwnProperty('key');
```



## 语法

```javascript
Number.prototype.add = function (x) {
  return this + x;
};

3.add(3); //Uncaught SyntaxError: Unexpected token ILLEGAL
(3..add(3); //6
3['add'](3);//6
(3).add(3);//6
(3).add(1).add(2); //6

Number.prototype = Object.defineProperty(
  Number.prototype, "double", {
    get: function (){return (this + this)} 
  }
);

```

````
0.1 + 0.2 = 0.30000000000000004


