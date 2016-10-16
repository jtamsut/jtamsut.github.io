---
layout: post
title: "Core Ruby: Classes and Objects"
categories: ruby objects classes
---

In this post we explore some core features of the Ruby programming language: objects and classes. Ruby is, after all, an object-orientated programming language. Every value in Ruby is an object. Programming in Ruby involves creating objects and classes that are able to do *things*. This ability to *do things* is granted by the methods these objects have access to.

Creating an object in Ruby is simple:

```ruby
1  obj = Object.new
2
3  def obj.greet(name)
4  	"Hello #{name}"
5  end
```

In the above code snippet, we are introducing a number of Ruby constructs:

  * on line 1 we are creating a new object using the `new` keyword
  * on line 3 we are creating a method on the `obj` object
  * on line 4 we are using string interpolation and the fact that Ruby implicitly returns that last line of a method to return the

Every expression in Ruby evaluates to an object. Here we can borrow a term from the JavaScript community:
*truthy*. All objects in Ruby are truthy. A truthy value is a non-Boolean value that evaluates
to a Boolean. All objects in Ruby evaluate to true, except the `false` object and `nil`.

Every object in Ruby has a unique id associated with it:

```ruby
string1 = "foo"
string.object_id #=> 70122274571720
```

TODO: Finish this article with plenty of examples, precision and understanding

> Sidebar: Difference between puts, p and print


In Ruby an object is created
