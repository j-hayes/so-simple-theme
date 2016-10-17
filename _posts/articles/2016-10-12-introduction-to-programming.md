---
layout: post
title: Introduction to Programming (Using C#)
excerpt: " Programming is not magic. Programming is just writing structured text, text that a way that a computer can take in as input and then out put a result."
modified: 2016-06-01T14:17:25-04:00
categories: articles
tags:
- programming
- c#
- 101
- Introduction

image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

## TL;DR

Programming is not magic. You can understand it and you can do it. It can be taught. You don't have to be a nerd or a geek and most certainly not a genius. I do it every day and I am only one of those. (Hint it's not genius.)

Here is how you write out to a screen the words Hello, World in the programming language C#.

``` csharp

using System;
public class HelloWorld
{
   public static void Main()
   {
      Console.WriteLine("Hello, World!");
   }
}

```

If you would like to run this yourself go to
https://www.tutorialspoint.com/compile_csharp_online.php

-  Click File
  -  Save Files
- Click the Compile button
- Click Execute button

In the Terminal area the following should appear:

```
sh-4.3$ mcs *.cs -out:main.exe                       
sh-4.3$ mono main.exe                            
Hello, World!
```

With this code read I now welcome you to the world of programming. This code is a time honored tradition. It is the first thing almost ever programmer is taught to do.

There are a lot more interesting and exciting things to learn. But hey, this is a start.


----------

## Introduction

#### Programming is not magic, as pop culture tends to paint it as.

Or to put it another way:

![alt text](https://cdn.meme.am/instances/500x/72449023.jp
g)

Also not real:

![alt text](http://i.imgur.com/MUoxwMu.gif)

^ Wonderful movie worth watching if you have 31 minutes set aside for some ridiculousness:  http://www.imdb.com/title/tt3472226/


 Again, programming is not magic. Programming is just writing structured text, text that a way that a computer can take in as input and then out put a result.

In simpler language, it takes your code and it does stuff with it. That stuff is math, binary math, but it is abstracted away from you the programmer to the point where it can do a multitude of different complex things for you.

My goal with this post are:
- to demystify programming for those not familiar with it.
- help you to execute your first program,
- set you on your way to learning to write software,
- avoid some mistakes I made learning to build apps and websites
- hopefully have a few laughs.

----

#### Let's examine the code closer

``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {
      Console.WriteLine("Hello, World!");
   }
}

```
We will move outward. Starting with:

``` csharp
    Console.WriteLine("Hello, World!");
```

This line is what does the work. It is the instruction that the computer is interpreting to do the work.

"Console" is an class (a word I imagine you are not familiar with in this context, bear with me for a second, I will have a set of definitions once we get into it). Console comes in the "System" library that is part of C# which allows you the programmer to interact with a console.

Yeah, it's that thing you associate with programmers:

![alt text](http://media.tumblr.com/tumblr_m1wjechWv01qekfnu.png)

"WriteLine" is a function that writes a line of text to the console.

The semi-colon ";" at end of the line is what terminates the statement. It says: "hey computer, do the thing." It is important because it also distinguishes the statement from other statements, so you can do more than one thing.


``` csharp
Console.WriteLine("Hello, World!");
Console.WriteLine("Hello, Jackson!");
```
In plain English:

- "Computer write to the console the text Hello, World.
- "Computer write to the console the text Hello, Jackson.

The quotation marks around the words the text ( ->"Hello, World!"<-) denote that the text between them is of the data type string. A string is the data type that is text.

Now for the next level up:

``` csharp
public static void Main()
{

}
```

--------
### Definitions

--------
### Math

--------
### Functions

--------
### Objects

--------
### Write your first web page

--------
### More, More, More!
