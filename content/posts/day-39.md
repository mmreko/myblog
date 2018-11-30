+++
title = "Day 39: The Wonders of Microservices"
date = 2018-11-30T15:33:42+01:00
draft = false
tags = []
categories = []
+++

Another day at the (home) office, and yet another post on software design. Today I'll go into more detail on a specific pattern (or shall I say THE pattern) - the almighty, the amazing, the fantastic - __microservices__. This topic is far too huge for me to cover in one post, so I'll just try to give an overview of what microservices are, what are their advantages and disadvantages, and what are the different things we need to consider when building and maintaining a microservice application.

Microservices are an _architectural_ pattern, which means that they allow us to model a high-level structure of the entire system. The main idea behind them is to decompose a large, complex system into multiple, loosely coupled services. I find it astounding how popular microservices have become over the last few years. Everywhere you go, in everything you do, microservices are there. I think what contributed to their popularity is the fact that they also go hand-in-hand with many other advancements in software engineering, such as Agile software development, cloud computing, DevOps culture, continuous integration and continuous deployment, and of course containers.

![Microservices](https://www.mememaker.net/api/bucket?path=static/img/memes/full/2018/May/11/19/microservices-127478.png)

__But why are they so good? What are the problems that they solve?__ Here are some I can think of from the top of my head:

* Microservices can defer in terms of __technologies__ that they use. This means that we can choose the best tools for the job every time.
* Microservices can be __scaled independently__, unlike the monolith that has to be scaled all at once.
* Microservices allow for natural __division of work__ among development teams. With that said, they are also a way to scale an organization, not only the application.
* Microservices can also be __deployed independently__, so there is no need to redeploy the entire application every time an update is made. This also means that the deployment time is shorter, and that new functionality is delivered faster.
* Microservices support __reusability__, as they can be used in different ways for different purposes.
* Microservices are __replaceable__, which means that you can replace one implementation with another without breaking the application.

It is easy to get seduced by all of these advantages, but we should always be aware that microservices are not a silver bullet. I'd even say that, in a way, they give us more questions than answers. I didn't fully grasp the severity of this until I tried to implement and deploy a microservice application on my own. It was a rather small application (4 services and 2 databases), but nevertheless large enough for me to understand all complexities that come with managing a distributed system.

First of all, __how do I split my services? How big should they be?__ I like how the book answers these questions: _make your services small enough, but no smaller_. If the service feels too big to you, it most probably isn't small enough. Make the services focused on doing one thing well. Ask the question: _what is my service supposed to do?_ before thinking about the data that it needs.

__How will my services communicate?__ I've heard of different ways to handle this, but a general consensus is that REST established itself as the best choice. __How will the services know where to find other services?__ There needs to be some kind of a service discovery mechanism, right? Again, there are different ways to go about this, but I've found that the good old DNS is by far the simplest one.

Then comes my favorite topic: _data_. In order to ensure loose coupling, a microservice application doesn't have a single data store, but rather multiple smaller databases local to their own specific service. __How do we make this split? What if multiple services need to access the same data? How do we ensure that all data is consistent? What if a transaction that spans multiple services fails mid-way?__ This is far too many questions to answer in this post, so I might just do a separate one on this sometime in the future.

__How do we organize deployment of our services?__ We can either run a single service per host, which allows for easier monitoring (as now we know exactly which service is causing problems), or multiple services per host, which is probably a simpler and cheaper option. From my understanding, what we usually do is a compromise of the two: we package a service inside a container (which gives us a degree of isolation from other services) and then deploy multiple containers on the same host.

__How do we test a complex application such as this one?__ Surely unit tests are not enough. Neither are the per-service tests. We need to make sure that the communication between services is also working seamlessly. These end-to-end tests give us a lot of confidence that the entire system is working, but they are also very slow. The trick is to find the right balance for a specific situation; have enough small tests to provide a quick feedback, but also some large tests to increase the overall confidence in the system. However, at some point, a good monitoring system can even entirely remove the need for end-to-end tests.

__What if things go wrong? How do we deal with failures in a distributed setting?__ What we need to understand is that in a system such as this one failure is inevitable. And as much as we focus on eliminating failure, we should also think of how to degrade gracefully in case one happens in spite all of our efforts. It is better if your application returns degraded results, then if it completely blows up, right? So make sure that you have a mechanism to protect against misbehaving services (timeouts are your friend here!), and whenever something goes wrong, handle it with grace.

As you can see, building a microservice application is by no means a walk in the park. It is complicated, even frustrating at times, but oh-so-rewarding when you finally get it right. I just barely scratched the surface here, so if you wish to know more, I recommend the _Building Microservices_ book by Sam Newman, as well as the [Microservices website](https://microservices.io/) (they are so cool that they even have their own website!).

And of course, never underestimate the power of a hands-on experience. I certainly learned a lot by building my own microservice application. At the very least, now I know that all of their benefits come with a cost - and not a cheap one at that :)