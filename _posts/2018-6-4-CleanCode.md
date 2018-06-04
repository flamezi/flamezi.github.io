---
layout: post
title: Clean Code and Refactoring
---

![_config.yml]({{ site.baseurl }}/images/cleancode/room.png)

This post will be mostly about spotting code smells and what to do to freshen up those smells. For this post, I've read two books (albeit just the parts about code smells and refactoring them). So, this would be a combination of both books and what I think are important points.

**_"Leave the campground cleaner than you found it."_**

This line from the boy scouts perfectly represents the mindset one needs to effectively spruce up your code. If we all make sure our code is a little cleaner than when we first encountered it, the code will definitely not rot.

The next part of this post will be about the specific smells that feels very close to home since I've pretty much encountered these smells during my programming life. I will not include all smells from the book because that will just turn into a boring mess. I'll let you (the reader) discover the other smells on your own. I highly recommend that you read the books *Clean Code: A Handbook of Agile Software Craftsmanship by Robert C. Martin* and *Refactoring: Improving the Design of Existing Code by Martin Fowler*

___


![_config.yml]({{ site.baseurl }}/images/cleancode/figure01.png)

## Comments

As a programmer, I was always taught that comments are a great way to show how mature you are as a programmer because it showed that you are thinking about the next developer that will potentially work on your codes. But reading these books, I've realized that comments are just a sign of lazy development. Your codes should be able to explain themselves without the help of a few English words.

### Some common code smells:

1. **Inappropriate Information** - Comments that are better placed somewhere else other than your source code should be removed. An example of this is change history. You should let your version control system handle that.
2. **Obsolete Comment** - Not using those comments? sweep them away! If the comments are no longer relevant to the current state of your code, just delete them.
3. **Redundant Comment** - If your comments are just describing the code and the code can describe itself, remove the comments. An example of this is describing a function that gets employees' last names but the function already is named as "getEmployeeLastName". Your comments are no longer welcomed here.
4. **Poorly Written Comment** - Comments are used for communicating with other developers. They lose meaning if others can't understand what you're talking about because of horrendous grammar. Try to clearly convey what you mean as best as you can.
5. **Commented-Out Code** - Again, if the commented part is no longer used or represents the current state of the system, remove those comments. You can use the version control system to check the change history.

### Suggestions from refactoring perspective:

*"If you need a comment to explain what a block of code does, try __Extract Method__. If the method is already extracted but you still need a comment to explain what it does, use __Rename Method__. If you need to state some rules about the required state of the system, use __Introduce Assertion__."*



![_config.yml]({{ site.baseurl }}/images/cleancode/figure02.png)

## General

Next up are common mistakes that programmers do when writing code. (I am guilty of most of these code smells)

### Some common code smells:

