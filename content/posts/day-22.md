+++
title = "Day 22: My Docker Journey (So Far)"
date = 2018-11-05T19:08:50+01:00
draft = false
tags = []
categories = []
+++

This week I am going back to an old friend of mine: the awesome, amazing, irreplaceable - __Docker__.

We go a long way, Docker and I. Met for the very first time two years ago in Bolzano, and went through so much since then. We didn't get off to a great start, though. When the professor introduced it to us, I immediately thought: _What a great idea this is!_ Packaging my application in this so-called _"container"_, together with all its dependencies, and then being able to run that container literally anywhere with no additional setup - almost sounded like science fiction to me. And what is even better, these containers run on the host operating system, unlike those nasty virtual machines, that have their own OS on top of the host one, and provide much more resources than what is needed to run most applications.

But of course, everything that's good comes with a price, which proved to be the case here as well. Docker was too hard to understand and learn, at least on the first glance. For a University project, my team and I had to develop this application and then package and deploy it with Docker. As usual, I was tasked with doing my backend stuff, while another friend of mine did the deployment. Once he was done, he gathered all of us in the dormitory common room and started explaining what he did and how he did it. 

He talked about these ___images___, which are supposedly something like a blueprint for building containers. And then there are different kinds of images. _Base_ ones, that don't have a parent image, and _child_ images, which are built off of them. Next, he introduced ___containers___, which are basically runtime instances of images, or in other words: images with a state. Then he showed some strange files called `Dockerfiles`, that allegedly define how to build an image. He proceeded on to uploading an image on some thing called _DockerHub_, which reminded me a lot of GitHub, but it stored these strange images instead of repositories. As if that wasn't enough, there were also these `docker-compose.yml` files. What on Earth is that and why do we need it? My friend patiently explained that, too. This file shows how the containers should behave in production. _Understood_, I said. _WHAAAAT?_ I thought.

I still remember sitting on that blue sofa and staring half-blankly at the screen. Sometimes I glanced over at the other guys in the room and wandered if I'm managing to look at least a little less confused than them. In the meantime, our Docker expert continued typing those weird Docker commands in the terminal as if it came natural to him; he built images, instantiated containers and played around with them like it was nothing. It almost looked like magic. I watched him in awe, thinking how cool it must be to know all this stuff, and at the same time worrying that I will never be able to do the same.

But here I am, almost two years later, about to defend my Master thesis for which I designed, implemented (in part) and deployed this large microservice-based application using Docker, as well as orchestrated a rather large number of containers with the help of Kubernetes. If someone told me this two years ago, while sitting on that sofa, I would have laughed and said _no way_. But hey, it happened. 

And I still want more. I want to master Docker one day. I want to know all of its secrets. So I will give my best to use this apprenticeship to get at least a step closer to that goal. Docker is such a great invention, that it would be a shame not to use this opportunity to dive into its deepest depths.

I have my oxygen mask ready, so bring it on!