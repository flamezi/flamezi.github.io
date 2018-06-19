---
layout: post
title: Continuous Delivery
---

![_config.yml]({{ site.baseurl }}/images/contdelivery/delivery-truck.png)

This post will tackle the foundations of the Continuous Delivery pipeline and the concepts or ideas surrounding it. The info here is based on the book *Continuous Delivery By Jez Humble and David Farley*. As the book tells us, this information will benefit all of the members of the team as the book aims to improve the collaboration between the individuals who are responsible for delivering the software/product.

The idea of Continuous Delivery is very far from the traditional approach to software delivery and there are many concepts introduced that will challenge the views of people regardless of experience.

I will stick to the format of the book by splitting this post into four parts (not including this intro)

___


![_config.yml]({{ site.baseurl }}/images/contdelivery/figure01.png)

## The Problem of Delivering Software

One of the main points of this books to alleviate stress and a person who experienced the traditional software delivery practice would know that the process comes with a mountain of stress.
If you're not convinced that you're doing something wrong, then you can check the following ant patterns if they are familiar to your situation.

**Deploying Software Manually**
Manually deploying software means manually creating documentation of steps and manually testing the software is correctly running. If there is something wrong, the development team is called and corrections will be made during the release itself. This eventually leads to unpredictable releases and people who need to stay up at the middle of the night just to do verification.

*Instead of this ...* your team can focus on automating the deployment process. Target to have only two manual tasks: pick the version and environment and pressing the "deploy" button. Your goal should be to have a single automated process to package your software. This automation will leave minimal room for errors and will make the process repeatable. With automation, you can have your scripts serve as your documentation

**Deploying to a Production-like Environment Only after Development Is Complete**
If the team is restricted to deploying to production-like environments only after development (worse would be during the release process) then this will be a late stage for other people to interact with what you've done. This means feedback will not be as timely. Feedback from your users or business people is key to measuring value. This also poses a threat to the validity of your testing because this means the testing parameters you've completed can be far from the parameters of a prod-like environment.

*Instead of this ...* your team can focus on integrating the testing, deployment, and release processes into the development stage. This will enable you to have a low risk production release since you've already done the process in your development stage.

**Manual Configuration Management of Production Environments**
This is most obvious when you have deployed the software to non-prod environment but when you eventually deploy to production, the deployment fails. This also means you need to have environments that are time consuming to setup and reverting back to earlier configurations of your system is near impossible

*Instead of this ...* your team can focus on placing all of your configurations in your version control system to be applied by your automated process. This means all the configurations of all of the available environments. This will also help your process to be incredibly repeatable.

**_How Can You Achieve All This?_**
Well, keep these two words in mind: *Automated* and *Frequent*.

1. Automated - If your whole release process is automated, then it is most likely repeatable. Each time you go through this process, it will be the same regardless of your environment. It will be predictable and easily monitored.
2. Frequent - Making your releases frequent will allow the average between them will be smaller and smaller. A small release period will mean timely feedback. This will also mean reverting will be easier because the change is very small. This ultimately leads to lower risks when releasing.

**_Deciding To Make The Change_**
You need to keep these *Principles of Software Delivery*

1. Create a Repeatable, Reliable Process for Releasing Software - This repeatable and reliable process relies on making your whole process automated and keeping everything you need for delivering your software in version control.
2. Automate Almost Everything - The word "almost" is used there since you really can't automate everything. You still need manual showcases and manual testing for exploring your software. But still, target to automate everything else.
3. Keep Everything in Version Control - Keeping all of the configurations and files needed for your software delivery in version control will allow you to manage your deployments and reverts with relative ease.
4. If It Hurts, Do It More Frequently, and Bring the Pain Forward - This is a general principle and can be applied to many parts of your process. An example would be testing. If it's difficult, do it more frequently and bring it forward. This will allow you to focus and practice with the negative feedback you get (eventually allowing you to grow)
5. Build Quality In - The main thing you need to remember for this principle is *The earlier you catch defects, the cheaper they are to fix*. This again is enabled if you properly setup automated testing and code checks in your development process.
6. Done Means Released - This is enforced because the real indicator of a successful enhancement or code change should be when it gives value to your user and it only gives value when it is released.
7. Everybody Is Responsible for the Delivery Process - If we keep the tradition of having different teams oversee different stages then this will open up possibilities of finger pointing when something goes wrong. People will ignore stages not related to their work.
8. Continuous Improvement - This applies not only to the software that continuously evolves. This also applies to your delivery process.

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure02.png)

