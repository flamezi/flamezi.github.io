---
layout: post
title: The Decorator Pattern
---

![_config.yml]({{ site.baseurl }}/images/cleancode/room.png)

This is the third design pattern introduced in the Head First book. The official definition of the decorator pattern is:

*"It attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality."*

Basically, it allows a user to add new functionality to an existing object without altering its structure. This pattern creates a decorator class which wraps the original class and provides additional functionality keeping class methods signature intact.

The Design Principles it introduces:
1. Classes should be open for extension, but closed for modification.
- *Our goal is to allow classes to be easily extended to incorporate new behavior without modifying existing code.*

___

Now I will try to guide you through the demonstration of this design pattern using my words the best that I can. I'm not really savvy in the lingo of the OO world. So please bear with me.

The book uses Coffee as its example. The scenario is the developer is tasked to create an ordering system for a coffee shop. So obviously, he would create the **Beverage** class (coffee shops provide other drinks too). We also need a method to get the cost of the customer's order. We'll call it the cost() method.

![_config.yml]({{ site.baseurl }}/images/decorator/figure01.png)

But like every coffee shop, customers are provided the ability to customize their drinks with several choices of condiments. If we use our initial approach to tackle this problem, we will end up with a very nasty class explosion.

![_config.yml]({{ site.baseurl }}/images/decorator/figure02.png)

This will lead to a maintenance nightmare. One change in cost of condiment would lead to disaster. If you're thinking, "why not place all the condiments as instance variables?". Well, we will also have problems with maintenance.

![_config.yml]({{ site.baseurl }}/images/decorator/figure03.png)

A change in cost will effect the beverage subclasses to modify their codes as well. This is also true if we add new condiments. This will also be a headache.

This is where the **Decorator Pattern** should be used. This will involve "wrapping"/"decorating" objects to add behavior to the object it "wraps"/"decorates".

For example, a customer orders a DarkRoast with Mocha and Whip. It would look like this:

![_config.yml]({{ site.baseurl }}/images/decorator/figure04.png)

This is all possible by implementing the **Decorator Pattern**'s key players which are the **Component** and the **Decorator**.

![_config.yml]({{ site.baseurl }}/images/decorator/figure05.png)

If we will apply this pattern to our example, it would look something like this:

![_config.yml]({{ site.baseurl }}/images/decorator/figure06.png)

If you are still wondering how this all works, here is an example of the code of one Concrete Component and one Concrete Decorator:

![_config.yml]({{ site.baseurl }}/images/decorator/figure07.png)

![_config.yml]({{ site.baseurl }}/images/decorator/figure08.png)

You can see that the decorator gets the base cost of the beverage and adds its behavior to it (in this case, it adds the cost of Mocha). By doing the **Decorator Pattern**, we have effectively provided a flexible alternative to subclassing (and avoiding that terrifying class explosion).
