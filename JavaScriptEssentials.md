# JavaScriptEssentials

## [Reading JS Basics Course](https://www.programiz.com/javascript/get-started)
## [Friendly and complete js tutorial that covers every topic](https://javascript.info)

## Tasks that might be asked during the interview

- How many data types are there in modern JS?
```js
// What output will the following code produce?
console.log(typeof 1);
console.log(typeof '');
console.log(typeof {});
console.log(typeof (() => {}));
console.log(typeof function() {});
console.log(typeof true);
console.log(typeof NaN);
console.log(typeof undefined);
console.log(typeof null);
console.log(typeof 12n);
console.log(typeof []);
```
- Data types convesion
```js
// What output will the following code produce?
console.log('3' + 2);
console.log('3' + true);
console.log('3' + undefined);
console.log('4' * 2;)
console.log(3 - '2';
console.log(4 + true);
console.log('hello' - 'world');
```

- What is Symbol type used for?
- Difference between value types and reference types
```js
// What output will the following code produce?
const x = {};

function foo(y) {
  y.a = 2;
};

foo(x);

console.log(x);

function bar(y) {
  y = {}
}

bar(x);

console.log(x);

const z = 23;

function baz(y) {
  y = 25;
}
baz(z);
console.log(z);
```
- Hoisting. How does the hoisting work?
```js
// What output will the following code produce?
x();

function x() {
  console.log(22);
}
```
```js
// What output will the following code produce?
console.log(x);
var x = 20;
function x() {
}
console.log(x);
```

```js
// What output will the following code produce?
var x = 2;

function y(x) {
  console.log(++x);
}

y(x);

console.log(x);
```

```js
// What output will the following code produce?
var x = 2;

function y() {
  console.log(++x);
}

y();

console.log(x);
```

```js
// What output will the following code produce?
var x = 2;

function y() {
  x = 1;
  console.log(x);
  {
    var x = 3;
  }
  console.log(x);
}

y();

console.log(x);
```
- Variable declaration. Difference between var, let, const?
```js
// Is this code erroneous
x = 2;
var x;
```

```js
// Is this code erroneous
x = 2;
let x;
```

```js
// Is this code erroneous
const x = {};
x = 2;
```

```js
// Is this code erroneous
const x = {};
x.someProp = 2;
```

- Function context. How do you understand keyword this in JS?
- Difference between ordinary and arrow function
- Methods to modify function context

```js
// What output will the following code produce?
const obj = {
  name: 'John',
  sayHi() {
    console.log('Hi!, I am ' + this.name);
  },
  sayHiArrow: () => {
    console.log('Hi!, I am ' + this.name);
  },
  anotherObj: {
    name: 'Pete',
    sayHi() {
      console.log('Hi!, I am ' + this.name);
    }
  }
}

obj.sayHi();
obj.sayHiArrow();
obj.anotherObj.sayHi();
const func = obj.sayHi;
func();
func.apply(obj);
func.call(obj.anotherObj);
const func2 = obj.sayHi.bind(obj.anotherObj);
func2();
```

