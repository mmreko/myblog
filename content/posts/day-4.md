+++
title = "Day 4: The Requested Operation Requires Elevation"
date = 2018-10-05T14:59:47+02:00
draft = true
tags = []
categories = []
+++

So it's day 4 of my apprenticeship adventure. Came to the office before 8, in the hope of leaving earlier and starting my first weekend as an employed person. Oktoberfest awaits!


But first things first. Had a meeting with my menthor Periklis today to talk about the self-assessment and plan my future steps. In short, there will be lots of reading, talking and probably a bit of frustration, which is innevitable when you try out new things, I guess. So here's what awaits me: My first encounter with functional programming. Visual regression and headless browser testing. Trying out Linux and its tools. Presenting stuff in front of people. I am all for leaving my comfort zone, and nothing really worries me - except the last thing. I already get stressed just thinking about it. Anyways, I'll do my best and we'll see how it goes.



I wanted to start with Scala today, but didn't have my Kindle with me, and the book was in .mobi format. Besides, it's Friday, I thought I could take it easy. So I looked at my backlog and chose what I thought was the easiest: translate my Tic-Tac-Toe app written in Java to JavaScript (so that I can later test it using [BackstopJS](https://garris.github.io/BackstopJS/). Little did I know that this would take almost all of my day and leave me completely and utterly exhausted in the end. All because of JavaScript array methods.



I needed to make a queue data structure for my minimax algorithm implementation. Adding an element at the end of the array posed no problem (just use the `push` method), but I made a mistake by using the `splay` method for removing the first element. Apparently, `splay(-1, 1)` does not return the first element, but an ARRAY containing the first element. And I looked and looked and looked for hours and couldn't find anything wrong with the code. Thankfully, my fellow apprentice Mark came to the rescue. In the end we managed to find an elegant solution to the problem, by using `shift` (for removing the first element) and `unshift` (for adding an element at the end) instead. However, needless to say that I deeply regret choosing to do JavaScript today. But I managed, and that's important.



In other news, I still don't have administrator rights on my laptop. I had the urge to burn my laptop and myself with it about 87 times today. It's funny that you start appreciating the little joys of life (such as being able to install Spotify) only when you lose them. I keep seeing that error message even when I close my eyes: __The requested operation requires elevation__. However, I managed to (partialy) work my way around it. Getting the [Scoop](https://scoop.sh/) package manager allowed me to install Node.js, Git and a couple of other stuff using the Windows Command Line. Still no Spotify though :(

This post marks the end of my first week as an apprentice. All in all, I couldn't be happier. (Actually, I will be, once I get those admin rights.) Next week, new challenges await. First up: learning __Scala__! Stay tuned!