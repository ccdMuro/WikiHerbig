---
title: C++ Tutorial
description: Where the journey of C++ programming begins.
published: true
date: 2021-03-07T11:13:57.380Z
tags: 
editor: markdown
dateCreated: 2021-03-07T10:55:09.387Z
---

## Entry Point

A C++ Programm begins with the `main()` funktion. This is the programms entry point, where it all beginns.

The least that one has to write so that the compiler recognizes the source code as valid C++:
```c++
int main () 
{

}
```
When compiled, you get an executable file that does nothing.

But there is still something we can look at. We have a *function definition*. So lets take this one apart.

- The name of the function or the *identifier* is `main`. 
- In fornt of the function name is the *return type* `int`.
- After the function name comes the *parameter list* `()` (in this example it is empty).
- The *function body* is enclosed by curly braces `{ }` (in this example it is empty too).

> The space enclosed by curly braces `{  }` is called **scope**.
{.is-info}
