---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---

* Explain event delegation. 
* Describe event bubbling.
* Describe event capturing.
    - https://dmitripavlutin.com/javascript-event-delegation/
    - Event Delegation is basically a pattern to handle events efficiently. Instead of adding an event listener to each and every similar element, we can add an event listener to a parent element and call an event on a particular target using the .target property of the event object.
    - DOM events are dispatched from the document to the target element (the capturing phase), and then bubble from the target element back to the document (the bubbling phase). 
    - A click event propagates in 3 phases: Capture phase, Target p, Bubble phase. `event.target`, `event.currentTarget`
    - https://codesandbox.io/s/event-propagation-example-71yvl?file=/src/index.js:6-15
```
<div id="buttons"> <!-- Step 1 -->
  <button class="buttonClass">Click me</button>
  <button class="buttonClass">Click me</button>
  <!-- buttons... -->
  <button class="buttonClass">Click me</button>
</div>
<script>
  document.getElementById('buttons')
    .addEventListener('click', event => { // Step 2
      if (event.target.className === 'buttonClass') { // Step 3
        console.log('Click!');
      }
    });
</script>
```
* `"use strict"` 更严格 https://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html
* Explain how `this` works in JavaScript.
    - A property of an **execution context** (global, function or eval) that, in non–strict mode, is always a reference to an object and in strict mode can be any value.
    - global context, (outside of any function), `this === window === globalThis`
    - Function context. Non strict, if not set by the call, is window.  In strict, if no call() or apply(), is undefined.
    - Class context. just the object. `new Person()` this in person becomes Person. `Person()` without new, this in person becomes window. 
    - When a function is called as a method of an object, its this is set to the object the method is called on.
    - DOM its this is set to the DOM element on which the listener is placed
```
var o = {
  prop: 37,
  f: function() {
  // this bound to f context. If no context when f(), this is global (non strict)
    return this.prop;
  }
};
// because o calls f, 'this' in 'f' bounds to 'o' now
console.log(o.f()); // 37

```
* Can you give an example of one of the ways that working with `this` has changed in ES6?
    - `bind(X)` creates a new fn, same body, but this bound to args X.
    - `=>` bind, or apply NOT WORKING. use parent context.
* Explain how prototypal inheritance works.
* var let and const
    - var: global scope(window) , updated and re-declared, hoisted as undefined
    - let: block scope({}) , updated but NOT re-declared, hoisted not initialized(reference error)
    - const: block scope({}), NOT updated or re-declared, hoisted not initialized(reference error), must be initialized during declaration.
* What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?
    - undeclared variables is a variable that has been declared without ‘var’. undeclared variables are created as global variable
    - undefined means a variable has not been declared, or has been declared but has not yet been assigned a value
    - null is an assignment value that means "no value". null is a value of a variable and is a type of object.
* What is a closure, and how/why would you use one?
    - a closure gives you access to an outer function’s scope from an inner function.
    - A closure is the **combination of a function and the lexical environment** within which that function was declared. let you associate data (the lexical environment) with a function that operates on that data.
```
function makeFunc() {
  var name = 'Mozilla';
  function displayName() {
    alert(name);
  }
  return displayName;
}
// The closure is created when displayName fn is declared. The instance of displayName maintains a reference to its lexical environment, within which the variable name exists. For this reason, when myFunc is invoked, the variable name remains available for use
var myFunc = makeFunc();
myFunc();
```
* What language constructions do you use for iterating over object properties and array items?
* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
    - forEach: NOT return, return get ignored, just iterate over an array.
    - map: returns a new array.
* What's a typical use case for anonymous functions?
* What's the difference between host objects and native objects?
    - object supplied by the host environment (browser or node), window, document
    - native defined by the ECMAScript specification, String, Math.
    - User obj
* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
    - The former is a function declaration while the latter is a function expression. 
    - The key difference is that **function declarations** have its body hoisted but the bodies of function expressions are not
* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two? - apply takes array of args
* Explain `Function.prototype.bind`.
* What's the difference between feature detection, feature inference, and using the UA string?
    - a Cross browser testing, run a test to determine whether a feature is supported in the current browser
    - Modernizr is a great library to handle feature detection. 
    - navigator.userAgent
```
if ("geolocation" in navigator) {
  navigator.geolocation.getCurrentPosition(function(position) {
    // show the location on a map, perhaps using the Google Maps API
  });
} else {
  // Give the user a choice of static maps instead perhaps
}
```
* Explain "hoisting".
    - declaratation: var(let/const) and function. If no var, no hoisting
    - splitting **variable** and **function**  variable declaration and initialization, and moving (just) the declarations to the top of the code
    - var initialized with undefined. let and const are not initialized, if called, reference error
    - `function catName(name) {}`
    - `var num;`

