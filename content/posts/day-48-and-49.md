+++
title = "Day 48 and 49: The Force Is Strong With TDD"
date = 2018-12-14T14:20:41+01:00
draft = false
tags = []
categories = []
+++

Even though I've been spending this week over at the UX & Design team, trying to blend in there as much as possible, attend their meetings and watch what they do - I tried my best not to let that interfere with my study plans. I've been doing a lot of reading recently, and as rewarding as it can be, I honestly missed doing other stuff. My shoulder has been giving me trouble for weeks, but in these past few days I finally felt well enough to use both of my hands again (at least for a couple of hours every day) and do some coding at last.

There's been a lot of talk around the office about the online challenge called [Advent of Code](https://adventofcode.com/), where you get a new (very "christmassy"!) coding challenge to solve every day. During the morning _katas_, we would usually read the daily challenge and sketch out a "pen and paper" solution, but since our time was rather limited, we wouldn't get to do much coding afterwards. However, I missed coding _so so so badly_. It's been a while since I was able to do it without asking people to pair with me. Not that it wasn't fun, but as weird as it sounds, I missed the feeling of typing on the keyboard _myself_, and seeing the magic unfold on the other side. Therefore I used most of my time in between the UX & Design meetings to try and finish the challenges. No Scala this time, though. I felt like I needed a less stressful comeback to coding, so good old JavaScript came to the rescue.

Now, a funny thing happened on Day 1. Yes, I found myself starting with a test. Didn't even think about it; it just came to me naturally. _Well, that's new!_ I thought to myself. The feeling was rather weird, but _oh-so-good_ at the same time. I guess I can say I felt like I was doing things _right_ this time. Now I see where _katas_ have brought me. Repetition IS the mother of learning, after all. That _Red, Green, Refactor_ cycle got so hardcoded in my brain, that I started repeating it unconciously, like a reflex.

Then on Day 2 I decided to do a small experiment: do the challenge _without_ TDD. I had my experience from the day before that I wished to compare with my old way of doing things, which was jumping straight into coding. Did I still find that approach easier and faster? I was really curious to find out the answer.

I was very inspired that day, so I threw ideas all over the place and my code grow so fast, that it was hard to keep track of it. Eventually, I finished the challenge - or at least I thought I did. Everything seamed right, and I was pretty sure that it would work.

Alas, of course it didn't. 

Something somewhere broke and my hopes turned to dust. But what broke, and where? I had to write a test to find out. It was a tiring and frustrating process, but in the end the tests helped and my code worked. I paused for a second to think. So I had to write all of these tests anyways. Why didn't I write them first, then? Contrary to what I thought before, it would have saved me so much time. And I wouldn't get so stressed in the process. Yes, TDD would have been a way better choice!

![TDD](https://memegenerator.net/img/instances/76284045.jpg)

I suddenly felt my love for TDD grow exponentially, so I dug through my numerous files and found the book _TDD By Example_ by Kent Beck. I thought it would be nice to get a few tips from _the man_ himself (Kent Beck was the one who invented TDD!). The book was a nice and quick read; the author didn't try to suffocate his readers with boring theory, but rather walk us through an example, and offer some practical tips in the end. So here comes the summary of what I learned.

The biggest struggle I had relating to TDD was having to _think small_. Sometimes, when the problem was simple, I found it a waste of time to do teeny tiny steps, when I could have just done one huge leap and get to where I wanted to be. So I felt really constrained; I guess that's the only thing that kind of put me off TDD. However, the book tore down this notion, or rather: it refrased it in a way that was perfectly acceptable to me. Namely, you _don't have to_ do small steps. Large leaps are perfectly fine, if you feel confident enough that you'll be able to land safely. TDD does not require the steps to be small, nor big. In fact, you should be able to do both - and alternate between them if necessary - depending on the circumstances. Nevertheless, the more you do TDD, the smaller your steps will get. There's no need to force it - it will come to you naturally.  

So, in summary, here's how you can go about the problem at hand:

* __Obvious Implementation__ (_the leap of faith_) - If the solution seems too obvious to you, go ahead and implement it.
* __Fake It 'Til You Make It__ (_normal steps_) - Return a constant to make the test pass. Then, gradually transform the constant into an expression using variables. 
* __Triangulate__ (_baby steps_) - Only abstract when you have two or more examples. There's also this golden rule: 

> "Once Is Chance, Twice is Coincidence, Third Time Is A Pattern."

Furthermore, here are some more tips from the book that I found useful:

* __Isolate your tests from each other.__ The execution of one test should NOT affect another test in any way. (Note: I actually made this mistake yesterday, and spent two hours thinking why my code was wrong. It wasn't - but one test accidentally changed the global state which made the other tests fail.)
* __Keep track of what you want to test.__ Before starting, write a list of things you want to test - sort of like a TO-DO list. (Note: We have been practicing this at the _katas_ this week, and it has proven to be quite helpful.)
* __Use test data that is easy to read and follow.__ Your tests are also your documentation. Think about the people that will be reading your code in the future. Or at least, think about your future self that will be equally as confused when some time passes.

To conclude, I wanted to answer that everlasting question: _Why do TDD?_ I thought the book was pretty good at explaining it, so I'll just borrow the author's words: _TDD is a way of managing fear during development_. This fear is a completely normal thing to feel when faced with a hard problem, whose solution is not in plain sight. TDD helps you regain control. It keeps you focused on one single step that you need to take next, and gives you a sense of accomplishment with each passed test. What is there not to like?

So have a nice weekend, everybody! And remember: _Red, Green, Refactor_ :)