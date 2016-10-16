---
layout: post
title: Fundamentals of the Ruby Programming Language: Objects and Classes
categories: ruby objects classes
---

In this post we explore some core features of the Ruby programming language: objects and classes. Ruby is, after all, an object-orientated programming language. Every value in Ruby is an object. Programming in Ruby involved creating objects and classes that are then able to do things. This ability is granted by the methods these objects have access to. Creating an object in Ruby is simple:

```ruby
1  obj = Object.new
2
3  def obj.greet(name)
4  	"Hello #{name}"
5  end
```

Here we are introducing a number of constructs of the Ruby programming language:
	* on line 1 we are creating a new object using the `new` keyword
	* on line 3 we are creating a method on the `obj` object
	* on line 4 we are using string interpolation and the fact that Ruby implicitly returns that last line of a method to return the 

Every expression in Ruby evaluates to an object and all objects have 


> Sidebar: Difference between puts, p and print


In Ruby an object is created
