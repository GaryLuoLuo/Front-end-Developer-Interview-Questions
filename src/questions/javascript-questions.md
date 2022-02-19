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
    - Since a nested function is a closure, this means that **a nested function can "inherit" the arguments and variables of its containing function**. In other words, the inner function contains the scope of the outer function.
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
    - Extending a built-in/native JavaScript object means adding properties/functions to its prototype
    - Dangerous, might collide if two lib both extends.
    - Only do for polyfill (browser compatibility)
* What is the difference between `==` and `===`?
    - `==` is the abstract equality operator while `===` is the strict equality operator.
    - whether do type conversions
    - https://www.mattzeunert.com/2016/01/28/javascript-deep-equal.html
    - [] == [] or [] === [] are false
    - ==/===/ reference equality is always the first, and then compare the value
    - shallow-equals/deep-equal not recursively or recursively check array or obj properties using === 
* Explain the same-origin policy with regards to JavaScript.
    - prevents JavaScript from making requests across domain boundaries
    - CORS header
* Why is it called a Ternary operator, what does the word "Ternary" indicate? - condition ? exprIfTrue : exprIfFalse
* What is strict mode? What are some of the advantages/disadvantages of using it?
    - `"use strict"` 更严格 https://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html
    - prevent accidentally create global variables. 
    - Makes assignments which would otherwise silently fail to throw an exception.
    - this is undefined in the global context.
    - BAD: No more access to arguments.callee
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript? TypeScript
* What tools and techniques do you use debugging JavaScript code? 
    - React/Redux DevTools, Chrome Devtools, console.log
    - **技巧！** https://raygun.com/blog/javascript-debugging/
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript? - String, Number
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code? - list/map: immer/immutable.js, array/object: `[...]`
* Explain the difference between synchronous and asynchronous functions.
    -  In synchronous functions, statements complete before the next statement is run. the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.
    -  Asynchronous functions usually accept a callback as a parameter and execution continue on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread is not blocked (UI freeze)
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
    - for creating new objects
    - syntactic sugar class
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
    - https://dmitripavlutin.com/differences-between-arrow-and-regular-functions/
    - this value inside a regular function is dynamic and depends on the invocation. But this inside the arrow function is bound lexically and equals to this of the outer function.
    - arguments => ...rest
    - => implicitly return
    - => define methods inside class, always bind this to class instance
    - bind call apply no effect on =>, as => always bind to it's lexical scope
```
// define class => this always bind to Hero
class Hero {
  constructor(x) {
    this.x = x;
  }
  logName = () => {
    console.log(this.x);
  }
}
// regular fn => this is dynamic and can be detached from obj as callback
class Hero {
  constructor(x) {
    this.x = x;
  }
  logName() {  //  or logName = function() {
    console.log(this.x);
  }
}
const batman = new Hero('Batman');
setTimeout(batman.logName, 1000) // undefined
```
* What advantage is there for using the arrow syntax for a method in a constructor? - bind this to it's lexical scope
* What is the definition of a higher-order function?
    - A Higher-Order function is a function that receives a function as an argument or returns the function as output. 
    - For example, Array.prototype.map, Array.prototype.filter and Array.prototype.reduce are some of the Higher-Order functions built into the language.
```
// custom HOF, map
function mapForEach(arr, fn) {
  const newArray = [];
  for(let i = 0; i < arr.length; i++) {
    newArray.push(
      fn(arr[i])
    );
  }
  return newArray;
}
```
* Can you give an example for destructuring an object or an array?
* Can you give an example of generating a string with ES6 Template Literals? - note ES6 Tagged templates
* Can you give an example of a curry function and why this syntax offers an advantage? 
    - curried function takes multiple arguments one at a time.
    - https://zhuanlan.zhihu.com/p/80043365
```
// currify 1
function curryIt(fn) {
  // 参数fn函数的参数个数
  var n = fn.length;
  var args = [];
  return function(arg) {
    args.push(arg);
    if (args.length < n) {
      return arguments.callee; // 返回这个函数的引用
    } else {
      return fn.apply(this, args); // 调用函数
    }
  };
}
// currify 2
// https://medium.com/@juliomatcom/an-elegant-and-simple-curry-f-implementation-in-javascript-cf36252cff4c
function curry(f) {
  return function currify() {
    // Since a nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function.
    const args = Array.prototype.slice.call(arguments);
    return args.length >= f.length ?
      f.apply(null, args) :
      currify.bind(null, ...args)
  }
}
// currify 3 - you can import curry from well known libraries like lodash or ramda for both Node and the Browser.
```
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
    - if you want to **copy** values of iterables(Objects/Strings/Arrays), make use of spread.
    -  If you want specific items to be **excluded from the copy**, make use of **destructuring** and the rest operator.
* How can you share code between files?
    - ES5 require/module.exports, ES6 import/export
* Why you might want to create static class members?
    -  Static methods are often utility functions, such as functions to create or clone objects, 
    - static properties are useful for caches, fixed-configuration, or any other data you don't need to be replicated across instances.
```
class ClassWithStaticMethod {
  static staticProperty = 'someValue';
  static staticMethod() {
    return 'static method has been called.';
  }
  static {  
    console.log("Class static initialization block called");
  }
}
```
* What is the difference between `while` and `do-while` loops in JavaScript?
* What is a promise? Where and how would you use promise?
    - 遇到new Promise执行内部的创建函数, (遇到setTimeout，将回调丢到macrotask)，同时将then中的回调函数丢到microtask。在resolve之前，pending promise, 在resolve之后，fulfilled or rejected promise.
* What is callback
    - A callback function is a function passed into another function **as an argument** HOF?, which is then invoked inside the outer function to complete some kind of routine or action.
    - callbacks are often used to continue code execution after an asynchronous operation has completed — these are called asynchronous callbacks. A good example is the callback functions executed inside a .then() block chained onto the end of a promise after that promise fulfills or rejects. This structure is used in many modern web APIs, such as fetch().


## Coding questions
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* What will be returned by each of these?
    - && operator is executed before the || operator
```javascript
console.log("hello" || "world") // 'hello'   hello is true, whole expression must be true, short circuit, return it
console.log("foo" && "bar") // 'bar'  T&&F   foo is false, result must be false, return false. foo is true, see another one
```
* Write an immediately invoked function expression (IIFE) `(function() {})()`

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
