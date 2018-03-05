---
layout: post
title: "Computer Science Melange"
categories: computer science algorithms
---

This article covers the basics of algorithms and data structures. We define recursion and provide some examples of recursive functions in JS. We then go on to cover the graph data structure and some of its basics algorithms.

## Recursion 

A **recursive function** is one that calls itself. Recursive functions can accomplish much of what iterating can do.

Every recursive function must include these two parts: 

1. **base case** - You need to tell your function when it should no longer call itself or it will continue calling itself forever resulting in an infinite loop!
2. **recursive step** - The step where you call your function 

### Example 1:  Factorial 

The factorial of a number is the product of all numbers up to that number. 

For example, 5! is equal to 5 * 4 * 3 * 2 * 1 = 120

Let's write an algorithm to recursively compute a factorial of some integer.

* **What is the base case?**
* **What is the recursive step?**

Ok, now that we have our recursive step and base case lets write our algorithm: 

<img style="width: 50%;" src="{{ "/images/snippet1a.png" }}" />

If you paste the above algorithm into the Chrome DevTools `Snippets` tab you can visual the **call stack**. The **call stack** is a stack that records function calls. When a function is returned it is popped off the stack. When a function *calls* another function the *called* function is added to the call stack. Each one of our `recursive` calls to factorial places `factorial` onto the stack.

### Example 2: recursiveForEach 

We stated earlier that we could express all iterative functions in a recursive way. Let's write `forEach` recursively. Here is the code below:

<img style="width: 75%;" src="{{ "/images/snippet2b.png" }}" />


We pass `recursiveForEach` an input array, an empty array, a starting index and a callback. It returns to us the result of applying `cb` to each element in `inp`.

What's the base case? What's the recursive step?

## Graphs and Their Algorithms

Graphs are a very useful data structure. They can be used to model social networks, computer network or even roads in a city. This part of the lecture will discuss the fundamentals of graphs.

### What is a Graph 

Graphs are a data structure comprised entirely of only two components:

* Edges
* Nodes or Vertices

<img src="https://docs.google.com/drawings/d/1BX3LCUb9Z-dHS25zc2RKo4nDbMt4S3A85cUYh53r91A/pub?w=527&amp;h=347">

Figure 1. A undirected, unweighted graph.

A graph can either be **directed** or **undirected**. A undirected graph has unordered vertices. This means that one can traverse an undirected graph in any order. Figure 1 is an undirected graph. A directed graph enforces some ordering with respect to traversal. You can only move from the tail to the head of a directed graph edge arrow. For example, in Figure 2 the only way to go from node *a* to node *c* is through nodes b and d. You can think of this as a one-way street.

A graph can also have a *weight* associated with each edge. This weight is typically an integer. It is simply the cost of traveling from one node to the next node.

<img src="https://docs.google.com/drawings/d/1tIer7LchDYoMjXKGDQqSeBjznAXETpRHfnOZrnyxdlc/pub?w=551&amp;h=289">

Figure 2. A weighted, directed, cyclic graph.

A **cycle** is a path on a graph that when followed returns you to where the path began. Figure 2 is a cyclic graph. 

The **distance** between two nodes in a graph is a measure of how close two nodes are to one another. For an unweighted graph the distance is simply how many edges are between two nodes. For a weighted graph, the distance is the sum of edge weights between two nodes. In Figure 2 the distance from node c to node a is 16 and the distance from node *a* to node *d* is 19.

### Representing a Graph with an Adjacency List 

The adjacency representation of a graph and its edges utilizes an array to store edges in a graph. In this representation each node has associated with it, an array of the edges it is connected to. For example an adjacency array representation of the graph in Figure 1 would look like this in pseudocode:

```
node 1 = [node 2, node 4]
node 2 = [node 1, node 3]
node 3 = [node 2, node 4]
node 4 = [node 1, node 4]
```

#### JavaScript Implementation of a Graph 

Below is an undirected, unweighted graph written in JavaScript.

<img style="width: 60%;" src="{{ "/images/snippet3c.png" }}" />

### Breadth-First Search and Greedy Algorithms

The breadth-first search algorithm is a greedy shortest path algorithm. A greedy algorithm is an algorithm that chooses the locally optimal choice at each stage to get the globally optimal solution. This is a general class of algorithms.

### Finding the Shortest Path

The shortest path problem is as follows: given a graph and a starting node, find the shortest path from that node to every other node. 

#### Description of Breadth-First Search

A breadth-first search algorithm is initially provided a starting node. We will call this initial node the **source node**. The central idea behind breadth-first graph traversal is that the algorithm works by first visiting all the nodes that are connected to the source node before it traverses any other nodes. This logic is repeated for the nodes that are connected to the source node and so on, until all nodes are visited.

<img src="https://docs.google.com/drawings/d/1VSgfupN7JEoadaIQEbl17E6oE3Y_1hU_cbCXfKeXiak/pub?w=915&amp;h=596">


Figure 4. Representation of breadth-first graph traversal. The initial graph appears in the top left. The blue nodes represent those that the algorithm has not yet traversed, while the red nodes represent those that the algorithm has already traversed. The breadth-first algorithm traverses the algorithm in layers. Each layer is composed of nodes that are the same distance away from the source node.

To implement breadth-free search you can use a queue. Here is some pseudocode for the breadth-first search algorithm.

```
function breadth-first(graph, source node)
    put the source node onto the queue
    while queue is not empty
        dequeue
        visit that the dequeued node
        put the children of the dequeued node in the queue
```

<a href="https://www.youtube.com/watch?v=bIA8HEEUxZI">This</a> is a great video explaining breadth-first graph traversal. 

## Conclusion 

We just covered *a lot* of ground. The concepts and algorithms we just covered are fundamental ideas in Computer Science. Knowing these concepts can make you a better programming. Many problems can be reduced to problems that can be expressed with a graph algorithm. If you want to learn more about this topic I suggest reading *Introduction to Algorithms* by CLRS or taking [this](https://www.coursera.org/learn/algorithms-part1) course on Coursera.