## Configuration Management
The definition given by the book for Configuration Management is:

**_Configuration management refers to the process by which all artifacts relevant to your project, and the relationships between them, are stored, retrieved, uniquely identified, and modified._**

Seeing this, it's understandable why people often also call this as "version control". Your target should be the following points:
1. Make sure you are able to completely recreate your production software from scratch from the assets you store in version control.
2. Make sure you are able to revert to an earlier working state of your software.
3. Make sure that deploying to non-production environments is exactly the same way as deploying to production.

If you avoid configuration management, you are definitely at risk of having unpredictable deployments thus opening a door to many more issues.

You can achieve great management by focusing on using version control properly by keeping absolutely everything in version control and committing regularly. In version control, make sure you are managing your dependencies, software configuration, and the environments. Specifically, make sure to have the following:
1. *Your applications’ source code, build scripts, tests, documentation, requirements, database scripts, libraries, and configuration files*
2. *Your development, testing, and operations toolchains*
3. *All environments used in development, testing, and production*
4. *The entire application stack associated with your applications—both binaries and configuration*
5. *The configuration associated with every application in every environment it runs in, across the entire application lifecycle (building, deployment, testing, operation)*

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure03.png)

## Continuous Integration
Continuous Integration will always be a controversial topic for a traditional team. It is a paradigm shift for any team starting up with agile practices. The best argument I've seen for using CI is the default state of your software.

*Without CI, your application is broken until you prove otherwise. With CI, the default state of your application is working*

Though this comes with a disclaimer. The "working" there depends on the coverage of your automated testing. Using CI creates a feedback mechanism that is fast and reliable. Having this fast feedback allows us to respond to issues when they first pop up. This means it will definitely be cheaper to fix.

There are three main things you need to begin setting up your CI:
*Version Control*, *An Automated Build*, and *Agreement of the Team*
These three points are pretty much self explanatory (also, I just don't want to repeat myself over and over again ;) ).

Establishing your team's CI will pave way to many great things that will benefit your team. Namely, you can have:
1. Visual tools to display information about your builds which will provide easier ways to give you feedback (in our team, we use two monitors placed in a common area).
2. Data about your overall quality (this is will be loved by managers).
3. A pipeline to not only build, test, and deploy to non-prod environments but also to prod environment itself.

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure04.png)

## Implementing a Testing Strategy
Traditionally, testing will be a separate stage in the life of a code change or enhancement. But the ideal and most effective way is actually having the testing as a common responsibility among everybody in the team. Not only this, testing should not only be stuck in a single stage. It should be performed from beginning to end.

Constant testing will drive our development, design, and release. If we establish a great feedback mechanism, we can be assured that we will detect issues with the deployment early on. This feedback loop is made possible by your automated tests. These tests work hand in hand with manual testing because we should target a complete testing strategy where we test from unit tests up to the exploratory testing and showcases.

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure05.png)

Looking at the figure above, your team should target to have all these implemented when deploying software. This will definitely ensure high quality software.

Testing should be tightly coupled with your definition of **done**. Your testing strategy will ensure that this is true in every increment to your software.

__

This is just the foundations of Continuous Delivery. If you want to learn in-depth knowledge, I suggest you to read *Continuous Delivery By Jez Humble and David Farley* as it will give you the best start for implementing this on your project.
