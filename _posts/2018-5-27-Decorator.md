---
layout: post
title: The Decorator Pattern
---

![_config.yml]({{ site.baseurl }}/images/decorator/gift.png)

This is the third design pattern introduced in the Head First book. The official definition of the decorator pattern is:

*"It attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality."*

Basically, it allows a user to add new functionality to an existing object without altering its structure. This pattern creates a decorator class which wraps the original class and provides additional functionality keeping class methods signature intact.

The Design Principles it introduces:
1. Classes should be open for extension, but closed for modification.
- *Our goal is to allow classes to be easily extended to incorporate new behavior without modifying existing code.*

___

Now I will try to guide you through the demonstration of this design pattern using my words the best that I can. I'm not really savvy in the lingo of the OO world. So please bear with me.
