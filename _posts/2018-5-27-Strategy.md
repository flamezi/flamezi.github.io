---
layout: post
title: The Strategy Pattern
---

![_config.yml]({{ site.baseurl }}/images/strategy/brainstorming.png)

This is the first design pattern introduced in the Head First book. The official definition of the strategy pattern is:

*"It defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it."*

Basically, it's used to define behaviors/algorithms for a class that can be changed at run time. When using this design pattern, we create separate classes to represent behaviors. These classes are then used by our original object. By doing this, the object can then have varying behaviors depending on the behavior (strategy) object it uses.

The Design Principles it introduces:
1. Identify the aspects of your application that vary and separate them from what stays the same.
- *If you’ve got some aspect of your code that is changing then you know you’ve got a behavior that needs to be pulled out and separated from all the stuff that doesn’t change*
2. Program to an interface, not an implementation.
- *The point is to exploit polymorphism by programming to a supertype so that the actual runtime object isn’t locked into the code.*
3. Favor composition over inheritance.
- *Creating systems using composition gives you a lot more flexibility. Not only does it let you encapsulate a family of algorithms into their own set of classes, but it also lets you change behavior at runtime*

___

Now I will try to guide you through the demonstration of this design pattern using my words the best that I can. I'm not really savvy in the lingo of the OO world. So please bear with me.

The book uses ducks as the example for implementing this strategy. The scenario is the developer is tasked to create a game about ducks. So obviously, he would create the **Duck** class. This duck class would contain the many methods(behaviors) that a duck would have which will then be inherited by the different duck types i.e. **MallardDuck** and **RedHeadDuck** to name a few.

![_config.yml]({{ site.baseurl }}/images/strategy/figure01.jpg)

But this approach is really a **maintenance nightmare** if you think about implementing ducks that do not fly (like rubber ducks) or ducks that do not quack (like wooden ducks).

What about using interfacing? Create **Flyable** and **Quackable** interfaces that ducks will implement to suit their needs.

![_config.yml]({{ site.baseurl }}/images/strategy/figure02.jpg)