1. **Duplication** - There is a great principle introduce in the clean code book. It is the DRY principle (DON'T REPEAT YOURSELF). Each time there is duplication in your code, it just shows that we have missed a chance to apply abstraction. The most common and obvious form of duplication is when you have the same code over and over again. This can be easily solved by using the **Extract Method** and call the code from each place.
2. **Dead Code** - These codes are the no longer touched or passed through by the current logic. These codes can be kick out of the code. According to the Refactoring book, all code should be worth the pay. This can be related to *Lazy Code* which is similar but these codes are still used but not very much. If the code contains subclasses that are not doing enough, try using **Collapse Hierarchy**. Nearly useless codes should be turned into **Inline Class**.
3. **Vertical Separation** - This talks about the travel distance a programmer has to go through just to find related code. Having C++ as my first language, I got used to putting all variables at the top of the method or function. But again, reading this book, I've realized that it's best to place the codes as close as they can be for readability. If locating the related code is still challenging, then maybe the code suffers from having a *Long Method*. Most of the time, all you have to do is **Extract Method** to shorten that long method. You may also find parts of the method that seem to work well together and create a new method.
4. **Inconsistency** - This is probably one of the most frequent code smell I see in our system. This inconsistency pertains to methods/variables/etc. One moment you are using *employeeTransactionResponse* and the next moment you are using *response*. Make up your mind!
5. **Feature Envy** - Maybe you've created a method in a class that you initially thought was perfect for that class. But soon you realized that the method primarily contains methods/data from another class. You should then consider fixing this. Luckily, this is quite quick to fix. The method clearly wants to be somewhere else. You can use **Move Method** to move it there. If only a part of the method is envious, then you can use **Extract Method** on that part and Move Method to place it where it belongs.
6. **Obscured Intent** - Have you encountered a method like "m_otCalc"? You may be thinking, "what the heck is that?". If so, this clearly is a case of intent being totally incomprehensible. Make sure your code clearly shows what you want it to do. Believe it or not, that method was supposed to be for calculating overtime pay.
7. **Prefer Polymorphism to If/Else or Switch/Case** - Do you have a switch statement that performs various actions depending on object type or properties? Is it appearing in many parts of the system? Then it's probably best to use polymorphism instead. The first step should be to use **Extract Method** to extract the conditional statement and then **Move Method** to get it onto the class where the polymorphism is needed. After that, you can now decide whether to use **Replace Type Code with Subclasses** or **Replace Type Code with State/Strategy**. These actions will set up the inheritance structure. After which you can use **Replace Conditional with Polymorphism**.



![_config.yml]({{ site.baseurl }}/images/cleancode/figure03.png)

## Java

The following part will now focus on language specific smells (Particularly, Java). Though since many modern languages are similar with each other, these may also apply to other languages.

### Some common code smells:

1. **Avoid Long Import Lists by Using Wildcards** - Avoid having a long list of lines on top of your java classes by using the wildcard import. Though personally, I am cautious about using the wildcard import. Because in our current system, there are many similarly named classes. The risk of using the wrong class is higher with wildcards and change them can be pretty annoying.
2. **Constants versus Enums** - Enums are awesome to use because it unconsciously forces me to group constants together in one convenient place. It also provides the programmer to change enum values and see if any related values need some changing as well.



![_config.yml]({{ site.baseurl }}/images/cleancode/figure04.png)

## Names

The book states that naming your code should receive the same attention as naming a child. I guess that somehow makes sense especially if you really value your work. In the words of **Michael Feathers**, author of Working Effectively with Legacy Code, *"Clean code always looks like it was written by someone who cares."*

### Some common code smells:

1. **Choose Descriptive Names** - 90% of what makes our code readable is actually from the names we choose. We need to take our time to choose those names wisely and keep them relevant to our code base. Careless naming will always lead to bad things.
2. **Choose Names at the Appropriate Level of Abstraction** - Avoid picking names that communicate implementation. You should try to choose names the reflect the level of abstraction of the class or function in which you are working. Example would be a Vehicle class. Naming a method for transportation as "drive()" would be somehow inappropriate because aircrafts are also considered vehicles and the fly.
3. **Use Standard Nomenclature Where Possible** - Use common names that are easily recognizable by industry people. Example would be for Factory classes, you may suffix them with "Factory". This way it's easily recognizable by other programmers.



![_config.yml]({{ site.baseurl }}/images/cleancode/figure05.png)

## Tests

Refactoring your production code is very important. But refactoring your test code is equally as important. Test codes serve as your manual for how your production code behaves and it showcases the intent of the developer on what the system's behavior should be.

### Some common code smells:

1. **Insufficient Tests** - "That seems enough." This is the common programmer's mindset when it comes to creating the test suite. This will leave some holes in our testing. We should always remember that the test suite should cover all things that can possibly break.
2. **Don’t Skip Trivial Tests** - If the test case seems very minor and easy to do, then why not just do it? It will definitely add to the scope of your test suite and it's easy to write. It's a win-win situation.
3. **Tests Should Be Fast** - Tests are ideally ran after a change in production code to check if we broke anything during our tweaking. If the tests are very slow, then we will be stuck with waiting and waiting and eventually our time will be used up by the slow running tests. Some might even skip running the slow tests.
