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

![_config.yml]({{ site.baseurl }}/images/strategy/figure01.png)

But this approach is really a **maintenance nightmare** if you think about implementing ducks that do not fly (like rubber ducks) or ducks that do not quack (like wooden ducks).

What about using interfacing? Create **Flyable** and **Quackable** interfaces that ducks will implement to suit their needs.

![_config.yml]({{ site.baseurl }}/images/strategy/figure02.png)

But what if you need to change something minor in the flying behavior? You will see that this will lead to more maintenance headaches because a simple change in the behavior will lead to an update to all of the implementations that uses that behavior.

This problem exposes the most important aspect we need to keep in mind when developing software. **_Change Is Constant_**. Now, with that in mind. The first thing you need to do to apply the **Strategy Pattern** is that we need to separate what changes from what stays the same.

![_config.yml]({{ site.baseurl }}/images/strategy/figure03.png)

With this approach, we effectively allow other objects to reuse the behaviors because these behaviors are not hidden in our **Duck** classes anymore. This allows us to add new behaviors without actually modifying our existing behavior classes or any of the Duck classes that use the fly and quack behavior.

![_config.yml]({{ site.baseurl }}/images/strategy/figure04.png)

Actual integration of this approach would require us to add two new instance variables to our **Duck** class. Now each duck object will set these variables polymorphically to reference the specific behavior type it would like at runtime. With this addition, we can now remove the fly() and quack() methods in the duck classes and replace it with something like performFly() and performQuack(). These methods will then call the fly() and quack() methods in the behavior variables we just added.

![_config.yml]({{ site.baseurl }}/images/strategy/figure05.png)

What does this actually do? Well, it effectively removes the burden of doing the behavior from the **Duck** class and transfer the responsibility to the behavior interfaces we created. This will allow us to freely setup the behavior types of each duck subclasses depending on which behaviors we set as its flyBehavior and quackBehavior. **_This will then allow us to set the behavior our "Duck" dynamically during runtime_**.

![_config.yml]({{ site.baseurl }}/images/strategy/figure06.png)

![_config.yml]({{ site.baseurl }}/images/strategy/figure07.png)

Further expanding the ability of the **Strategy Pattern** would be to add a setter method in the **Duck** class to dynamically change the behaviors in runtime. This will allow something like the **ModelDuck** who cannot fly to magically fly with one call from the setter method.

![_config.yml]({{ site.baseurl }}/images/strategy/figure08.png)

This is the magic of the **Strategy Pattern**. It allows us to define a family of algorithms, which we encapsulate and make them interchangeable. The **Strategy  Pattern** lets the algorithm vary independently from clients that use it.
