---
layout: post
title: "The Basics of Bash"
categories: bash command line shell
---

# An Introduction to the Linux Shell

This post will introduce the basic and most fundamental concepts of the Unix shell.

## What is a shell

The shell is a computer program. It provides an interface in which a user can send commands to an operating system kernel. Since the shell is a user interface it was designed to take commands from the user and execute them.

binaries are executable files that contain "binary code" that is executed directly by an OS kernel.


- single file tree
- inodes: uniquely identify a file
- stdout, stderr, stdin


"Everything is a text file"

The different types of files



The shell is a computer program. It takes in keyboard commands typed by you, the user,
and passes them off to the operating system. *shell* is a general term - it refers to a type
of computer program that provides a user interface for an operating system's services. There are
many different types of specific implementations of shell programs:

  * Bourne Again Shell (`bash`)
  * Z Shell (`zsh`)
  * Bourne Shell (`sh`)

These shell programs all have similar behavior.

- Unix has a single file Trees

This takes you to tour previous working directory:

```sh
$ cd -
```

General speaking most shell commands follow the this format:

```sh
$ <command> -<options> <arguments>
```

There are 8 bits in a byte.

2^8 = 256

With 8 bits you can represent 256 characters.

Carriage return resets a devices position to beginning of a line of text

Read this and add this content to doc: http://guide.bash.academy/01.inception.html

Wildcards allow you to select filenames based on patterns of characters

## Inodes

In terms of how they are represented in memory directories are really stored as files. You do not have files in stored inside of directories in memory. Directories can be thought of as a special kind of file.

A UNIX file is stored in 2 different parts of the disk:

1. the data blocks and
2. the Inodes

The data blocks contain the contents of the file

The inodes contain information *about* the file -> each hard link refers to a specific inode containing a files contents

Har

- stdout
- stdin
- stderr

stream: A stream is information (specifically, bytes) flowing through the links between files, devices and processes in a running system. They can transport any kind of bytes, and the receiving end can only consume their bytes in the order they were sent.
