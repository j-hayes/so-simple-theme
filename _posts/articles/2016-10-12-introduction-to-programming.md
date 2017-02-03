---
layout: post
title: Introduction to Programming (Using C#)
excerpt: " Programming is not magic. Programming is just writing structured text, text that a way that a computer can take in as input and then out put a result."
modified: 2017-01-15T23:17:00-05:00
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

Here is how you write out to a screen the words Hello World in the programming language C#.

``` csharp

using System;
public class HelloWorld
{
   public static void Main()
   {
      Console.WriteLine("Hello World!");
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

![alt text](https://cdn.meme.am/instances/500x/72449023.jpg)

Also not real:

![alt text](http://i.imgur.com/MUoxwMu.gif)

^ Wonderful movie worth watching if you have 31 minutes set aside for some ridiculousness:  http://www.imdb.com/title/tt3472226/


 Again, programming is not magic. Programming is just writing structured text, text written in a way that a computer can interpret and then output a result.

My goal with this post are:
- to demystify programming for those not familiar with it
- help you to execute your first program
- set you on your way to learning to write software
- avoid some mistakes I made learning to build apps and websites
- hopefully have a few laughs

----

#### Let's examine the code closer from above

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

The opening brace is the beginning of the class. The closing brace is the end of the class.

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

### String Manipulation

Another concept key to dealing with text is the concept that you can manipulate strings.

In the below example we have a couple of strings and we can combine them together to make a full name.

``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {
      string firstName = "John";
      string lastName = "Hayes";
      string middleName = "Joseph";
      string suffix = "Jr."

      //the first simplest way to combine
      //strings is using "Concatenation" using the plus operator.
      string fullName = "my name is" firstName + " " + middleName + " " + "lastName" + " " + Suffix;

      //the more standard approach is to use string interpolation (actaully a realtively new way thing in C#)
      string fullNameInterpolated  $"my name is {fistName} {middleName} {lastName} {suffix} "


      Console.WriteLine(fullName);
      Console.WriteLine(fullNameInterpolated);
   }
}

/*
This will output:
My name is John Joseph Hayes Jr.
My name is John Joseph Hayes Jr.
*/
```

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
### Math

The last basic thing I have to share is how to do a bit of arithmetic.

What I do here in this next snippet of code is create two integer variables both set to the number one. I then add them together and and the result is as you would expect two.


``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {     
       int one = 1;
       int anotherOne = 1;

       int result = one + anotherOne;

       Console.WriteLine(result);

   }
}

/*
The result printed is
2
*/

```

Here is another one with subtraction

``` csharp
using System;
public class HelloWorld
{
   public static void Main()
   {     
       int one = 1;
       int anotherOne = 1;

       int result = one - anotherOne;

       Console.WriteLine(result);

   }
}

/*
The result printed is
0
*/

```
--------
### Boolean Operations

I will once again lean on a quick google search for the definition of boolean:

- "denoting a system of algebraic notation used to represent logical propositions, especially in computing and electronics."
- "a binary variable, having two possible values called “true” and “false.”"

Boolean operations are about true or false. In plain English an expression like:
- the sun is more massive than the earth
- Chicago is north of Champaign
- the word coat has four letters in it
- the word piano has four or more letters long.

All of the previous statements evaluate to true.

Here is how one might write those in c#. (The objects and variables we will pretend were defined earlier in the program)

``` csharp
using System;
public class BooleanExpressions
{
   public static void Main()
   {     
       /*Creation and definitionn of the objects omitted*/

       /* the greater than operator here is comparing the integer value of Mass on both the sun and earth objects, and the result is assigned to that variable*/

       bool massBoolean = sun.Mass > earth.Mass;

       bool isNorth = chicago.Latitude > champaign.Latitude;

       string coatString = "coat";
       /* the "==" operator checks if the two things around it have the same value.  

       .Length is a property on any string that will give you an integer value of how many characters are in the string.
       */
       bool lengthIsFour = coatString.Length == 4


       bool pianoIsMoreThanOrEqualFourLetters = 4 =< "paino".Length; // yes you can type it this way but you probably shouldn't

       Console.WriteLine(massBoolean);
       Console.WriteLine(isNorth);
       Console.WriteLine(lengthIsFour);
       Console.WriteLine(pianoIsMoreThanOrEqualFourLetters);


   }
}

