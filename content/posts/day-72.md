+++
title = "Day 72: Exploring Type Classes"
date = 2019-01-25T15:48:14+01:00
draft = false
tags = []
categories = []
+++

As I announced yesterday, today's post will also be a bit more tech-centric. I felt like I needed to summarize what I learned in a concise way, so that I can check how much from it I actually understood; after all, if you can't explain it, then you don't know it - am I right?

While spending a week in User Flow, I realized I was still missing knowledge about some terms that are apparently used quite frequently in the world of Scala. So yesterday and today I dived a bit more into the FP principles, catching up with a bit of theory that I guess I should have covered earlier. But anyways, it is never to late, I suppose.

So my topic of the day was __Type classes__. I heard a lot of people mentioning _Monoids_ and _Monads_ and so on, but I never quite understood what they were. At first I thought that was some complex, high-level, impossible-to-understand-at-this-point stuff, but it turned out that I was totally wrong, at least when it comes to the basic idea behind them. A quick Google search revealed to me that type classes were basically something I already knew; I just never gave it a proper name (or any name, for that matter). Here is a nice explanation by Miran Lipovača, from his book _Learn You a Haskell for Great Good_:

> “A type class is an interface that defines some behavior. More specifically, a type class specifies a bunch of functions, and when we decide to make a type an instance of a type class, we define what those functions mean for that type.”

So esentially it's a way to add behavior to data types without inheritance, especially useful when you can't (or don't want to) modify their original source code. Certainly, it is not something strictly limited to the functional way; you can use it just as effectively in object-oriented programs (which I probably have, I just didn't know it).

Nevertheless, a type class consists of three components:

* __The type class__, which is a trait with at least one generic parameter
* __Instances of the type class__, for those data types that we want to extend
* __Interface methods__, which expose the new API

I tried to follow the explanation from [here](https://alvinalexander.com/scala/fp-book/type-classes-101-introduction) and create a small code example, so that it would be easier to understand what was going on behind all the theory.

I started with the following classes:

``` scala
sealed trait Vehicle
final case class Car() extends Vehicle
final case class Bicycle() extends Vehicle
final case class Plane() extends Vehicle
```

I wanted to provide a flying functionality to the plane, but not to the car nor bicycle (even though that would be quite cool, obviously). For that I created a trait with a generic parameter, that would allow me to apply the `fly` method on whatever type I want.

``` scala
trait IsAbleToFly[A] {
  def fly(a: A): Unit
}
```

Then, for each of the data types I wanted to extend (in this case only `Plane`), I created an instance of the type class and implemented the `fly` method. The `implicit` keyword here indicates that the object can be used implicitly.

``` scala
object IsAbleToFlyInstances {
  implicit val planeIsAbleToFly = new IsAbleToFly[Plane] {
    override def fly(a: Plane): Unit = println("I am flying!")
  }
}
```

The final step is to expose the new API. The `implicit` keyword before the class means that the class’s primary constructor is available for implicit conversions.

``` scala
object IsAbleToFlySyntax {
  implicit class IsAbleToFlyOps[A](value: A) {
    def fly(implicit isAbleToFlyInstance: IsAbleToFly[A]): Unit = {
      isAbleToFlyInstance.fly(value)
    }
  }
}
```

Now, if we want to make the plane fly, we can do it in the following way:

``` scala
import IsAbleToFlyInstances.planeIsAbleToFly
import IsAbleToFlySyntax.IsAbleToFlyOps

val plane = new Plane()
plane.fly
```

Awesome! The plane got a new functionality, and I never had to modify its original code. That's a pretty useful feature to have, if you ask me.

After understanding the basic idea behind type classes, it was much easier to grasp terms such as _Monoids_ and _Monads_. They are basically the most frequently used type classes, and the __Cats__ library provides all of them for use in Scala programs. Here are some that I explored a bit more today:

* __Semigroup__, which has an associative binary operation (combine)
* __Monoid__, which is a Semigroup with an additional empty value (which is an identity for the combine operation)
* __Functor__, which has a mapping operation
* __Applicative__, which is something between a Functor and a Monad; they allow sequencing of functorial operations (unlike Functors), but these operations must be independent and not affect each other (unlike Monads)
* __Monad__, which can combine operations that are not independent (one operation can influence the next one, and so on)

I followed all this without many problems up until the _Applicative_, where things got much more complicated. I am not sure yet if I got the essence of it right, but let's say that's it for the time being. I'll definitely go back to fix this post if it turns out I got it wrong.

## Short Reflection On This Week

Before wrapping up the post, I wanted to do a short retrospective/reflection on my week at the User Flow team. All in all, it was a very Scala-heavy week (like I anticipated), but I didn't mind that at all (which I didn't anticipate). Not sure I completely changed my mind when it comes to Scala, but I guess I needed to see how it's actually used in practice in order to truly appreciate it. The week in User Flow definitely helped with that, and to be honest, now I think it might be fun to join them and learn more about Scala from the masters themselves. But on the other hand, I love love love JavaScript and want to do more of it. As you can see, I feel pretty confused with what I want at the moment, but I'll give it more thought in the next few weeks - thankfully there's still two months left for me to finally make up my mind.

Anyways, thank you __User Flow__ for an amazing week, and happy weekend to you all!