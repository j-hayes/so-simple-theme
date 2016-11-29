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
This is a function called Main.  Let's start with a definition of functions:

A function is a named section of a program that performs a specific task which may or may not return a value. 

In our example this function performs the specific task of printing "Hello World" to the console. The "Main" function is typically the function that is the function that is called when a program is started, or its "entry point". (For all practical purposes for this post Main is **Always** the "Entry Point".)

Let's break down what we are seeing syntactically. 

"public" in this context means that any other module can call this function. This is the opposite of "private", which means you can only call this function from within the same scope as the program. (This will be covered in more detail later.) The syntax is intentionally intuitive; private is more restrictive on what modules can use it than public.  

"static" don't worry about it for now, we will cover it later. 

void:  
Functions can call into other functions and have them perform their procedures and return values. "void" means the function is not returning anything.  In our example this function is the entirety of the program, but obviously in most programs there will be many functions. What we mean by "returning something" is that a caller function will not get back when calling a function. We would replace this void with the keyword "string" if we were going to return some text from our function. 

``` csharp
public static string GetMyName()
{
    return "Jackson";
}
```

Again, Main() says this a function named main. The open and close parenthesis means that there are not "Arguments" being passed into the function. Imagine that you wanted to specify what would get output to the console. That function would look like this 
``` csharp
public static void ConsoleWriter(string textToOutput)
{
    Console.WriteLine(textToOutput);
}
```
"string textToOutput" would be some text passed in by the calling function. That text would be written to the console. (not the word textToOutput.) You could pass in anything you like, such as: Jackson, why are you writing this blog post? Literally thousands of people have done this, does the internet really need another intro to programming blog post? Answer no.  

Let's look at the next level(s) up. 

``` csharp
using System;
public class HelloWorld
{

}
```

"public class HelloWorld" is defining and naming a class. For now just think of a class as a collection of things. All you know about at the moment are functions and strings, but there are other things it might contain. Again this class is marked as public just like our Main function. The meaning is the same here. This class can be used by other modules (in more precise language it will be other classes). 
  
The opening brace is the begining of the class. The closing brace is the end of the class. 

Here is an example of a slightly more complicated class:


``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {
      PrintHello();
      PrintJackson();
      ConsoleWriter("Coding is not magic.");
   }
   
   public static void PrintHello()
   {
     Console.WriteLine("Hello, World!");
   }
   public static void PrintJackson()
   {
     Console.WriteLine("Jackson");
   }
   private static void ConsoleWriter(string textToOutput)
   {
       Console.WriteLine(textToOutput);
   }
}

This will output:
Hello, World!
Jackson
Coding is not magic

```

As you can see there are multiple functions defined and being used by the Main function. 

The line "using System;" means that this class is referencing the System namespace. (A namespace is a way of organizing and naming groups of code.) The reason we want to do that is because the class "Console" is in the "System" namespace. Without that using statement, our HelloWorld class would not have access to the Console class. (Actually the program would not be able to run, because the program would not compile correctly, i.e. the computer would not be able to interpret the code into something it can run.) 


--------
### Variables

Now let's introduce another concept that was not used in our previous example, a variable. Just like in math, a variable is a thing that could have different values. 


``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {
      string myName = "Jackson Hayes"; 
      string myRealName = "John Joseph Hayes Jr."; 
      Console.WriteLine(myName);
      Console.WriteLine(myRealName);
   }
}

This will output:
Jackson Hayes
John Joseph Hayes Jr.
```

What we did here in our main function was define a new variable of type string (again string is text) and assigned it the value "Jackson Hayes." Then we created another string variable and set its value to "John Joseph Hayes Jr." Then of course as before we write those values to the console. 

### Basic types 

As you might be able to imagine, text is not the only thing available to you in programming. It would be a bit of a pain in the ass to do everything with text. 

Here are some basic types available to you (not an exhaustive list) 

(also a note for the below code if you see // this is a comment, comments are ignored by the computer, they are there only for developers when writing code.) 

``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {     
        bool isMale = false;	 //This is a boolean value i.e. true or false.        
        char oneCharacter = 'a';	//System.Char one character, not a whole string. Notice that we use single quotes and not double quotes.
        string oneCharacterInAString = "a"; //this is a string. 
        int aNumber = 100; // this is an integer value of 100. int as you can imagine cannot handle decimals it is only for whole numbers. 
        decimal aDecimal = 1000320.30230;	//this is a decimal value (Always use decimal when you are dealing with money values. )
        double aDouble = 103020.392392d;	// A double can hold a larger numbers or numbers with more decimal places. 
        
        ///Then later do something with these variables
   }
}
```

--------
### Math and String Manipulation 

--------
### Definitions

--------
### Functions Continued 

--------
### Objects and Classes Continued 

--------
### Write your first web page

--------
### More, More, More!
