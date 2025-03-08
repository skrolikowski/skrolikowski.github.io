---
title: Benefits of Unit Testing
author: shane
description: Unit tests allow for making sure the functional logic of your program is guaranteed to be in place and working.
categories: [programming]
tags: [programming, unit-tests, testing]
image:
    path: /assets/img/covers/pexels-photo-546819.jpeg
    alt: Photo by luis gomes from Pexels

toc: false
published: false
comments: false
---



Unit Testing is just one or many approaches to testing your software. The term *unit* can be thought of as a function or a code block that represents a single idea. They allow for making sure the functional logic of your program is guaranteed to be in place and working.

## Benefits of Unit Testing

### Faster Development

Investing the time upfront will save you in the long run. If you write good tests you will write code that performs to your expectation. And that can go a long way when trying to track down unexpected behavior in your program.

### Refactor Allowance

There will often be times when you have several classes that rely on other utility classes (e.g. **Vec2**, **AABB**) Now let's say you want to make an update to your **Vec2** class (or you simply want to refactor it). How do you know the changes you make won't cause several new bugs to appear?

Building a set of tests for your utility classes allow their initial integrity to remain in tact, through any minor edits or refactors. You can quickly make the changes and run the tests. If something breaks, then you've just saved yourself a headache down the road.

Of course if you're making actual functional changes to the utility class itself, then you must remember to update the test(s) as well. But now the [Open/Close Principle] has just been broken.

### Test Driven Development

It happens that you can get so carried away writing code that you forget about testing your code. Going back after the fact to write code is doable, but it isn't as fun and may leave for lazy tests. In other words, it might feel like homework and be treated as such.

Writing your tests first will force you to stop and think about what you're actually try to do; in other words, you are planning. It will also assist you in writing the classes themselves; going back-and-forth between implementing methods and running tests. This is referred to as [Test Driven Development].

## Further Reading

* [Unit Testing](https://en.wikipedia.org/wiki/Unit_testing){: target="_blank"}

[Open/Close Principle]: https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle	"Open/Close Principle"
[Test Driven Development]: https://en.wikipedia.org/wiki/Test-driven_development	"TDD"

---
Photo by [luis gomes from Pexels](https://www.pexels.com/photo/close-up-photo-of-programming-of-codes-546819/)