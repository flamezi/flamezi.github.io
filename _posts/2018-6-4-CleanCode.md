---
layout: post
title: Clean Code and Refactoring
---

![_config.yml]({{ site.baseurl }}/images/cleancode/room.png)

This post will be mostly about spotting code smells and what to do to freshen up those smells. For this post, I've read two books (albeit just the parts about code smells and refactoring them). So, this would be a combination of both books and what I think are important points.

*"Leave the campground cleaner than you found it."*

This line from the boy scouts perfectly represents the mindset one needs to effectively spruce up your code. If we all make sure our code is a little cleaner than when we first encountered it, the code will definitely not rot.

The next part of this post will be about the specific smells that feels very close to home since I've pretty much encountered these smells during my programming life. I will not include all smells from the book because that will just turn into a boring mess. I'll let you (the reader) discover the other smells on your own. I highly recommend that you read the books *Clean Code: A Handbook of Agile Software Craftsmanship by Robert C. Martin* and *Refactoring: Improving the Design of Existing Code by Martin Fowler*

___


![_config.yml]({{ site.baseurl }}/images/cleancode/figure01.png)

## Comments

As a programmer, I was always taught that comments are a great way to show how mature you are as a programmer because it showed that you are thinking about the next developer that will potentially work on your codes. But reading these books, I've realized that comments are just a sign of lazy development. Your codes should be able to explain themselves without the help of a few English words.

### Some common code smells:

1. Inappropriate Information
  Comments that are better placed somewhere else other than your source code should be removed. An example of this is change history. You should let your version control system handle that.
2. Obsolete Comment
  Not using those comments? sweep them away! If the comments are no longer relevant to the current state of your code, just delete them.
3. Redundant Comment
  If your comments are just describing the code and the code can describe itself, remove the comments. An example of this is describing a function that gets employees' last names but the function already is named as "getEmployeeLastName". Your comments are no longer welcomed here.
4. Poorly Written Comment
  Comments are used for communicating with other developers. They lose meaning if others can't understand what you're talking about because of horrendous grammar. Try to clearly convey what you mean as best as you can.
5. Commented-Out Code
  Again, if the commented part is no longer used or represents the current state of the system, remove those comments. You can use the version control system to check the change history.

## General