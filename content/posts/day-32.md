+++
title = "Day 32: Checking Out ScalaCheck"
date = 2018-11-20T15:58:30+01:00
draft = false
tags = []
categories = []
+++

Yesterday I learned the basics of _property-based testing_, and created this abstract image in my head about what property-based testing is and how it should be done. Now it's time to give that abstract image a shape, and what better way to do that than trying things out on my own?

For this purpose I chose [ScalaCheck](https://www.scalacheck.org/), which is a property-based testing framework for testing Scala and Java programs. I was very interested to see how powerful a framework like this can get, and also find out if I am able to write some tests for the _katas_ that I solved before. I mostly focused on the various `List` methods that I wrote, and I must say that the whole process has been a lot of fun. I can even say that I've rediscovered my passion for testing, that got kind of neglected in the past couple of years.

Needless to say, it wasn't easy. However, I was prepared for that after the research I did yesterday. The methods I tested were relatively simple, but it still took some time to get used to the approach itself; as I mentioned yesterday, property-based testing forces you to think deeply about the method you're testing - about its inputs, outputs, rules it should satisfy, and so on. You really have to let your imagination flow in order to define the properties - here it's not as straightforward as checking the actual output with the expected one. But I guess that's also where all the fun lies. I've spent hours writing tests today, completely losing track of time. I even managed to break some of my previous solutions and then fix them - and it felt amazing.

When it comes to my experience with ScalaCheck, I'd say it was quite easy to learn, but yet powerful enough to specify basically anything. Here's a small summary on what it could do.

In ScalaCheck, there are three ways how we can create properties to be verified:

* using the `forAll` method (this is how you create so-called _universally quantified properties_ which are the simplest ones)
* combining multiple properties using logical operators (&&, ||, etc.)
* combining multiple properties using the methods of the `Prop` class (`all`, `atLeastOne`, etc.)

Here's a (very generic) example:

``` scala
val p1 = Prop.forAll(generator) { input => condition_it_should_satisfy }
val p2 = Prop.forAll(generator) { input => condition_it_should_satisfy }
val p3 = p1 && p2 // both p1 and p2 should be satisfied
val p4 = Prop.all(p1, p2) // essentially the same as p3
```

The `forAll` method takes a function as a parameter and creates a property out of it. The function can accept almost any type as input, but should return a `Boolean`. 

On the other hand, it is also possible (but not necessary) to supply the `forEach` method with a specific data _generator_. In many cases, the default one will do the job, unless:

* there is a need to control the way data is generated
* there is a need to generate data of types that are not supported by default

You can think of a generator as a function that takes some generation parameters and (maybe) returns a generated value (so in Scala that would be `Gen.Params => Option[T]`). The `Gen` class also offers many methods for creating generators that I found very useful. Here are only some of them:

``` scala
Gen.choose(1, 100) // generates a random integer between 1 and 100
Gen.oneOf(1, 2, 3) // picks one value out of a selection of values
Gen.choose(1, 100) suchThat (_ % 2 == 0) // generates a random EVEN integer between 1 and 100
Gen.containerOf[List, Int](Gen.choose(1, 100)) // generates a list of integers with elements that have the value between 1 and 100
```

There are also other useful features for labeling parts of properties, setting the frequency of different inputs, etc. For details on those (and a lot of nice examples!), make sure to check out the ScalaCheck [User Guide](https://github.com/rickynils/scalacheck/blob/master/doc/UserGuide.md).

The easiest way to run the tests is to place them in the `test\scala` folder, and run them in the sbt terminal with the command `test`. ScalaCheck will then generate 100 random inputs for each of the properties and check if they hold. If they don't, it will explicitly show us the failing test cases, so that we can figure out what's wrong. From my experience, a failing test doesn't always have to mean a bug in the code; especially if you are a novice like me, it can happen quite often that the bug was actually in the test itself. But that's also cool. We learn from every failure and use it to get better next time. It doesn't matter where the failure occured.

Tomorrow, my fellow apprentices and me will attempt at writing our own library for property-based testing. I think that will also be a good way to get more practice with functional programming principles and design. Wish us luck!

