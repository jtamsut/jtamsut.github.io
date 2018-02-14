---
layout: post
title: "An Intuitive Introduction to Big-O"
categories: javascript modules
---

## What is an Algorithm? What is a Data Structure?

An **algorithm** is a list of instructions to complete some task. An example of an algorithm is a recipe. A **data structure** is a way of organizing data. A family tree is a type of data structure. It organizes the relationships amongst familial relatives in an intuitive and hierarchical way.

## Big-O

**Big-O** is a measure of how long an algorithm takes to run to completion. Let's consider an example.

The following algorithm, `isOneInArray` takes as input an array of integers. It returns `true` if a 1 *IS* in the array and returns `false` if the number 1 is *NOT* in the array. Remember that an integer is a number that can be written without a fractional component, like 4 or 1000.

```js
function isOneInArray(array) {
  for (let index=0; index<array.length; index++) {
    let currentItem = array[index];
    if (currentItem === 1) {
      return true;
    }
  }
  return false;
}
```

Before we proceed any further let's construct a simple model of a CPU or Central Processing Unit. The CPU is what does "logical" computations on our computers. Our model of a CPU will ascribe the following properties to a CPU:

  1. A CPU only does *comparisons* that result in a Boolean (e.g., 1 !== 2 results in true); comparisons include `!==`, `===`, `>`, `<`, etc. Our CPU compares *two* values.
  2. A CPU can only do *ONE* of these comparisons at a time.

Let's consider some sample input for the `isOneInArray` function:

```js
isOneInArray([5,4,3,2,1])
```

What is our CPU doing here?

If we take a look at our implementation of the `isOneInArray` function we can see that the CPU is being "asked" to compare each member in the array above. This is a total of 5 comparisons because there are 5 integers in the array. What the CPU is doing during the execution of the `isOneInArray` function can be written as follows:

```
Is 5 equal to 1? No. Next item in array.
Is 4 equal to 1? No. Next item in array.
Is 3 equal to 1? No. Next item in array.
Is 2 equal to 1? No. Next item in array.
Is 1 equal to 1? Yes. Return true!
```

**This was 5 comparisons**.

It is important to note that the number of comparisons equals the number of elements in the array. If we wanted to generalize we could say that the number of comparisons that our `isOneInArray` function does is equal to N where N is some positive integer that is equal to the length of the input array.

Therefore we say `isOneInArray` is *O(n)*.

If we were to graph the number of comparisons done by our CPU against the length of an input array it would look like this:

![linear](https://docs.google.com/drawings/d/1ERlK5scz4_dbylONq1caIGbSFfZ5AEQMP46alcLozuI/pub?w=850&h=541)

This is a linear line with a slope of 1. For this reason we say that our `isOneInArray` algorithm is O(n) where n is the length of the input array. The only thing affects the number of comparisons our CPU does is the length of the input array.

**One important thing to note is that whenever we are considering big-O we consider the worst possible input on an algorithm**. We can pretend that we have some evil genius adversary that is providing us with the input that would require us the most possible comparisons in our algorithm. A worst-case input for `isOneInArray` would have the 1 at the very end of the array.

We can also write functions that are O(n<sup>2</sup>), O(nlogn) and O(constant). Remember the n<sup>2</sup>, nlogn and constant are all just factors that we can multiply by an input array's length to get the number of comparisons an algorithm has to do.

Let's consider an algorithm with a nested for-loop like this:

```js
function isTwoInArray(nestedArray) {
  for (let index=0; index<nestedArray; index++) {
    for (let k=0; index<nestedArray[index]; k++) {
      if (nestedArray[index][k] === 2) {
        return true;
      }
    }
  }
  return false;
}
```

How many comparisons will the above function make when given the following input:

```js
isTwoInArray([[6,5,4], [3,1,2]])
```

Generally speaking when determining big-O we can use the following expressions:

O(n<sup># of nest for-loops</sup>)

## Conclusion 

This was an informal and not mathematically rigorous introduction to big-O. For a complete and in-depth treatment of this topic I reccomend consulting *Introduction to Algorithms* by Cormen, Leiseron, Rivest and Stein.