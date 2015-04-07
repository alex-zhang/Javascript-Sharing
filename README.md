# Javascript-Sharing

## JavaScript 中所有变量都是对象，除了两个例外 null 和 undefined

```javascript
false.toString(); // 'false'
[1, 2, 3].toString(); // '1,2,3'

function Foo(){}
Foo.bar = 1;
Foo.bar; // 1

2.toString(); // SyntaxError
(2).toString();
2..toString();
2[toString]();
```

## JavaScript 的对象可以作为哈希表使用，主要用来保存命名的键与值的对应关系
```javascript
var foo = {}; // 一个空对象

// 一个新对象，拥有一个值为12的自定义属性'test'
var bar = {test: 12}; 

var f = function() {};
f.a = 3;//f.a = 3;

var arr = [];
arr.help = 'help'; //help
```

## 有两种方式来访问对象的属性，点操作符或者中括号操作符。
```javascript
var foo = {name: 'kitten'}
foo.name; // kitten
foo['name']; // kitten

var get = 'name';
foo[get]; // kitten

foo.1234; // SyntaxError
foo['1234']; // works
```
 点操作符的属性名是一个有效的变量名， 而中括号则要更宽泛点。

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