* What's the difference between an "attribute" and a "property"?
    - When writing HTML source code, you can define attributes on your HTML elements. Then, once the browser parses your code, a corresponding DOM node will be created. This node is an object, and therefore it has properties.
    - `<input type="text" value="Name:">` has 2 attributes (type and value).
    - Once the browser parses this code, a HTMLInputElement object will be created, DOM node will have id,type, and value properties.
    - `theInput.value // returns "John"` - current value of the input.
    - `theInput.getAttribute('value') // returns "Name:"` - value attribute contains the initial text-content of the value attribute from the HTML source code.
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
    - js is always single thread. main thread in renderer process.
    - 每一句js 都是 一个task. sync and async tasks. sync 主线程执行. async进入Event Table
    - macrotasks (whole script, setTimeout, UI, I/O) and microtasks(promise) 代码块(不是每句）
    - https://zhuanlan.zhihu.com/p/79371232 例子
    - 例子补充
```
setTimeout(function() {
  console.log('1');
}, 1000)

new Promise(function(resolve) {
  setTimeout(function() {
    console.log('2');
  }, 0)
  resolve()
}).then(function() {
  console.log('3');
})

console.log('4');
// 4 3 2 1   注意不是 1 2
// setTimeout is async tasks, when hit setTimeout, put it into Event Table(Web/OS API 第三方？) to execute, only after it finished(0s vs 1s) in event table, can register callbacks in  macro/micro task queue.
```
![event loop](https://user-images.githubusercontent.com/35388473/138615441-75be0884-0fb9-49c2-810d-234cb20a6860.jpg)
![renderer process](https://user-images.githubusercontent.com/35388473/139111755-cdae6f25-0670-46e8-a50d-47d935ea17ae.jpg)


* What is the difference between call stack and task queue?
    - call stack - keep track of fn calls, When ever we **call** a function for its execution, we are **pushing** it to the stack. It is **popped** out of the stack when the **execution is completed**. This is how Synchronous code is executed in JavaScript.
    - task queue - micro/macro tasks queue
![call stack](https://user-images.githubusercontent.com/35388473/138616385-d70ee388-b977-4e0b-bacc-7c9174d84f5c.gif)

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

* prototypal inheritance  
    - 4 types of Obj property/method:  
1. property defined in Constructor and given to obj instance. `this.x=x`  
2. static properties/methods - defined directly on the constructor. `Math.max() or Object.keys()`  
3. inheritable, defined on Constructor's prototype property. `myConstructor.prototype.x()`  
4. object instance?  
    - update inheritance chain dynamically, `Person.prototype.farewell = function() {}`
    - performing `delete person1.__proto__.farewell` or `delete Person.prototype.farewell` would remove the `farewell()` method from all Person instances.
```
// call 借花献佛 - Teacher 强迫 Person 的 this 指向自己
function Person(first, last, age) {
  this.age=age;
  ...
}
function Teacher(first, last, age, subject) {
  Person.call(this, first, last, age);

  this.subject = subject;
}
// then get Teacher() to inherit the methods defined on Person()'s prototype
Teacher.prototype = Object.create(Person.prototype);
// 所谓继承，指prototypes之间相互继承?
```

* ES6 classes
```
class Teacher extends Person {
  constructor(first, last, age, subject, grade) {
    super(first, last, age);

    // subject and grade are specific to Teacher
    this.subject = subject;
    this.grade = grade;
  }
}
// Teacher 就是constructor, Teacher.prototype === teacher.__proto__
```

* Getters and Setters
```
class Teacher extends Person {
  constructor(first, last, age, gender, interests, subject, grade) {
    super(first, last, age, gender, interests);
    // subject and grade are specific to Teacher
    this._subject = subject;
    this.grade = grade;
  }

  get subject() {
    return this._subject;
  }

  set subject(newSubject) {
    this._subject = newSubject;
  }
}
// use getter method:  snape.subject 
// use setter method:  snape.subject="new value"
```
![prototypes](https://user-images.githubusercontent.com/35388473/138607259-79060cc5-57cb-4973-a29a-d1f453d346c0.jpg)  
当我们访问对象的属性或方法时，浏览器首先会查找对象本身是否拥有这些属性和方法。如果没有，浏览器会去查找对象的原型对象上有没有这些属性和方法。如果还是没有，就查找原型对象的原型对象。这就是所谓的原型链。
注意，如果不写new，这就是一个普通函数，它返回undefined。但是，如果写了new，它就变成了一个构造函数，它绑定的this指向新创建的对象，并默认返回this，也就是说，不需要在最后写return this;。  
https://www.liaoxuefeng.com/wiki/1022910821149312/1023022126220448
