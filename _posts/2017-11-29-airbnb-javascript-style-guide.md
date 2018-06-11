---
title: Airbnb JavaScript Style Guide
date: 2017-11-29
categories: [developer]
tags: [code-style]
excerpt_separator: <!--more-->
---

```javascript
AirbnbJavaScriptStyleGuide() {
/*
 * Airbnb JavaScript Style Guide
 * 用更合理的方式写 JavaScript
 */
}
```

<!--more-->

### 类型
* **原始值: 存取直接作用于它自身。**

  * string
  * number
  * boolean
  * null
  * undefined

```javascript
var foo = 1;
var bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
```

* **复杂类型: 存取时作用于它自身值的引用。**

  * object
  * array
  * function

```javascript
var foo = [1, 2];
var bar = foo;

bar[0] = 9;

console.log(foo[0], bar[0]); // => 9, 9
```

### 对象
* **使用直接量创建对象。**

```javascript
// bad
var item = new Object();

// good
var item = {};
```

* **不要使用*[保留字](http://es5.github.io/#x7.6.1)*作为键名，它们在 IE8 下不工作。**

```javascript
// bad
var superman = {
  default: { clark: 'kent' },
  private: true
};

// good
var superman = {
  defaults: { clark: 'kent' },
  hidden: true
};
```

* **使用同义词替换需要使用的保留字。**

```javascript
// bad
var superman = {
  class: 'alien'
};

// bad
var superman = {
  klass: 'alien'
};

// good
var superman = {
  type: 'alien'
};
```


### 数组
* **使用直接量创建数组。**

```javascript
// bad
var items = new Array();

// good
var items = [];
```

* **向数组增加元素时使用 Array#push 来替代直接赋值。**

```javascript
var someStack = [];


// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```

* **当你需要拷贝数组时，使用 Array#[slice](http://www.w3school.com.cn/jsref/jsref_slice_array.asp)。**

```javascript
var len = items.length;
var itemsCopy = [];
var i;

// bad
for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
itemsCopy = items.slice();
```

* **使用 Array#slice 将类数组对象转换成数组。**

```javascript
function trigger() {
  var args = Array.prototype.slice.call(arguments);
  ...
}
```

### 字符串

* **使用单引号 '' 包裹字符串。**

```javascript
// bad
var name = "Bob Parr";

// good
var name = 'Bob Parr';

// bad
var fullName = "Bob " + this.lastName;

// good
var fullName = 'Bob ' + this.lastName;
```

* **超过 100 个字符的字符串应该使用连接符写成多行。**
* **注：若过度使用，通过连接符连接的长字符串可能会影响性能。**

```javascript
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
var errorMessage = 'This is a super long error that was thrown because \
of Batman. When you stop to think about how Batman had anything to do \
with this, you would get nowhere \
fast.';

// good
var errorMessage = 'This is a super long error that was thrown because ' +
  'of Batman. When you stop to think about how Batman had anything to do ' +
  'with this, you would get nowhere fast.';
```

* **程序化生成的字符串使用 Array#join 连接而不是使用连接符。**

```javascript
var items;
var messages;
var length;
var i;

messages = [{
  state: 'success',
  message: 'This one worked.'
}, {
  state: 'success',
  message: 'This one worked as well.'
}, {
  state: 'error',
  message: 'This one did not work.'
}];

length = messages.length;

// bad
function inbox(messages) {
  items = '<ul>';

  for (i = 0; i < length; i++) {
    items += '<li>' + messages[i].message + '</li>';
  }

  return items + '</ul>';
}

// good
function inbox(messages) {
  items = [];

  for (i = 0; i < length; i++) {
    // use direct assignment in this case because we're micro-optimizing.
    items[i] = '<li>' + messages[i].message + '</li>';
  }

  return '<ul>' + items.join('') + '</ul>';
}
```

### 函数
* **函数表达式：**

```javascript
// 匿名函数表达式
var anonymous = function() {
  return true;
};

// 命名函数表达式
var named = function named() {
  return true;
};

// 立即调用的函数表达式（IIFE）
(function () {
  console.log('Welcome to the Internet. Please follow me.');
}());
```
> 永远不要在一个非函数代码块（if、while 等）中声明一个函数，浏览器允许你这么做，但它们的解析表现不一致，正确的做法是：在块外定义一个变量，然后将函数赋值给它。

* **注： ECMA-262 把 块 定义为一组语句。函数声明不是语句。**

```javascript
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
var test;
if (currentUser) {
  test = function test() {
    console.log('Yup.');
  };
}
```

* **永远不要把参数命名为 `arguments`。这将取代函数作用域内的 `arguments` 对象。**

```javascript
// bad
function nope(name, options, arguments) {
  // ...stuff...
}

// good
function yup(name, options, args) {
  // ...stuff...
}
```

### 属性

* **使用 `.` 来访问对象的属性。**

```javascript
var luke = {
  jedi: true,
  age: 28
};

// bad
var isJedi = luke['jedi'];

// good
var isJedi = luke.jedi;
```

* **当通过变量访问属性时使用中括号 `[]`。**

```javascript
var luke = {
  jedi: true,
  age: 28
};

function getProp(prop) {
  return luke[prop];
}

var isJedi = getProp('jedi');
```

### 变量

* **总是使用 `var` 来声明变量。不这么做将导致产生全局变量。我们要避免污染全局命名空间。**

```javascript
// bad
superPower = new SuperPower();

// good
var superPower = new SuperPower();
```

* **使用 `var` 声明每一个变量。 这样做的好处是增加新变量将变的更加容易，而且你永远不用再担心调换错 `;` 跟 `,`**

```javascript
// bad
var items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';

// bad
// （跟上面的代码比较一下，看看哪里错了）
var items = getItems(),
    goSportsTeam = true;
    dragonball = 'z';

// good
var items = getItems();
var goSportsTeam = true;
var dragonball = 'z';
```

* **最后再声明未赋值的变量。当你需要引用前面的变量赋值时这将变的很有用。**

```javascript
// bad
var i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// bad
var i;
var items = getItems();
var dragonball;
var goSportsTeam = true;
var len;

// good
var items = getItems();
var goSportsTeam = true;
var dragonball;
var length;
var i;
```

* **在作用域顶部声明变量。这将帮你避免变量声明提升相关的问题。**

```javascript
// bad
function () {
  test();
  console.log('doing stuff..');

  //..other stuff..

  var name = getName();

  if (name === 'test') {
    return false;
  }

  return name;
}

// good
function () {
  var name = getName();

  test();
  console.log('doing stuff..');

  //..other stuff..

  if (name === 'test') {
    return false;
  }

  return name;
}

// bad - 不必要的函数调用
function () {
  var name = getName();

  if (!arguments.length) {
    return false;
  }

  this.setFirstName(name);

  return true;
}

// good
function () {
  var name;

  if (!arguments.length) {
    return false;
  }

  name = getName();
  this.setFirstName(name);

  return true;
}
```
### [...](https://github.com/sivan/javascript-style-guide/blob/master/es5/README.md)

---

来源：*Sivan Sun* 
链接：*https://github.com/sivan/javascript-style-guide/blob/master/es5/README.md*




























