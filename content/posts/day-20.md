+++
title = "Day 20: Playing With My Headless Puppet"
date = 2018-10-31T15:20:34+01:00
draft = false
tags = []
categories = []
+++

I continued playing around with [Puppeteer](https://pptr.dev/) and Headless Chrome today, this time writing some actual __headless browser tests__. I've spent quite a bit of time trying to find a proper tutorial online that would explain to me in simple words what I need to do. However, I wasn't that lucky. I gathered some useful tidbits here and there (mostly from this [page](https://www.valentinog.com/blog/ui-testing-jest-puppetteer/)), but ultimately ended up "brute forcing" my way through it, trying many different approaches until I finally had all the tests green.

So in an attempt to make life easier for someone that decides to test his luck with "puppeteering" like me, I decided to write a brief blog post explaining how you can use Puppeteer to write tests for your JavaScript application. Not sure if this is the proper way to do it, but hey, it works!

Anyways, here's how a simple test template could look like.

First, you import Puppeteer, specify the URL of the page to test, and define variables needed for Puppeteer.

```javascript
import puppeteer from "puppeteer"
const url = <your_url_goes_here>

let browser
let page
```

Then, you specify what needs to be done before and after the tests. Before we run a test, we need a browser to run it in. Once the browser is spawned, a new page is opened and we are ready to start the tests. Upon completing all tests, the browser is closed. Of course, here we could have used `beforeEach` and `afterEach` methods as well, but it simply made more sense to use the same browser for all tests (otherwise we would lose precious time!).

```javascript
beforeAll(async () => {
	browser = await puppeteer.launch()
	page = await browser.newPage()
});

afterAll(() => {
	browser.close() 
});
```

And here is how a test looks like. Once we go to a page we want tested, we can perform some actions on it. Puppeteer offers a wide range of functions for that, including mimicking mouse clicks, keyboard typing, etc. It also allows us to fetch specific elements on the page (for example using their class name or id) and inspect their CSS styles. For reference, check out the [Puppeteer API](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md).

```javascript
describe("test group", () => {
    test("test name", async () => {
        await page.goto(url)
        // perform some actions
        // assertions
    });
});
```

In order to make assertions, we need some help from external libraries. I used [Jest](https://jestjs.io/), which is a library for testing JavaScript code developed by Facebook, but there are many other good ones out there as well. Feel free to use whichever you like best.

Finally, once we start the tests using the `npm test` command, we can see the results in our console. Remember, we are using a headless browser here, so we won't be able to see how the tests are executed. There's a trick if we want to go around it, though. Here are the steps.

1. Launch the browser in non-headless mode, configure it to run the actions in slow motion (otherwise it will be so fast that you won't be able to see anything!) and set its dimensions.

```javascript
browser = await puppeteer.launch({ 
	headless: false, 
	slowMo: 80, 
	args: [`--window-size=${width},${height}`] 
});
```

2. Set the dimensions of the page, too.

```javascript
page = await browser.newPage(); 
await page.setViewport({ width, height }); 
```

3. When performing a test, set a timeout to a larger value (for example 15000). If this is not done, the test will be aborted after the default 5 seconds, which is not enough to see everything unfold on your screen.

```javascript
test("test name", async () => {
    // ...
}, 15000); 
```

Now, run your tests again and see how stuff magically happens in your browser!

It sure is fun to be a puppeteer! :)