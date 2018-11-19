+++
title = "Day 31: Introducing Property-based Testing"
date = 2018-11-19T15:53:06+01:00
draft = false
tags = []
categories = []
+++

This week I am venturing into the topic of ___property-based testing___, which is something I may have heard of before, but can only remember vaguely. Therefore it's safe to say that I'm starting from scratch here.

So far I've only ever done the _example-based_ tests (honestly, before today I didn't even know they were called like that; I simply refered to them as _tests_). I'd say that these tests resemble stories, or anecdotes about your program in a way. They specify what happens in the story, as well as how the story must end. This means that the assertions are hard-coded - you know exactly what the input is, as well as the output - and you write a test to check for it.

But what if there are many edge or special cases that we need to think about? Or, what if we don't _know_ what the expected output should be?

Property-based testing may be an answer to those questions. Here, the approach is slightly different. Firstly, you don't run your test just once for a given scenario; rather, you run it many times, over and over, for different inputs. And, most importantly, you don't check for hard-coded expected results - in this case, you check ___properties___. A _property_ can be defined as a high-level specification of behavior that should be satisfied for a range of inputs. Of course, all of this would be too tedious to do manually, so we can make use of the many property-based testing frameworks and make our lives much easier.  

For example, if we want to test a method that reverses a list, example-based test could look like this:

``` scala
val ls = List(1, 2, 3)
assert(ls.reverse === List(3, 2, 1))
```

Whereas the property-based test could look like this:

``` scala
val reverseProperty = forAll { ls =>
    ls.reverse.reverse == ls
}
```

Here the testing framework would generate (usually) 100 test cases (empty lists, non-empty lists, one element lists, extremelly long lists - essentially all important edge cases) and check whether each of those lists, when reversed twice, would return the original list. So, as you see, there are no hard-coded assertions. It basically comes down to checking the rules that your program should satisfy.

Which makes it all the more complex.

I guess for humans it's just easier to think in stories, and example-based tests come to us more naturally. Property-based testing makes you think deeper about your specification, and all the rules it should satisfy. If I want to test a method that reverses a list, what does reversing a list actually mean? (Ok, reversing a list may be too simple as an example here, but you get the idea.) Besides, thinking about the output is still not enough; what about the input? What kind of input should we support? How can we generate it? And so on.

So all in all, I'd say property-based testing is hard, and should be handled with care. To quote Jessica Ker: 

> "Writing tests first forces you to think about the problem you're solving. Writing property-based tests forces you to think way harder."

Is property-based testing necessary? Perhaps not. I'm pretty sure you can test an application quite well even without it. Is it useful, though? Sure it is! Writing property-based tests forces you to think more about the code and the rules it should satisfy. It helps you understand the code better, and adjust accordingly.

Besides, there are few better feelings than seeing 100 assertions successfully pass, am I right?