+++
title = "Day 21: Wrapping Up the Frontend Testing"
date = 2018-11-02T16:11:49+01:00
draft = false
tags = []
categories = []
+++

That moment has finally come.

Everything I did in the past weeks has led me to this. Everything I learned so far has prepared me for this day. As the last step in my _Basics of Frontend Testing_ adventure, today I finally faced __Visual Regression Testing__.

There was no need for fear, though. It was a rather smooth ride through it, in the end. I created a very solid base by first learning about the _headless browsers_ and experimenting with _Puppeteer_, as the _visual regression testing_ relies heavily on these concepts. 

For this blog post, let's dissect this term and learn what it actually stands for.

Firstly, the "regression" part refers to re-running the entire test suite whenever an update is made, to make sure that nothing that previously worked got broken by that update. The "visual" part simply narrows these tests down to frontend tests. Anyone who has ever worked with CSS surely knows how important these tests are, as even a slightest change can create an immense chaos and anarchy on your page, as well as cause a lot (a LOT!) of anger and frustration.

![CSS](https://i.imgur.com/Q3cUg29.gif)

So how does visual regression testing work? The process is actually very simple and straightforward. When a web page (or a component) is created, a screenshot of it is taken and saved as a reference. Then, whenever a change is made, a new screenshot is taken and compared to the reference one. In that way, we can see if our update caused some unexpected CSS problems. This can also be done manually, of course, but why lose precious time when we have awesome tools that can create much higher test coverage and compare screenshots in much greater detail, than a human eye could ever do?

One of these tools is [BackstopJS](https://github.com/garris/BackstopJS), which uses a headless browser (a-ha!) to capture screenshots and run comparissons between them. It also offers a visual feedback that highlights differences after each test run, which really comes in handy when trying to squash those nasty CSS bugs. 

And which is more, BackstopJS is incredibly easy to use. There are only three commands you need to know:

* `backstop init`, to set up a new BackstopJS instance
* `backstop test`, to create a set of test screenshots and compare them with the reference screenshots
* `backstop approve`, to approve the changes made and update the reference screenshots

All tests are stored in a configuration file located in the root of the project. This file is called `backstop.json`, and it has a number of properties, with the most important ones being:

* `id`, which is used for screenshot naming
* `viewports`, which is an array of screen size objects your DOM will be tested against
* `scenarios`, which are your test cases, with the following sub-properties: 
    * `label`, which is also used for screenshot naming (required)
    * `url`, which is an url of the page to test (required)
    * `selectors`, which is an array of selectors to capture
    * and many others that you can find in the official documentation

In short, BackstopJS allows us to use simple [CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) to define what elements to capture, click, hide, remove, etc. For more complex configurations, we can also use scripts to specify what happens before and during each test (that's where Puppeteer comes into play!). All in all, BackstopJS is a very powerful, and yet so simple tool. Maybe it doesn't make all your CSS problems go away, but at least it exposes them in a clear way, so that you can target them more easily.

With that said, I end this week with a full stop on the _Basics of Frontend Testing_. Overall, it's been a rather successful week, with a lot of lessons learned, but now it's time to turn my attention to something different. Starting with Monday, I will be revisiting something I already learned before (and liked a lot!): __Docker__. This revision will then (hopefully) culminate with my first apprenticeship talk next Friday. Everyone that knows me is perfectly aware how scared, messy and nervous I get when I have to speak in front of people.

That's fine, though. I'll be scared, messy and nervous again. 

But I'll show up anyways. 