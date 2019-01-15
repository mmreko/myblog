+++
title = "Day 55-62: Code(Freezing) in Finland"
date = 2019-01-15T12:25:28+01:00
draft = false
tags = []
categories = []
+++

As promised, here's an overview of some of the highlights that I took away from this CodeFreeze.

## Microservices with The Help of DDD

This was the first session I attended, and one that I was particularly excited about, given my huge love for microservices. There was a lot of discussion about how to slice microservices, so that they properly reflect their domain. This, of course, is a very hard task to perform, so any input on it may be incredibly useful. I did learn a bit about __Domain Driven Design__, understood what a Domain is, what a Bounded Context is, etc. But overall, I feel like I fell short. In this one hour session, a lot of questions were asked and very few answers given. I appreciated a real-life example that was provided to us, though. I just wish I got more out of it, that's all. But hey, now I can add another item to my backlog :)

## Consumer Driven Contracts

This was one of the few well-structured, well-prepared presentations that actually had slides, and a code demo to go along with it. I think it's after this session that I realized that I'm more of a type for conferences than _unconferences_, after all. But anyways. The talk was about designing APIs from the consumer's point of view, instead the producer's. The basic idea is that the consumer defines a contract where he states his expectations of the provider. The provider must then fulfill every point stated in the contract, and perform tests to check whether they did it well. The main benefit is that the producer now knows how each consumer will be affected by any given change, but can also make changes that will not affect any consumer. I thought it was a nice idea, but I guess not applicable in every situation.

## TCR

__Test-Commit-Revert__ is an alternative approach to TDD, also a creation of Kent Beck. The rules are the following:

1. Write a test.
2. Write code in an attempt to make the test pass.
3. If the test passes, commit.
4. If the test fails, revert.

![TDD vs TCR](https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F52531331%2F204415613557%2F1%2Foriginal.jpg?auto=compress&s=d2d1a179405c27b7ca3eedf89188fe4a)

The session itself was organized in the form of Mob Programming, with two people driving the code and the rest giving advice. After each round, the drivers would change. The kata we did was FizzBuzz, which was more than familiar to all of us, so it wasn't particularly exciting. Only one revert was done, and that was on purpose.

All in all, I personally didn't like the whole TCR approach. I understand the motivation behind it - to force you to do small steps and think more about the code you write. But I found so many commits unnecessary. And reverting everything if you make a mistake seems a bit too radical to me. Besides, I like my red tests. They drive your coding in a sense that the error message literally tells you what to fix. So in conclusion, I'll stick to my classical TDD.

## Architectural Katas

Ah, these ones I found particularly fun! Basically the idea is to practice designing architecture of a system in a similar way you practice coding through _katas_. The kata is performed in iterations with the following phases: _Design & Discuss -> Pitch -> Reflect & Break_. It can be done in as many iterations as you wish, sometimes even lasting a whole day. The architecture is usually documented using a __C4 model__, which is a very nice and concise way to discuss architecture within a team.

![Arch Kata](https://mashareko.tk/archikata.jpg)

The materials are all available online, so if you're interested, check [here](https://archkatas.herokuapp.com/rules.html) and [here](http://nealford.com/katas/index.html).

## The internet as a workplace for people with invisible disabilities

A bit less technical, but still a very important subject that a Software Crafter should definitely care about. The discussion revolved around people with disabilities that work as freelancers, and don't have anyone to ensure that their rights are protected and their needs met. Also, we talked about how invisible disabilities do not recieve the same attention in a workplace as, for example, physically or sensory disabilities - and what we can do about it.

## The Dark Side of Software Craftsmanship

Everything has its dark side, even beautiful ideas such as Software Craftsmanship. I am happy that we barely managed to avoid the subject of terminology here; I find it completely unnecessary for people to feel offended by the term "craftsMANship". After all, it has nothing to do with gender roles, but the mankind itself. So I see no problem there.

We talked a bit about "fixing" the Software Craftsmanship manifesto, so that it can better reflect our beliefs. For example, does the thing that we build matter just as much as _how_ we build it? Should a Software Crafter build software that is _evil_? And what does _evil_ mean? Then we discussed the term "professionalism" and what it means for us. Is that the right term for what we are advocating?

Overall, a very interesting talk. It was quite insightful to hear all the diverse opinions on these topics.

## Apprenticeship Program Scheme

Aaaand the best for last! My fellow apprentices and I also held a session on the apprenticeship, explaining how it's done in HolidayCheck and giving more details about our personal journeys so far. It triggered some interesting discussions afterwards, as well. I was happy to see that people were curious about what we do, and what we represent for the Software Craftsmanship community. It made me incredibly proud, and I truly felt like I did my fair share out there, when it comes to contributing to this CodeFreeze. After all, this was my first (un)conference talk! And I survived!

## Final Thoughts

After coming back from the CodeFreeze, I was a bit disappointed with the actual "conference" part of it, given its lack of structure and organization (see my yesterday's post). But now when I put some of my learnings on paper, I see that I took away from it much more than I previously thought. It definitely gave me a nice base for certain topics, and sparked my wish to learn more about them in the future. Which is also a great thing!

Now, I'm off to do my usual apprentice stuff yet again. It feels nice being back in the office after so long. The Business Phase is still going on, so this week I'm visiting my first development team - __team Take-off__! But more on that in my next post :) 
