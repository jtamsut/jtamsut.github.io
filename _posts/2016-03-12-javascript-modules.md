---
layout: post
title: "JavaScript Modules"
categories: javascript modules
---

This article discusses the module design pattern. The module design pattern is a common design pattern
that is available in many programming languages. This article will discuss modules as they pertain to JavaScript.

A <b>module</b> is a chunk of code that is "wrapped up" and made "available" to other code through some <b>interface</b>. An interface is essentially a boundary with which two parts of a software system communicate. A module interface defines the way a module will interact with other parts of your code, and therefore, can also be thought of as a specification for how that module will be used. Modules allow you to encapsulate some data and functionality within a given lexical scope and return that scope and data to be consumed as a "public API".

>A Brief Aside: Closures<br><br>
To understand the basics of JavaScript modules you first must understand JavaScript <b>closures</b>. A [closure](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch5.md) is a construct in JavaScript that arises when a function maintains private access to its lexical scope even when that function is being evaluated outside its originally defined scope. Here is an example of a closure:

```js
function dog() {
   var bark = true;

   function cat() {
      if (bark) {
         console.log('I am a dog, not a cat! Bark!');
      } else {
         console.log('I am a cat! Meow!')
      }
   }

   return cat;
};

var pet = dog();

pet(); //-> I am a dog, not a cat! Bark!
```
>We say that the `cat` function has *closure* over the `dog` function, because even though the `cat` function is being executed outside the scope of the `dog` function it still has access to the `dog` function's scope (i.e., the value of `bark`).

Now that we understand closures allow me to provide you with a simple example of the module pattern in action:

```js
function myModule() {

  var randomVariable = "yes!";
  var anotherRandomVariable = {a: 10, b: 11, c: 12};

  function blah() {
    console.log(randomVariable);
  }

  function something() {
    console.log(JSON.stringify(anotherRandomVariable));
  }

  return {
    blah: blah,
    something: something
  }

};

var bar = myModule();

bar.blah(); //-> yes!
bar.something(); //-> {"a":10,"b":11,"c":12}
```

The pattern above is often referred to as the *Revealing Pattern* module pattern. It is characterized by the fact that the outer function (in this case the `myModule` function) needs to be invoked in order to return an object which can be thought of as the *public API* other code can consume in order to gain access to the contents of the `myModule` module.

### Why are Modules Useful?

Now that we have an appreciation for the module pattern let's discuss why modules are useful. Modules allow you to:

* <b>Reuse code</b>: Code that will be used multiple times throughout your application can be wrapped up in a module. If would like to change the internal logic of that module you only have do it once and that change is propagated throughout your entire application.

* <b>Prevent namespace pollution</b>: In a large project too many global variables (i.e., namespace pollution) can be disastrous. Two variables inadvertently given the same name can result in unexpected behavior and difficult to debug code. By wrapping code up in a local scope and providing it to the rest of your code as a public API (i.e., by using modules) you reduce the likelihood that you mistakenly given two variables the same name.  

* <b>For logical abstraction</b>: Modules allow you to break code up into parts and abstract away the details of how such code was implemented and just focus on the interface of a module. This allows you to use a module and only worry about its inputs and outputs and not its functionality.

* <b>To decouple code</b>: Coupling refers to how much JavaScript modules rely on other JavaScript modules. Loose coupling refers to the fact that each piece of code can be tested without using the other the other modules. Loosely coupled code is easier to debug.

### CommonJS

We will now discuss one specific instantiation of the module pattern: CommonJS. You should know that other instantiations exist like AMD and ES2015's native module feature.

With CommonJS the variables each module is making public are explicit. The two main features of the CommonJS module system are:

1. the `require()` function allows you to *import* a module into the current scope
2. the `module` object which allows you *export* code from the given scope


If we have two files: `hello.js` and `world.js` defined in the same directory:

```js
// hello.js

var hello = "hello";
module.exports  = hello;
```

and

```js
// world.js

var hello = require("./hello");

console.log(hello + " world!");
```

The output of `world.js` will be the string "hello world!". The `hello` variable is the result of an interface allowing `world.js`
to access the contents of the `hello.js` module.

### References

[1] http://semver.org/ <br>
[2] [*Using Objects to Organize Your Code*](http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code)<br>
[3] [This](https://webpack.github.io/docs/commonjs.html) succinct discussion of the CommonJS module pattern in the webpack documentation.<br>
[4] http://yuiblog.com/blog/2007/06/12/module-pattern/<br>
[5] [You Don't Know JS: Closures and Scope, Ch. 5](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch5.md#modules)
