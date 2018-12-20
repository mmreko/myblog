+++
title = "Day 51 and 52: The Functional State of Mind"
date = 2018-12-20T14:01:37+01:00
draft = false
tags = []
categories = []
+++

It's Thursday today and my week so far has been filled with Scala, Scala and some more Scala. I had to do some revising as I got a bit rusty with it, but I think that did me good. Namely, some of the gaps that have been bothering me for a while got filled at last.

The thing I've been mostly struggling with when it comes to the whole functional programming paradigm is probably the issue of handling _state_ in a purely functional way. The idea of maintaining state without actually modifying it anywhere sounded nice enough in my head, but understanding how to actually do it in practice was a whole other story. I felt like this was too important, and a mountain I just had to climb before moving on to other challenges, so I took the time this week to do just that.

As I mentioned in some of my previous posts, there is a chapter in the _Functional Programming in Scala_ book that deals with this issue. I think I read it so many times by now that I would be able to recite it to you word for word. The exercises there I did - I think - three times so far. The last time I did them I found them super easy; all of them took me like one hour, which comparing to the first time (when they took 2 days!) was a huge improvement. It's not like I learned them by heart and that's why they were easy. This time I actually understood every single line of code I wrote. But no matter how proud that made me, I still wasn't quite sure I was ready to let go of the exercises and apply what I learned to something practical. Actually, it didn't even have to be practical. Applying it on literally anything - even the stupidest app with state - would have made me so much more confident.

Nevertheless, even though I had a turbulent relationship with the book in question, I liked this chapter way more than others. It actually provided me with a pattern - a tool to use whenever I had to deal with state in any way. And I appreciated that. It doesn't happen so often that you get a concrete answer to a very vague question such as "_How do I handle state in a functional way?_"

So anyways, here's how you do it. Since side effects and modifying state are not really in spirit of functional programing (the fact that you can still do it in Scala makes it so much harder to let go of it), there is a pattern you can use to sort of work around this. The rule sounds simple enough: __Don't modify state as a side effect; rather, return the new state together with the result that was asked for__. Now, the old state remains unchanged, but we still got a new one to use for our next computations.

By virtue this means that each function that updates state is of type `State => (Result, State)`. Conveniently, these functions are also called _state actions_ or _state transitions_, as they are the ones that make us transition from one state to the other. In order to make it easier for us to deal with multiple state actions and combine them, we can define the so-called _combinators_. 

Anyways, since we don't want to pass the state along ourselves (you will agree that it can get pretty tedious to do so manually every time you invoke a state action), there is a way to automate this process. What we can do is define a _state_ type like this:

```scala
type State[S,+A] = S => (A,S)
```

and define our _state actions_ and _combinators_ in terms of this type.

We can even give the state its own class, and wrap its underlying function like this:

```scala
case class State[S,+A](run: S => (A,S))
```

As for the combinators, the book advises us to have at least the following (of course you can still live without those, but at a risk of duplicating code all over the place):

* `def map[B](f: A => B): State[S, B]`, which transforms the result of the state action, without modifying the state itself
* `def map2[B,C](sb: State[S, B])(f: (A, B) => C): State[S, C]`, which combines two state actions and returns a new state action
* `def flatMap[B](f: A => State[S, B]): State[S, B]`, which transforms the result of the state action, for which you possibly also need to pass the state along (this one is also the most powerful, as we can use it to implement the other two)

There are a couple more useful methods that don't naturally go into the class itself, but rather to the companion object:

* `def unit[S, A](a: A): State[S,A]`, which passes the state along without using it
* `def sequence[S, A](fs: List[State[S, A]]): State[S, List[A]]`, which is basically used when you need to do a series of state actions one after the other

In theory, this is all we need in order to apply our state class in basically any case! (When I say "all we need" I make it sound so simple; the truth is, it took me a while to figure out how to actually do it, but more on that below.)

Once that was understood, I decided that the best way to check my knowledge is to try to apply it. To tell you the truth, I was terrified of miserably failing at it. I'm a perfectionist by nature, and as good as that is sometimes, it also introduces pressure that otherwise should not be there. So I stopped for a moment and took a deep breath. For once I decided to allow myself to fail; try out different things, and learn by making mistakes along the way.

With that said, I've spent the past few days trying to come up with different, rather small and not very smart examples of applications with state, and try to implement them using the above pattern. Needless to say there was a lot of failing before I finally got it right; it took a while for things to "click" in my head, but once they did, everything was a smooth sail from there. At first I tried a "reversed" approach: I used the function signatures to "follow the types to an implementation" (as the book would say it), as well as the compiler to sort of give me "hints" on what to do. Then, when I got things working, I tried to figure out why they worked. I put some console outputs here and there, just to see what got called and in which order. I think this approach really helped me understand what was actually going on under the hood. After a while, it became natural to me to handle state in such a way, so I'd say the whole thing was a success, after all.

Now that this mountain is climbed, I have other Scala-related things to look forward to. Most importantly: __Akka-Http__, which I am starting to learn today. After that, I'll see how much more into the depths of Scala I want to go. I did sign up for the [_Programming Reactive Systems_](https://www.edx.org/course/programming-reactive-systems) online course, though. It starts on February 18th, and focuses mostly on Akka, Actors and Akka-Streams. 

Anyways, enough writing for now, coding awaits! :)