# JavaScriptEssentials

## [Reading JS Basics Course](https://www.programiz.com/javascript/get-started)
## [Friendly and complete js tutorial that covers every topic](https://javascript.info)

## Tasks that might be asked during the interview

- How many data types are there in modern JS?
There are 8.
String
Number (integer and floating point)
BigInt(integer with arbitrary precision)
Boolean
undefined
null
Symbol (unique and immutable)
Object - key-value pairs of collections of data

```js
// What output will the following code produce?
console.log(typeof 1); #number
console.log(typeof ''); #string
console.log(typeof {}); #objects
console.log(typeof (() => {})); #funtion
console.log(typeof function() {}); #function
console.log(typeof true); #boolean
console.log(typeof NaN); number
console.log(typeof undefined); #undefined
console.log(typeof null); #null
console.log(typeof 12n); #bigint
console.log(typeof []); #object
```
- Data types convesion
```js
// What output will the following code produce?
console.log('3' + 2); #32
console.log('3' + true); #3true
console.log('3' + undefined); #3undefined
console.log('4' * 2); #8
console.log(3 - '2'; #1
console.log(4 + true); #5
console.log('hello' - 'world'); #NaN
```

- What is Symbol type used for?
it is a primitive object that creates guaranteed unique representations of the data it wraps/encapsulates. Used often to create property keys to an object.

- Difference between value types and reference types
- value types hold values/data and reference types are pointers
- values stored in stack, pointers in heap


```js
// What output will the following code produce?
const x = {};
//declares a new object x (reference type)

function foo(y) {
  y.a = 2;
};

//functions that receives y, assigns the value 2 to reference y.a

foo(x);
//sends object x to foo(), which assigns 2 to x.a

console.log(x);
prints the contents of object x, which is a:2

function bar(y) {
  y = {}
}

//function that receives y and creates a new object under it

bar(x);

//sends object x to bar(), but it only reassigns the reference of x during the scope of the function, so when the function exits it reassigns itself to have a:2

console.log(x);
//prints a:2

const z = 23;
//assigns value 23 to constant number z

function baz(y) {
  y = 25;
}

//function that receives y and assigns it 25

baz(z);

//we send baz() z but since z is a constant it cannot be re-assigned, javascript passes the value of z rather than the reference, which is 23

console.log(z);
```
- Hoisting. How does the hoisting work?
in JS, all variable/function declarations are hoisted to the top of the scope of their declaration at the beginning of runtime. Because of this, technically we can call a function or use a variable before we define it.

```js
// What output will the following code produce?
x();

function x() {
  console.log(22);
}
``` -- 22 because the function declaration was hoisted
```js
// What output will the following code produce?
--first it prints the function, then it prints the variable x. This is because the function declaration is moved above the var x initliazation so it is referenced by x first/
console.log(x);
var x = 20;
function x() {
}
console.log(x);
```

```js
--

3
2

because the function is called and prints the varx in its scope before the one outside

// What output will the following code produce?
var x = 2;

function y(x) {
  console.log(++x);
}

y(x);

console.log(x);
```


```js
3
3
because there is no x in the scope of y
// What output will the following code produce?
var x = 2;

function y() {
  console.log(++x);
}

y();

console.log(x);
```

```js
1
3
2
(var x = 3 is moved to top of y)
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
yes it is erroneous because x is declared/initilizaed as a const which is not hoisted
// Is this code erroneous. Why?
  x();
  
  const x = () => {
    console.log(22);
  }
```

- Variable declaration. Difference between var, let, const?
```js
not erroneous, function scoped cant be accessed outside function
but within block scope it is available outside of it
// Is this code erroneous. Why?
x = 2;
var x;
```

```js
is erroneous
block scope - only available inside scope
// Is this code erroneous. Why?
x = 2;
let x;
```

```js
is erroneous
because we are trying to reassign the value of x from obj to number
// Is this code erroneous. Why?
const x = {};
x = 2;
```

```js
not erroneous
no bc we are only reassigning a property of x
// Is this code erroneous. Why?
const x = {};
x.someProp = 2;
```

- Function context. How do you understand keyword this in JS?
 “this” holds the reference to current execution context in javascript
 --if function is called using an object (obj.function()) it will retain a reference to the objext
 --if called as standalone function this will refer to the window object
 --if strict mode defined then this will be undefined
 --keyword can be bound in render method or constructor, because sometimes functions are rescoped at runtime?
 --can be bound correctly using arrow functions, or helper methods for render
- Difference between ordinary and arrow function
- --classic functions create an ~object~ and a scope with its own definition of this keyword
--- arrow functions don't, they inherit their scope, so it can be used to access local context only if it is called/initilized correctly, also arrow functions are shorter and easier to pass around as parameters

- Methods to modify function context
- - can change using call, or apply which can bind THIS to an explicitly new object context
- -- is also automatically changed with 'new' keyword in instantiation
- -- 

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

obj.sayHi(); //John
obj.sayHiArrow(); //___ //inherits global scope
obj.anotherObj.sayHi(); //Pete
const func = obj.sayHi; //accessing this, returns undefined???????
func(); // global context
func.apply(obj); //John
func.call(obj.anotherObj); //Pete
const func2 = obj.sayHi.bind(obj.anotherObj);
func2(); // Pete
```
- Scope and closures

```js
// Write a calculator

function makeCalc () {
  let sum = 0
  return {
    add(num) {
      sum += num
      return sum
    },
    print(){
    	console.log(sum)
    },
    mul(num) {
      sum *= num
      return sum
    },
    div(num) {
      sum /= num
      return sum
    }
  }
}

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
5
4
6
1
2
3
7

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

We need to change var to let, because var will be function-scoped, accessible everywhere, and will be bound to only 1-value (the final # of the loop. Let is block-scoped, and only accessible in the for loop itself. A new copy is created every iteration. Var has 1 copy, let has as many as loop

var doesn't work with the settimeout because of how the loop and function are queued. by the time the settimeout is addressed, var points to 1 value.

with let, every iteration of the loop closes the scope of the variable, so a new i is created for the loop counter, and the previous i is included in the closure of the function inside the loop (settimeout).

with var, it has function scope, so every time the loop iterates, the variable is incremented across the whole function.. so there is no 0..1..2.. stored they all get incremented because they are one variable. The loop closes on the max value because it must update to check the inequality.

for(var i = 0; i < 10; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}

//can fix the issue, because it creates a block scope wherein i 
for(var i = 0; i < 10; i++) {
  ((i) => {
      setTimeout(() => {
      console.log(i);
      }, 0);
  })(i);
}


``` 

closures--
--lexical scoping, variables defined outside scope are already available inside every scope


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