/*
The result printed is
true
true
true
true
*/

```
One of the many ways to use boolean values is to change what happens in your program based on the state of the data in it. You usually achieve this by use of if statements.

``` csharp
using System;
public class BooleanExpressions
{
   public static void Main()
   {     
       Console.WriteLine("First try at it.");
       ConditionallyPrint(false);
       Console.WriteLine("Second try at it,");
       ConditionallyPrint(true);
   }

   public static void ConditionallyPrint(bool shouldIPrint)
   {
       if(shouldIPrint)
       {
           Console.WriteLine("Ah yeah look at this text.");
       }
       else
       {
           //nothing happens here.
       }
   }
}

/*
The result printed is
First try at it.
Second try at it.
Ah yeah look at this text.

*/
```


There is a lot more that you can do with boolean variables. Please see the further reading section to do a deeper dive. Boolean logic is a cornerstone of understanding programming, but a full discussion is a bit outside of the scope of this post.

--------
### Loops

Another key topic to understand for more complex functionality is a loop. A loop is some piece of code that is run multiple times. There are several kinds:

-while loops
-for loops
-foreach loops

For now we will just while loops. They are the simplest to understand and all we need for now.

A while loop will first check if a condition is met, if the condition is true it will do the loop. When the code is finished it will once again check if the condition holds and run the code again.

- The next example will be interpreted like this.
- Enter the main function
- Enter the while loop
- Check the condition in the parenthesis
- It evaluates to true (because it is just the boolean value true)
- Write Echo to the console
- Reach the end of the loop

- Check the condition in the parenthesis
- It evaluates to true
- Write Echo to the console
- Reach the end of the loop

- Check the condition in the parenthesis
- It evaluates to true
- Write Echo to the console
- Reach the end of the loop

On and on and on.

``` csharp
using System;
public class WhileLoopExample
{
   public static void Main()
   {     
      while(true)
      {
          Console.WriteLine("Echo");
      }
   }
}

/*
The result printed is
Echo
Echo
Echo
Echo
Echo
Echo
Echo
Echo
.... on and on until someone shuts of the program or the computer running it.

*/

```

The opposite example is of course one that the loop is never entered. This code will execute the condition in the while loop evaluates to false and nothing is printed to the console.

``` csharp
using System;
public class WhileLoopExample
{
   public static void Main()
   {     
      while(false)
      {
          Console.WriteLine("It's not a question of where he grips it, It's a simple matter of weight - ratios ... A five-ounce bird could not hold a one pound coconut.");
      }
   }
}

```
Now it's time for one that changes after you go through the loop.

``` csharp
using System;
public class WhileLoopExample
{

   public static void Main()
   {     
      Console.WriteLine("Before the loop");

      bool keepGoing = true;
      string loopString = "loop";

      while(keepGoing)
      {
          Console.WriteLine(loopString);          
          keepGoing = loopString.Length < 10;
          loopString = loopString + "loop";          
      }

      Console.WriteLine("After the loop");
   }
}

/*
The result printed is:

Before the loop
loop
looploop
looplooploop
After the loop

*/

```

--------
### Definitions

There are a lot of terms and concepts in programming but a high degree of understanding of them are not necessary to get started.

But since we have gotten through a bit of the basics, I want to take a step back and talk through a few definitions.

C# is an object oriented language:
A quick google search for the definition of what object oriented gives:
"(of a programming language) using a methodology that enables a system to be modeled as a set of objects that can be controlled and manipulated in a modular manner."

What that definition refers to when it refers to "modular" is something that is broken up into many pieces to make up the greater whole. Objects are those pieces.

That brings us to the term "class." A class is the definition for a particular type of object. Or in reverse an object (in the context of programming) is an instance of a class.

The best definition that I was given while learning programming that has stuck with me is that objects or classes are a unit that contains data and functionality.  

Take the following class as an example:

Side note you really can represent almost anything in a class. I just searched around my apartment quickly to come up with something that could a fun example. The first thing that caught my eye was my microwave. So we will boil some tea in it.)

``` csharp
using System;
public class Microwave
{

