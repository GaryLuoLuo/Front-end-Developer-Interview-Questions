---
title: Coding Questions
layout: layouts/page.njk
permalink: /questions/coding-questions/index.html
---

https://medium.com/frontend-development-with-js/answers-of-front-end-job-interview-coding-questions-3c227d59016c

Question: What is the value of `foo`?
```javascript
var foo = 10 + '20';
```
'1020'

Question: What will be the output of the code below?
```javascript
console.log(0.1 + 0.2 == 0.3);
```
0.1+0.2==0.3000000004  
Simple explanation: 1/10 is periodic in binary (0.0 0011 0011 0011...) just like 1/3 is periodic in decimal (0.333...), so 1/10 can't be accurately represented by a floating point number.  
`parseFloat((2.3 + 2.4).toFixed(10))`

Question: How would you make this work?
```javascript
add(2, 5); // 7
add(2)(5); // 7
```
`const add = x => y => x+y; add(2)(5);`

Question: What value is returned from the following statement?
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```
reverse all char  
This is not a robust way to reverse a string, If you need a solution that supports UTF-16, use `[...s].reverse().join("");`

Question: What is the value of `window.foo`?
```javascript
( window.foo || ( window.foo = "bar" ) );
```

Question: What is the outcome of the two alerts below?
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```
for the second alert, 'bar' is not defined.

Question: What is the value of `foo.length`?
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

Question: What is the value of `foo.x`?
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```
foo.x is undefined, as now foo is refering to {n:2}
<img width="687" alt="Screen Shot 2021-10-11 at 8 44 27 PM" src="https://user-images.githubusercontent.com/35388473/136887849-777f48f5-508b-460e-a85f-3d6d15837507.png">


Question: What does the following code print?
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
Promise.resolve().then(function() {
  console.log('three');
})
console.log('four');
```
one four three two  
I think output one and four are pretty clear. setTimeout is a part of Main Task queue while Promise is of Micro task queue that's why "three" and finally "two" is printed.  
setTimeout from OS timer?

Question: What is the difference between these four promises?
```javascript
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```
https://gist.github.com/nolanlawson/940d1a390b2d9cf9483c

Question: What will the code below output to the console and why?
```javascript
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
`window.b=3; var a=3`

Question: Consider the two functions below. Will they both return the same thing? Why or why not?
```javascript
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}
```
Its automatic insert of the semicolon here. The rest of code is never reached.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Stmt_after_return
