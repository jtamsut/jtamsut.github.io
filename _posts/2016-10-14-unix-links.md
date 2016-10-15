---
layout: post
title: "Unix Links"
categories: unix links
---

This article will briefly explore the Unix link utility. A Unix link is a useful mechanism that allows one to create a reference from one file or directory to another file or directory. There are two types of Unix links - *hard links* and *symbolic links*.

### What are Symbolic Links? What are Hard Links?

A symbolic link is simply a reference to another file. They allow you to reference a file or directory with different names. Let's say you have a file named `file1.js` with the following contents:

```javascript
console.log('Hello world!')
```

Now let's imaging that you have another directory name `foo` in the same directory as `file1.js` so the directory structure now looks like this:

```
|- file1.js
|- foo
```
Imagine that you would like to have another file named `file2.js` located in `foo` that always had the same exact contents as `file1.js`. This can be done with a *hard link* or a *soft link*. Inside the `foo` directory you can type this:

```sh
$ ln ./../file1.js file2.js
```
or this:

```sh
$ ln -s ./../file1.js file2.js
```
into the command line. In both cases if `file2.js` is executed it will result in the same output as `file1.js`. In this case if `file2.js` is executed with Node we get:

```
$ node file2.js //=> Hello world!
```

So in the example above we used the `ln` command to create a link. In general, a link is created by typing in the command

```
$ ln <-s> <source> <link>
```

To create a hard link exclude the `-s` flag in your command. Hard links have two main limitations:

* They can only reference files, **NOT** directories.
* They cannot reference files outside its own filesystem. This means that a hard link can only reference files on its same disk partition.

Both hard and soft links create files that reference a "source file" that is practically indistinguishable from the "source" file.

