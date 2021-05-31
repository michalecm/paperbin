# JavaScriptEssentials

function makeCalc () {
  let sum = 0
  return {
    add: (num) => {
      sum += num
      return sum
    }
  }
}

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
```js
// Is this code erroneous. Why?
  x();
  
  const x = () => {
    console.log(22);
  }
```

- Variable declaration. Difference between var, let, const?
```js
// Is this code erroneous. Why?
x = 2;
var x;
```

```js
// Is this code erroneous. Why?
x = 2;
let x;
```

```js
// Is this code erroneous. Why?
const x = {};
x = 2;
```

```js
// Is this code erroneous. Why?
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
- Scope and closures

```js
// Write a calculator

const calculator = makeCalc();
calculator.add(2);
calculator.print();
// prints 2
calculator.mul(-2);
calculator.print();
// prints -4
calculator.div(-2);
calculator.print();
// prints 2

//advanced! if you want you can try to make calculator a function itself. It will return current value
const l = calculator();
console.log(l);
//prints 2

function makeCalc() {
  // your code here
}
``` 

- What is the difference between scope and context. During which time of program execution each one is created? (Answer is in book "You don't know JS. Scope in closures")
- Asynchronous code. Methods that generate asynchronousity in browser, node.js
- What is async/await in a nutshell?
- Event loop. Stages of Event loop. Micro and macro tasks. 

```js
// Which output will this code produce?
// Why?

setTimeout(() => {
  console.log(1);
  Promise.resolve()
    .then(() => {
      console.log(2);
    })
    .then(() => {
      console.log(3);
    })
}, 0)

Promise.resolve().then(() => {
  console.log(4);
});
console.log(5);
Promise.resolve().then(() => {
  console.log(6);
});

setTimeout(() => {
  console.log(7);
}, 0)

``` 

```js

// Which output will this code produce?
// Why? How to make it work correctly?

for(var i = 0; i < 10; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}

``` 

```js

// Which output will this code produce?
// Why? 

Promise.reject()
  .then(() => console.log(1))
  .catch(() => console.log(2))
  .then(() => console.log(3))
  .catch(() => console.log(4))
  .finally(() => console.log(5))
  
```

- How does inheritance works in JS. Which two methods of inheritance implementation in JS do you know.

```js

// Write a class that does the following.
// don't use class syntax, you are allowed to use prototypes only

const pony = new Pet('pony');
console.log(pet.type); //pony
console.log(pet.speed); //25
console.log(pet.printHi()) // Hi, i am pony. My speed is 25
const tiger = new Tiger();
console.log(tiger.type); // tiger
console.log(tiger.speed); // 30
console.log(tiger.printHi()) // Hi, i am tiger. My speed is 30

// Write it again using es6 class syntax

```

```js

// Write a sortNumbers method, on Array which will be available to use on any array, it'll sort numbers in ascending order.
// It always creates a new array instead of sorting in place
// You are not allowed to use Array.sort in this task. (clue: If you are stuck, you may want to read what bubble sort is)

const arr = [3, 2, 6, 5];
const sortedArray = arr.sortAscending();
console.log(arr)//[3, 2, 6, 5]
console.log(sortedArray)//[2, 3, 5, 6]

```
