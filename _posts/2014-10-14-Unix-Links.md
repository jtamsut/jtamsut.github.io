---
layout: post
title: "Unix Links"
categories: unix links
---

The Unix link is a useful mechanism that allows one to create a reference from one file or directory to another file or directory. This article will explore the two types of Unix links - hard links and symbolic links - and how they can be useful.



# A Primer on Unix Links

## Soft v Hard

Sometimes it may be useful to refer to a

# What is a symbolic link

A symbolic link is a link that points to another file and does not contain the data in the target file

It points to another entry somewhere in the file system

Symlinks can link to directories

To create a symlink in Unix enter:

```sh
$ ln -s source_file myfile
```

## What is a hard link?

Hard links can only refer to files. They cannot refer to directories.

```sh
$ ln oldfile newlink
```

## Use Case: Synchronizing Two GitHub Repositories

Suppose you were tasked with building an application that had two large parts, say a complex and dynamic UI and an API that interacted with this UI. If these two parts needed to be developed in synchrony meaning that they need to be tested against each other but also need to be in seperate GitHub repos, a symlink might be useful. You see, you can symlink the UI in the API or vice versa. That way the two projects do not need to be in the same directory and can still communicate with eachother.


// TODO: Come up with better example.

Sources:

[1] http://unix.stackexchange.com/questions/20670/why-do-hard-links-exist
[2] `$ man ln`
[3] https://kb.iu.edu/d/abbe
