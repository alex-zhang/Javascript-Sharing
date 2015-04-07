# Javascript-Sharing

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


