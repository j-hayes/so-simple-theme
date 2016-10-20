---
layout: post
title: "Writing Testable Code"
categories: daily
excerpt: "First thing’s KIll All The Managers."
tags:
  - daily
  - software development
  - unit testing
image:
  feature:
date: 2016-10-19T20:07:17-06:00
modified: 2016-10-19T20:07:17-06:00
---

### TL;DR:
Don't name **anything** a manager. Have your classes should have a single responsibility. Name your class and interface after that single responsibility. Don't fear long, but specific names.  Have your functions in that class do one thing. Test those isolated pieces of functionality.

 Identify your "responsibility" before you write your interface. Then write the interface so that you could test it's responsibility. Then write the tests. Then write the code. Then fix the tests because it probably didn't quite work or test all the cases. Then fix the code for the edge case you forgot. Repeat until satisfied and acceptance criteria are met.

--------

One of the most frequent topics that comes up at my job is "Man I wish we were writing more unit tests." This is not to say that we don't test or that we wish to achieve 100% code coverage. I too am guilty of skipping over unit testing because it can feel like a nuisance. However, on my current project we have made unit testing a priority. I have gotten the time to go out and focus as much time as I think is prudent on testing the classes that I am writing.

I went looking for a good guide to writing solid testable code and wouldn't you know it, it only took one google search and hitting the first link to find a great article. [Guide: Writing Testable Code](http://misko.hevery.com/code-reviewers-guide/)

### My Takeaways

The part that most resonated with me was:

["Flaw 4 Class Does Too Much"] (http://misko.hevery.com/code-reviewers-guide/flaw-class-does-too-much/)

Warning Signs:
- Summing up what the class does includes the word “and”
- Class would be challenging for new team members to read and quickly “get it”
- Class has fields that are only used in some methods
- Class has static methods that only operate on parameters

It is extremely difficult to write a test around something that does more than one thing. Step one to over coming flaw 4 is to have methods that do just one thing. If you can at least get your methods to the point where they are doing just one thing, you can write tests for those methods. Regardless of the level of complexity of the rest of the class, at least you can test the functions—iso  long as they are not dependent on state of the class. The next step is to get your class slimmed down to where the class can be said to have a single responsibility. This should be the goal anyway with classes and functions.

The solid principles are a guide to writing good objected oriented code and should be the baseline goal of any OO software development, in terms of quality and style.

 #### [Solid Principles](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)

S	- Single responsibility principle

O	- Open/closed principle
“software entities … should be open for extension, but closed
for modification.”

L	- Liskov substitution principle

“objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.” See also design by contract.

I	- Interface segregation principle
“many client-specific interfaces are better than one general-purpose interface.”

D	- Dependency inversion principle
one should “Depend upon Abstractions. Do not depend upon concretions.”

#### In terms of testing, here is why you should care:
S - So that your tests can be simple. Test each individual type of functionality independently (Or don't test things that you don't need to test or don't have tme for)

O - Not exactly applicable here to what I am talking about here

L - If you test the base class you don't have to test that functionality in a derived class.

I - A class should have a few specific methods for doing one thing. Re: Don't have giant dumping ground manager classes.

D - You class should not be responsible for creating it's dependencies, that way they can be mocked. There by your tests can isolate just the "Unit under test." This is only possible if you are working against a dependencies interface and not the underlying implementation. See Dependency injection and Inversion of control to help with this.


The next one that drives me insane is when I see classes and functions that are lazily named. I know no better way to tell if a class is doing more than it should than if it is called Xmanager or Xservice (For some better naming conventions see [stackoverflow](http://stackoverflow.com/questions/1866794/naming-classes-how-to-avoid-calling-everything-a-whatevermanager)).

My favorite quote from the article was: "First thing’s KIll All The Managers." It is so true. I die a little inside every time I see something named a manager. I've done it, we all have. However, it's my new crusade to end this on projects that I am on. Instead of having a thing manager, have a thing thing repository, a thing reader, a thing writer, thing queuer, thing aggregator, thing to other thing converter. Don't have a thing manager. If you find yourself writing a really long class name, don't be too afraid as long as it is specific. If the word "and" get's involved you are probably doing more than one thing and it is time to break it up.

#### Important:
To make all of this easier on yourself it is important hat you identify your "responsibility" before you write your interface.

Once that is done you can then write the interface so that you could test it's responsibility.

  Then do one of the following in any order:
  - Then write the tests.
  - Then write the code.

  I don't get dogmatic about Test Driven Development. I think it helps you write testable code if you have to write your tests first. But if you want to write the code first that's fine too.

  But at the end of the day. WRITE THE TESTS. You will thank yourself in the long run because of all of the regression issues you catch and all of the edge cases (or even the happy path being wrong) the QA testers didn't have to catch.  

  The last paragraph of the article was also something that was right on the money and I will let it speak for itself.

 "**CAVEAT: LIVING WITH THE FLAW**

  Some legacy classes are “beyond the scope of this one CL.” It may be unreasonable for a reviewer to demand a large, pre-existing problem be fixed in order to make a small change. But it is reasonable to draw a line in the sand and request that the author take steps in the right direction instead of making a bad situation worse. For example, sprout a new class instead of adding another responsibility to an existing, hard to test, object.

That's what I learned today. I still am a novice unit tester. But I know where I want to be. I want unit testing to be second nature."

src = "http://misko.hevery.com/code-reviewers-guide/"
