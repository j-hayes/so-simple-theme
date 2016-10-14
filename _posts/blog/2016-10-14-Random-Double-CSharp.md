---
layout: post
title: "Random Double in C#"
modified:
categories: blog
excerpt:
tags: [learning]
image:
  feature:
date: 2016-10-14T11:30:55-04:00
modified: 2016-10-14T11:30:55-04:00
---

C#'s random number generator calculates doubles only from 0.0 to 1.0. Found a handy extension method at: 
http://stackoverflow.com/questions/1064901/random-number-between-2-double-numbers

to get a random double bounded by a min and max. (I could have come up with it myself, but googling was always going to be quicker than doing the math myself. :P

//extension
public double GetRandomNumber(this Random random, double minimum, double maximum)
{
    return random.NextDouble() * (maximum - minimum) + minimum;
}

//without just a method.
public double GetRandomNumber(double minimum, double maximum)
{ 
    Random random = new Random();
    return random.NextDouble() * (maximum - minimum) + minimum;
}
