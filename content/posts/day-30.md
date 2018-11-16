+++
title = "Day 30: Dealing With The Friday Mood"
date = 2018-11-16T14:23:05+01:00
draft = false
tags = []
categories = []
+++

I woke up this morning feeling tired and drowsy, as if I haven't slept at all last night. The cold and foggy weather didn't help my cause, either. Anyways, I sleep-walked my way to the office, drank two coffees, and finally sat down at my desk to do some work. As the day passed by at the speed of a wounded snail, I glanced around the office a couple of times, noticing that I'm probably not the only one feeling this way. I guess it's just a Friday thing, after all.

I have my own tricks for dealing with days like this, though. I realized a long time ago that when I'm in the Friday mood, every attempt at being productive in complex, brain-power-consuming tasks would spectacularly go up in flames. So in these situations I try to keep my daily tasks short and sweet. They usually involve tying up the loose ends that remained from the current week, so that I can start fresh on Monday, without any unfinished work weighing me back. 

The first thing I did was go back to the parallelism in Scala and play around a bit with __Akka__. I realized I've made some mistakes in yesterday's post, so I went back to fix them. Honestly, now I really like this whole idea of actors; it's so simple, but yet so effective. Make sure to have a look at it if you haven't already.

Next it occured to me that so far I've never really used arrays in Scala. Neither of the books I've read had any special mention of them, so I thought there's not much to it, after all. But I decided to do a quick Google search regardless - better safe than sorry, right? Anyways, it turned out that Scala arrays are fully compatible with Java ones, with three main differences:

* Scala `Arrays` can be generic
* Scala `Arrays` are compatible with Scala `Sequences` 
* Scala `Arrays` also support all `Sequence` operations, such as `map`, `filter`, etc.

Also, Scala arrays are immutable in the sense that their size cannot change, but their values, of course, can. Kind of what I expected. However, as this is not in spirit with the functional way of programming, arrays are not used that often in Scala. Their alternative, `Vectors` - which can be indexed but not changed - are used much, much more often.

Anyways, the only thing I found weird when it comes to arrays (and something I will probably never get used to) is the fact that you access their elements using parenthesis, and not braces (so it's `array(index)`, not `array[index]`). Such a strange syntax choice, is it not?

After lunch, I did a small research on the ways to handle _state_ in purely functional programs. I'm guessing that this topic can go on and on and on, and that today I barely scratched its surface. Needless to say, I will definitely need more time to go a bit deeper, before writing a full blog post about it. In any case, I'm happy with my overall progress so far.

Finally, the only thing that I didn't do today was plan my next week, figure out what categories I want to explore more, think of some practical tasks to do, etc. I glanced over to the clock and realized that it's almost 5pm, and that the weekend is impatiently waiting for its turn. So I caved in and  decided to leave the important scheduling decisions for Monday when I'm feeling more like a proper productive member of society. Besides, there is only one choice you absolutely have to make on a Friday, and that is bottle or glass :)

So cheers to the weekend! Make it a good one!