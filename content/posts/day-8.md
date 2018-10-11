+++
title = "Day 8: OOP vs FP"
date = 2018-10-11T16:56:41+02:00
draft = false
tags = []
categories = []
+++

Today marks the fourth day of my Scala adventure.



So far, I covered some of the basics: principles of functional programming, data structures and error handling. In addition, I did many exercises and wrote a fair amount of tests. The intruductory tasks were easy and fun, which probably made me more relaxed than I should have been. That was a mistake! Never EVER relax when doing Scala! It's a trap!



As I progressed through the book, the amount of information conveyed grew exponentially, and so did the difficulty of exercises. I found that when it comes to solving problems in Scala, no matter how complicated, if you sit down and really look hard at them - they become even more complicated. Most times when I got the solution right, I did it in the first try, second at most. Whenever I spent a significant amount of time thinking deeply about the problem, I got even more confused. 



Nevertheless, I learned a lot over the past couple of days. I may still be a novice, but on the other hand - now I know enough to start asking questions. The one that particularly bothered me today is the following: which approach is better - functional or object-oriented?



So I did what I always do when in doubt: extensive Google research. Of course I wasn't the first one to ask this question. There are thousands and thousands of articles and blog posts debating on this topic, and even more heated arguments on online forums. However, most of them agree in one thing: __it depends__. Even though I get annoyed by such vague answers, it was kind of what I expected. Such as pretty much everything in software development, there is no silver bullet that can magically solve all your problems. 



But then, what does it depend on? I found many answers online, which turned out to be not quite helpful. For example, [this](http://blog.fogus.me/2013/07/22/fp-vs-oo-from-the-trenches/) painfully subjective one:



> Use OOP if you don't know what you're doing, FP if you do.



Or, [this](https://medium.com/@sho.miyata.1/the-object-oriented-programming-vs-functional-programming-debate-in-a-beginner-friendly-nutshell-24fb6f8625cc) incredibly long and unnecessary complicated one:



> Team OOP argues that the concept of inheritance (new objects taking on the attributes/methods of existing objects letting us reuse more code) and encapsulation (the data and methods related to a certain object being bound together, creating independent, protected entities) makes it easier to manage and manipulate data. Team FP argues that the separation of data and methods, as well as the high level of abstraction leave less room for errors.



Finally, I came accross a great explanation by Michael Fogus, in his blog post [_FP vs OO, from the trenches_](http://blog.fogus.me/2013/07/22/fp-vs-oo-from-the-trenches/). He states the following:



> Whenever I write some code to deal with data __about__ people then functional programming seems to work best.



> Whenever I write some code to __simulate__ people then object-oriented programming seems to work best.



So simple, yet so on point. I will definitelly refer to this explanation in the future.



To sum up, it seems that FP and OOP are basically two sides of the same coin. I would say that a good software engineer should know the concepts of both, as well as understand when to use which. With that said, I am wrapping up this post and moving on to the next chapter in the Scala book. 

Wish me luck! :)