    /*
    The following is a constructor it is a special function of a class
    that is run when an instance is being created so that the object can
    be set up.
    */
    public Microwave(int seconds)
    {
        SecondsRemaining = seconds;
    }

    /*
    This is an autoproperty.
    This syntax code to change or get the
    value of the integer of seconds remaining
    */
   public int SecondsRemaining { get;set; }
   public int TeaTemperature { get;set; }

   public bool Cook()
   {   
       if(SecondsRemaining > 0)
       {
            TeaTemperature = TeaTemperature + 1;
            SecondsRemaining = SecondsRemaining - 1;
       }
       else
       {
           Beep();
       }
   }
   public void Beep()
   {
       Console.WriteLine("Your digital tea is ready.");
   }
}
```

Now lets use this class, both its data and its functionality.

``` csharp
using System;
public class MicrowaveExample
{

   public static void Main()
   {     
       Microwave microwave = new Microwave(5);

       while(microwave.Cook())
       {
           Console.WriteLine(microwave.SecondsRemaining);                    
       }
   }
}

// I will let you guess at the output this time : )

```

--------
### Thoughts and suggestions on your adventures in coding.

- One of the best ways to learn how to program is to just say screw it and go build something.

    - It is some much easier to motivate yourself to overcome the mental hurdles involved if you are motivated by the desire to build something. Don't just build anything, build something that you think would be useful, or cool or both. The first thing that I wanted to build was, in my sophomore year of college, a website that allowed students to connect and sell their books to one another as opposed to buying and selling back books to the big companies like amazon or bookstores.
- Find someone to guide you. Don't go it alone. **But.** Ask the right person(s).

    - Back to the story of the college sophomore who wanted to build a website. Well I started researching the tools that I knew about, and at that time it was WordPress and other content management systems. I asked someone I knew to be a well versed computer scientist, a friend of a highschool classmate of mine. His specialty is super computing. So yes he is a likely a great programmer. However, he didn't know the tools that I needed to be using to easily build the thing I wanted to build. Long story short I wasted many months using the wrong tool. Not to say I couldn't have built it using the tools that I was using, but I could have much more easily built it with the tools I used later.
    - I often think back at how laughably off track I was and how simple my goals were back then. I could build a half-assed version of what (not a well written one) I wanted to build in about an hour. Such is life. Save yourself time, find a friend. (It can be me if I know how to help or I will try to send you to someone who might be a better guide.)
- Be prepared for frustration.
    - See above story. You'll fail. But with persistence you will eventually succeed. You won't understand everything right away.
- Before you go ask someone else how to do something just google it.
    - This is my general advice for any type of learning these days. Someone else has likely had the same question as you. If you google your exact question, you will likely end up with an article that has answered your question. Then if you can't find it, go ask a person who might know the answer, not before.
- Find a good IDE (Integrated Development Environment) these are the "microsoft word" of writing software. There are many good options, using one will save you a lot of time and headache in the long run.


--------
### More, More, More!

There are so so so many resources to learn how to code out there. I will mention a few.

- C# stuff
    - Microsoft has really stepped up there game in terms of documentation. They have tons of tutorials and examples out there on the web.
    - Here is a better version, with hands on examplesm of what I set out to do in my post. [Getting Started with C#](https://www.microsoft.com/net/tutorials/csharp/getting-started)
- [Khan Academy](https://www.khanacademy.org/)
    - I haven't used this site before, but I have heard great things about it.
    - It really appears to be a great place to start learning a lot of different things.
- [Stackoverflow](http://www.stackoverflow.com)
    - This website is where you likely end up when you google your questions. It is an entire website of people saying "HALP I DON'T GET IT. ANYONE KNOW HOW DO THING I CAN'T DO?"
- As I write this list, honestly it's not worth even trying. I don't have a good landscape of where to learn programing from scratch these days. See my previous advice, ask someone who does the thing you are trying to do and they (or me) can send you in the right direction.
