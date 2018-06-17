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

Traditionally, the point of software release has been a time fraught with stress.
At the same time, when compared to the disciplines associated with creation and
management of code, it is treated as an unverified, manual process that relies on
ad-hoc configuration management techniques for crucial aspects of the configuration
of the system. In our view, the stress associated with software releases and
their manual, error-prone nature are related factors.
By adopting the techniques of automated build, test, and deployment, we gain
many benefits. We gain the ability to verify changes, to make the process reproducible
across a range of environments, and to largely eliminate the opportunity
for errors to creep into production. We gain the ability to deploy changes, and
so bring business benefits more quickly, because the release process itself is no
longer a hurdle. Implementing an automated system encourages us to implement
other good practices, such as behavior-driven development and comprehensive
configuration management.
We also gain the ability to spend more weekends with our families and friends
and to live our lives with less stress, while at the same time being more productive.
What is not to like about that? Life is too short to spend our weekends in server
rooms deploying applications.
The automation of the development, test, and release processes has a profound
impact on the speed, quality, and cost of releasing software. One of the authors
works on a complex distributed system. Release into production for this system,
including data migration in large-scale databases, takes between 5 and 20 minutes
depending on the scale of the data migration associated with a particular release.
Moving the data takes a long time. A closely related, and comparable, system of
which we are aware takes 30 days for the same part of the process.
The rest of this book will be more concrete in the advice that we offer and the
recommendations that we make, but we wanted this chapter to give you an ideal,
but nevertheless realistic, view of the scope of this book—from twenty thousand
feet. The projects that we have referred to here are all real projects, and while
we may have disguised them a little to protect the guilty, we have tried very hard
not to exaggerate any technical detail or the value of any technique.

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure02.png)

## Configuration Management

Configuration management is the foundation of everything else in this book. It
is impossible to do continuous integration, release management, and deployment
pipelining without it. It also makes a huge positive impact on collaboration
within delivery teams. As we hope we have made clear, it is not just a question
of choosing and implementing a tool, although that is important; it is also,
crucially, a question of putting good practices into place.
If your configuration management process is sound, you should be able to
answer “yes” to the following questions:
• Could you completely re-create your production system, excluding production
data, from scratch from the version-controlled assets that you store?
• Could you regress to an earlier, known good state of your application?
• Can you be sure that each deployed environment in production, in staging,
and in test is set up in precisely the same way?
If not, then your organization is at risk. In particular, we recommend having
a strategy for storing baselines and controlling changes to:
• Your applications’ source code, build scripts, tests, documentation,
requirements, database scripts, libraries, and configuration files
• Your development, testing, and operations toolchains
• All environments used in development, testing, and production
• The entire application stack associated with your applications—both binaries
and configuration
• The configuration associated with every application in every environment
it runs in, across the entire application lifecycle (building, deployment,
testing, operation)

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure03.png)

## Continuous Integration

If you were to choose just one of the practices in this book to implement on a
development team, we would suggest that you choose continuous integration.
Time and time again we have seen it make a step change to the productivity of
software development teams.
To implement continuous integration is to create a paradigm shift in your
team. Without CI, your application is broken until you prove otherwise. With
CI, the default state of your application is working, albeit with a level of confidence
that depends upon the extent of your automated test coverage. CI creates
a tight feedback loop which allows you to find problems as soon as they are
introduced, when they are cheap to fix.
Implementing CI forces you to follow two other important practices: good
configuration management and the creation and maintenance of an automated
build and test process. For some teams, that will seem like a lot to bite off, but
they can be achieved incrementally. We discussed the steps to good configuration
management in the previous chapter. There is more on build automation in
Chapter 6, “Build and Deployment Scripting.” We cover testing in more detail
in the next chapter.
It should be clear that CI requires good team discipline—but then, any process
requires this. What is different about continuous integration is that you have a
simple indicator of whether or not discipline is being followed: The build stays
green. If you discover that the build is green but there is insufficient discipline,
for example poor unit test coverage, you can easily add checks to your CI system
to enforce better behavior.
This brings us to our final point. An established CI system is a foundation on
which you can build more infrastructure:
• Big visible displays which aggregate information from your build system
to provide high-quality feedback
• A system of reference for reports and installers for your testing team
• A provider of data on the quality of the application for project managers
• A system that can be extended out to production, using the deployment
pipeline, which provides testers and operations staff with push-button
deployments

![_config.yml]({{ site.baseurl }}/images/contdelivery/figure04.png)

## Implementing a Testing Strategy

In many projects, testing is treated as a distinct phase carried out by specialists.
However, high-quality software is only possible if testing becomes the responsibility
of everybody involved in delivering software and is practiced right from
the beginning of the project and throughout its life. Testing is primarily concerned
with establishing feedback loops that drive development, design, and release.
Any plan that defers testing to the end of the project is broken because it removes
the feedback loop that generates higher quality, higher productivity, and, most
importantly of all, any measure of how complete the project is.
The shortest feedback loops are created through sets of automated tests that
are run upon every change to the system. Such tests should run at all levels—from
unit tests up to acceptance tests (both functional and nonfunctional). Automated
tests should be supplemented with manual testing such as exploratory testing
and showcases. This chapter aims to give you a good understanding of the various
types of automated and manual tests required to create excellent feedback and
how to implement them on various types of projects.
In the principles that we described in the “Introduction” section on page 83,
we discuss what defines “done.” Incorporating testing into every part of your
delivery process is vital to getting work done. Since our approach to testing
defines our understanding of “done,” the results of testing are the cornerstone
of project planning.
Testing is fundamentally interconnected with your definition of “done,” and
your testing strategy should be focused on being able to deliver that understanding
feature by feature and ensuring that testing is pervasive throughout your process.

__

This is just the foundations of Continuous Delivery. If you want to learn in-depth knowledge, I suggest you to read *Continuous Delivery By Jez Humble and David Farley* as it will give you the best start for implementing this on your project.
