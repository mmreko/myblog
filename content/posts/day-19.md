+++
title = "Day 19: Going Headless"
date = 2018-10-30T16:16:53+01:00
draft = false
tags = []
categories = []
+++

Even though the many meetings I had to attend today kind of messed up my schedule, I still managed to get some useful work done. Usually, if I don't start doing anything productive before 11, there is a high chance that the situation will remain that way for the rest of the day. Thankfully, I didn't let that happen. 



As I had less time than usual, I kind of re-adjusted my schedule and postponed my _visual regression testing_ adventure for tomorrow, leaving more room to explore and understand the technical concepts of _headless browsers_ and _headless browser testing_ (headless browsers are actually used to power visual regression testing tools, so this was a good introduction). I guess it would be quite helpful to know what I'm doing before actually doing it, right?



As the matter of fact, there weren't many resources online that explain these concepts, so I took the liberty to make a small summary of everything I learned today and formulate it as a blog post. Will try to keep it short and simple, though. Who knows, maybe somebody finds it useful.



The first time I heard of a term _"headless browser testing"_, I found it quite weird. I kept imagining a guy without a head, sitting at his computer and writing tests. Of course, it's nothing like that. Thankfully, it's not the developer going _headless_, but the browser.



What does this mean, though? Simply put, a __headless browser__ is a browser without a graphical user interface. It can do everything a normal browser can do, such as render web pages, except actually showing them on your screen. _What good comes from it then?_ you might ask. Well, a headless browser can be used for a bunch of things, such as automating UI tests, taking screenshots of web pages, or simply scraping web sites for data. These are all things that you can also do with a normal browser, but with a much larger efficiency loss that comes with starting up a GUI. Actually, when it comes to executing tasks like these, a headless browser is 2 to 15 times faster!



![Headless Browser Illustration](https://cdn-images-1.medium.com/max/1600/1*9TPFZA7Xmh9tXTWAig24ZA.png)



Of course, headless browsers have their limitations (with the obvious one being the inability to actually view the webpages), but as with any tool, they have their own area of use. Remember: it's all about choosing the right tool for the job. So don't use headless browsers for browsing the web or even debugging (I guess it's hard to find a mistake on a page that you cannot see). 



And finally, how do you perform __headless browser testing__? As you probably figured out by now, you run your tests through a headless browser, without using the GUI. These tests are usually written in the form of scripts, and are used to check for bugs on a page, validate its layout, and so on. However, remember that this is not a way to perform UX testing! For this you need to see the actual interaction of a user with the website, and for something like that you most probably need a browser with a head :)



In case you want to play around with headless browsers, I recommend [Headless Chrome](https://developers.google.com/web/updates/2017/04/headless-chrome). It comes with a couple of built-in command line features (for taking screenshots, creating pdfs of pages, etc.), however I had some trouble getting them to work on Windows (grrrrr!). Thankfully, they worked seamlessly on my Ubuntu virtual machine. For writing more complex scripts, though, you would need some kind of a library that offers an API for controlling the Headless Chrome, such as [Puppeteer](https://pptr.dev/).



So happy hacking, y'all!