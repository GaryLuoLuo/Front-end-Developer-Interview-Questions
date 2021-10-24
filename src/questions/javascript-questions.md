---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---

* Explain event delegation.
* Explain how `this` works in JavaScript.
  * Can you give an example of one of the ways that working with `this` has changed in ES6?
* Explain how prototypal inheritance works.
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
* What language constructions do you use for iterating over object properties and array items?
* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
* What's a typical use case for anonymous functions?
* What's the difference between host objects and native objects?
* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
* Explain `Function.prototype.bind`.
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain "hoisting".
* Describe event bubbling.
* Describe event capturing.
* What's the difference between an "attribute" and a "property"?
* What are the pros and cons of extending built-in JavaScript objects?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
* What is strict mode? What are some of the advantages/disadvantages of using it?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* What are the differences between variables created using `let`, `var` or `const`?
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
* Can you give an example of generating a string with ES6 Template Literals?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
* What is the difference between `while` and `do-while` loops in JavaScript?
* What is a promise? Where and how would you use promise?

## Coding questions
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* What will be returned by each of these?
```javascript
console.log("hello" || "world")
console.log("foo" && "bar")
```
* Write an immediately invoked function expression (IIFE)

---
* 构造函数 constructor functions - 大写, e.g. Object String Array Person   
declaring an obj literal `const a = {}` and using a constructor fn `class/fn + new` - both generate obj    
other ways to create obj:  
-  `let person1 = new Object({obj literal});`   
-  `let person2 = Object.create(person1);`  creating only a few instances of an object.   using an existing object as the prototype of the newly created object.   
```
function Person(name) {
  this.name = name;
  this.greeting = function() {
    alert('Hi! I\'m ' + this.name + '.');
  };
}
let person1 = new Person('Bob');
person1.name
person1.greeting()
```
* 原型 Prototypes are the mechanism by which JavaScript objects inherit features from one another.  
The prototype property's value is an object, which is basically **a bucket for storing properties and methods that we want to be inherited by objects further down the prototype chain**.  So Object.prototype.toString(), Object.prototype.valueOf(), etc., are available to any object types that inherit from Object.prototype, including new object instances created from the Person() constructor.  Object.is(), Object.keys() are not inheritable.   

* 对象的__proto__属性和该对象的构造函数的prototype属性是同一个对象，既该实例对象的原型对象。  
```
let A = function () {};

let a = new A();
let b = new String('b');
// 都是该实例对象的原型对象。
console.log(a.__proto__ === A.prototype); // true
console.log(b.__proto__ === String.prototype); // true
```
构造函数的 prototype instead is a property containing an object on which you define members that you want to be inherited.  

* The constructor property  
  - Every constructor function has a prototype property whose value is an object containing a constructor property. This constructor property points to the original constructor function.    
  - WARNING: `let B = function () {}` !== `let C = () => {}`, B.prototype ✔️ C.prototype 😫 not exist
  - B.prototype.constructor === B
  - object definitions pattern - define the properties inside the constructor, and the methods on the prototype.
```
// Constructor with property definitions

function Test(a, b, c, d) {
  // property definitions
}

// First method definition

Test.prototype.x = function() { ... };

// Second method definition

Test.prototype.y = function() { ... };

// etc.
```

* Inheritance  
    - update inheritance chain dynamically, `Person.prototype.farewell = function() {}`
    - performing `delete person1.__proto__.farewell` or `delete Person.prototype.farewell` would remove the `farewell()` method from all Person instances.
