+++
title = "Day 23: The Importance of Docker"
date = 2018-11-06T12:10:03+01:00
draft = false
tags = []
categories = []
+++

I mentioned in my previous post that my Master thesis involved deploying a microservice-based application using Docker and Kubernetes. But believe me when I say that it wasn't the hardest part. As strange as it sounds, what took way more energy and time was convincing people that Docker was a way to go.

For my thesis, I was tasked to completely redesign and reinvent a system that has been active for many years now. This system works as it is now, but only barely. All these years, it was maintained and extended by teams from more than 10 European countries, that each had their own idea of what the system should do and how. What happened as a result is this huge monolithic hell that is in danger of breaking every time an update is made. But nevertheless, if you are careful enough - it works. 

So some people, that have been involved in this project from the very beginning, had trouble understanding why a transition to Docker was necessary. Ok, the system needs to be redesigned and made more maintainable - no one opposed to that. But the deployment with virtual machines worked fine so far, and we are quite familliar with it, so why change? 

You know, I get it. People don't like change, nor do they like challenging their usual way of doing things. Programmers tend not to change stuff that works, but I think that's exactly what the problem is. We should never be afraid to let go of something good in order to get something better. It might take us a while to see the benefits - true - but taking a leap of faith is good for us every once in a while. 

I tried this philosophical approach first, but to no avail. The people I had to convince were highly technical and the only language that would get to them was the one of facts. Besides, I knew that we only dislike what we cannot understand. So I sat down and did my homework; prepared facts, figures and answers to every possible question they might have. That's where I learned that people respond to confidence; I believed in the idea of Docker and used my knowledge and passion to make them believe too. Simple as that.

So what I did first was compare the Docker containers with their beloved virtual machines. I explained how virtual machines come with much more baggage than most applications actually need. Each of them has their own, full-blown guest OS, and thus a hypervisor is needed to distribute computer resouces over different virtual machines. Containers, on the other hand, do not need this hypervisor at all. They run directly on the host machine's kernel, sharing their resources with other containers. Furthermore, containers are incredibly lightweight, as they take up only as many resources as it's actually needed by the app. To put it simply, if you have a piece of hardware, you can fit many more containers on it, than virtual machines. If you feel particularly adventurous, you can even run containers IN virtual machines!

Next, I did a demo to show them how you can deploy your containers anywhere - on your local machine, on the server, on the cloud - it doesn't really matter. The process is still the same. I demonstrated how containers facilitate both development and deployment in production. How they enable easier scaling, testing and bug tracking. And sure, even if Docker is a bit hard to grasp in the beginning, once you get the hang of it - everything goes smoothly. Besides, if I as a student could learn it, then a senior developer surely can too. 

So, to summarize. Docker is cool, use it. And if you have to convince someone of something, convince yourself first. Convince yourself so much, that when people look at you have no choice but to be convinced too.