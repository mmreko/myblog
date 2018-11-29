+++
title = "Day 37 and 38: Brushing up on Software Design"
date = 2018-11-29T14:04:21+01:00
draft = false
tags = []
categories = []
+++

As typing with my left hand proved to be a challenging and tiring endeavor, I've spent some time yesterday trying to think of a possible workaround. Finally, it occurred to me to use one of the [speech recognition tools](https://dictation.io/speech) and dictate my post instead of typing it. Oh, the wonders of modern technology! I was saved. Thankfully today I also did home office for the first time; I can only imagine how crazy I look sitting here and talking to my laptop as if it was a psychiatrist.

I've spent the last two days reading the _Building Microservices_ book and thoroughly enjoying it. I'd say it's very well-written and understandable even for those without any experience in microservices. In my case, it confirmed some of the things I've already known, explained a couple I found confusing,  and opened up some new horizons for me to explore.  

But before diving more deeply into microservices, I thought it would be a good idea to write a post about __software design__ in general. I've studied quite a bit about software design at the University, as that was one of the areas of software engineering that I am the most passionate about. While I was working as a student assistant, I got to dig through many designs submitted by students for different problems, and give them tips based on what I saw. True, they were all simple problems comparing to the real industry ones, but it made me happy to share my knowledge no matter how small in the grand scheme of things.

With that said, designing software is no easy task. It bears with itself this great responsibility of defining a high-level structure of your system that will (hopefully) satisfy the goals of your stakeholders. If done wrong, the consequences can be disastrous. 

![Software Design](https://i.pinimg.com/originals/0e/0b/1f/0e0b1f8c2b36404e4740b6f733097f19.jpg)

Thankfully there are also some _guidelines_ that can steer you in the right direction. We call those guidelines __design principles__. Some of them are:

* __KISS__ (Keep it simple, stupid) - Make simplicity your key design goal and avoid unnecessary complexity at all costs. 
* __DRY__ (Don't repeat yourself) - Avoid repetition of code, data, etc. When something needs to be changed, it would be best if we had to change it only in one place.
* __YAGNI__ (You aren't gonna need it) - Add functionality only when it is necessary, or to quote XP co-founder Ron Jeffries: 

> "Always implement things when you actually need them, never when you just foresee that you need them."

* __SOLID__
    * __Single Responsibility__ - A module should only have a single responsibility with regards to functionality; this also means that a module should only have one reason to change.
    * __Open/Closed__ - Modules should be open for _extension_, but closed for _modification_.
    * __Liskov Substitution__ - An interface implementation can be replaced by another implementation of the same interface without breaking the application.
    * __Interface Segregation__ - General-purpose interfaces shall be split into several client-specific interfaces, so that clients only have to know about those methods that are of interest to them.
    * __Dependency Inversion__ - High-level modules, which provide some logic, should be unaffected by changes in low-level modules, which provide utility features; instead both of them should depend on some higher abstraction.

* And many, many more...

Let's say these guidelines are enough to get you started. Then after some time you'll notice that some design problems occur very frequently. So why reinvent the wheel and solve them every time from scratch? Notice the patterns! Use them! Patterns are beautiful. They make our lives so much easier. In software design, there are two kinds of patterns:

* __Architecture patterns__, that define the structure of the system at the highest level
* __Design  patterns__, that solve a more specific problem within a high-level architecture

Each of these patterns comes with the name, intent, problem, solution, structure, and its own advantages and disadvantages. And of course, there are so many of them, that it's impossible to know them all! Thankfully, there are many pattern catalogs out there (some of them even online, such as [this one](https://refactoring.guru/design-patterns/catalog)) and beautifully written books on the topic. I personally first learned about them from the book _Software Architecture for Dummies_ by Robert Hanmer. Needless to say that I wholeheartedly recommend it.

Patterns may be cool and all, but they are still not always straightforward to use. For instance, maybe you'll find them quite a bit abstract at first. But that's okay. Patterns are abstract so that they can be adapted to any specific situation. However, the more you use them, the more obvious they become. Be careful not to overuse them though! A system that is too generic is also not very readable, nor understandable. Find the right balance and everything will be alright.

Oh wow.  I haven't realized how much this post has grown while I was speaking. Maybe the topic is to blame; you can go on and on and on about software design, and no amount of blog posts will ever be enough to cover it all. With that said, this would probably be a good place to stop for today; I still need to wrap up the microservices book, so that I can dedicate my post to it tomorrow. 

__P.S.__ If I haven't said so already, I LOVE speech recognition :)


