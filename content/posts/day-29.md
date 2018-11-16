+++
title = "Day 29: Untying Threads"
date = 2018-11-15T16:15:52+01:00
draft = false
tags = []
categories = []
+++

Yesterday I ventured onto the topic of parallelism in Scala, and to tell you the truth - the journey hasn't been as enjoyable as I expected it to be. I started reading about this in the _Functional Programming in Scala_ book, and I just ended up as confused as it gets. So I gave up half way through it, frustrated with both the book and myself. Honestly, I'm not sure if the book is way more abstract than it should be, or I am just not ready for it yet.

However, yesterday I also made a very important resolution, which was to not rely on the books as much, and try to do some more practical stuff on my own. So for today's blog post I will take a different approach than usual: I will try things out and write about them as I go. 

When I first started learning about Scala and its _purity_ (meaning: avoiding the side effects), I thought how great this language must be for concurrency. As data structures are basically immutable, you can operate on them without having to worry that the structure will be changed by other threads - because it won't. But, are things really that simple?

I am someone who has mainly been a Java developer so far, so one question instantly came to mind: if Scala is run on a JVM, why don't we just use Java's `Thread` and `Runnable` classes and be done with it? Well, if that was the case, this post would be incredibly short. I did some research and, of course, you _can_ use these classes in Scala too. I also tried them out and they work absolutely the same as in Java. However, the issue is the fact that `Runnable`'s method `run` does not return a result, so if we _do_ need it, this method will simply not suffice.

``` scala
val myThread = new Thread(new Runnable {
    override def run(): Unit = ...
})
myThread.start()
```

What are the alternatives, then? Firstly, Java also offers classes called `Executors` and `ExecutorService`, which can be quite helpful. `Executors` class offers static methods for configuring the `ExecutorService`, which allows us to do _thread pooling_. What a _thread pool_ basically does is maintain a fixed number of threads that wait for tasks to be allocated to them (see picture below). This means that there is no need for constantly creating and destroying threads. We can simply reuse them.

![Thread Pool](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0c/Thread_pool.svg/600px-Thread_pool.svg.png)

The `ExecutorService` can also execute `Runnable` tasks using its `execute` method. However, it also offers a `submit` method, that accepts a parameter of type `Callable`, which can actually return a result. This method wraps the result in a `Future` object, which is basically a placeholder for a value that might not exist yet. If we want to extract that value, we can call the `get` method on the `Future` object, which will block the current thread until the result becomes available. There is one problem with this approach, though. As the thread pool is of fixed size, we need to be very careful; otherwise we'll run out of threads and get stuck in a deadlock.

``` scala
import java.util.concurrent.{Callable, Executors, Future}

val pool = Executors.newFixedThreadPool(10)
pool.execute(new Runnable { // without result
    override def run(): Unit = ...
})
val result : Future[T] = pool.submit(new Callable[T] { // with result
    override def call(): T = ...
})
result.get()
pool.shutdown()
```

On the other hand, Scala also offers its own `Future` class, that works in a similar way. All we have to do is the following:

``` scala
import scala.concurrent.ExecutionContext.Implicits.global
import scala.concurrent.Future

val future = Future { // this is just calling the Future's apply method
    val result = doSomething()
    result
}
future.forEach(result => println(result))
```

And finally, the last approach to parallelism that I discovered is the one called __Akka__. Akka is a a free and open-source toolkit and runtime that simplifies the construction of concurrent and distributed applications on the JVM by using the concept of `Actors`. An `Actor` is essentially a concurrent process that doesn't constantly occupy a thread. Rather, it does so only when it receives a _message_. Multiple threads can send messages to the `Actor` simultaneously, but it processes them only one at a time. This means that there is no danger of deadlocks - we will certainly never run out of threads. Additionally, as each `Actor` can modify only its own internal state, the data will never be corrupted. So all we have to do is create a task and send it to the `Actor` - Akka will figure out the rest.

``` scala
import akka.actor.{Actor, ActorSystem, Props}

object Worker { // companion object of the actor class
    case object Message // add case classes for each type of message the actor receives
    def props() : Props = Props(new Worker()) // configuration parameters for the actor
}

class Worker extends Actor {
	import Worker._
	
	override def receive(): Unit = { // method to handle different types of messages
		case Message => ...
	}
}

val system = ActorSystem("systemName") // actor factory
val worker = system.actorOf(Worker.props(), "actorName") // create actor

worker ! Worker.Message // send message to the actor
```

On another note, what if our threads have to access/modify the same data? As in Java, we can deal with this issue in several ways:

* using __synchronized methods/blocks__ (i.e. _mutexes_), that allow only the thread that holds the mutex to access the data
* using __volatile annotations__, that are more or less identical to the above, but also allow null values
* using the `AtomicReference` class, which is basically a low-level concurrency primitive

When I was done with the basics (and felt confident enough in my understanding of them), I went back to the dreaded _Purely Functional Parallelism_ chapter in my book. The thing is, the book doesn't really explain any of those basics. It just assumes that I know them all, and dives straight into the low level stuff, which is how to design a library for fully functional parallelism. After seeing what Scala already has to offer off the shelf, I had trouble understanding why would I ever write a library like this from scratch. Sure enough I can't do it any better! However, I gave the book the benefit if the doubt, and went with the flow either way.

On the second read, things seemed a bit clearer. I wouldn't say I understood everything, nor that I feel ready to write such low level functions on my own, but perhaps I don't need to know that just yet. At least now I know how to approach tasks like this, and eventually in the `Future` I will be able to actually do them on my own. But for now, I'm happy with what the standard libraries have to offer :)