---
layout: post
title: The Strategy Pattern
---

![_config.yml]({{ site.baseurl }}/images/brainstorming.png)

This is the first design pattern introduced in the Head First book. The official definition of the strategy pattern is:

*"It defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it."*

Basically, it's used to define behaviors/algorithms for a class that can be changed at run time. When using this design pattern, we create separate classes to represent behaviors. These classes are then used by our original object. By doing this, the object can then have varying behaviors depending on the behavior (strategy) object it uses.

The Design Principles it introduces:
1. Program to an interface, not an implementation.
- *The point is to exploit polymorphism by programming to a supertype so that the actual runtime object isn’t locked into the code.*
2. Favor composition over inheritance.
- *Creating systems using composition gives you a lot more flexibility. Not only does it let you encapsulate a family of algorithms into their own set of classes, but it also lets you change behavior at runtime as long as the object you’re composing with implements the correct behavior interface*
