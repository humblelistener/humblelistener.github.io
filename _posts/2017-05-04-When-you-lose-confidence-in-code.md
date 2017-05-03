---
layout: post
title: "What do you do when you lose confidence in code?"
date: 2017-05-04
categories:
  - software testing
  - software engineering
  - A/B testing
  - Traffic splitting
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
comments: true
---
# What do you do when you lose confidence in code?

This is happening to me.

One of the inherited product I have is so complex that investing time and money on any of the following feels useless.

### Unit tests
The technology literally doesn't bend to write unit tests. I know the rebel in you telling that there should be a way to write unit tests on it. But I say, it is not worth it.

### Functional UI tests
Even if I overcome the response time, feedback cycle and brittleness of the test suite, It is hard to convince myself that a good coverage can be achieved without large efforts.

### Consumer-driven contracts
Wish I can find a way to do this in the given technology. The complex branching, conditional flows and data-driven decisions in the system make me think even if I magic a way to do consumer driven contracts on this system, I will age by the time I set up contracts with decent coverage.

### Manual/Exploratory testing
God forbid, this is the option that we are relying currently on the product along with some basic functional UI test coverage. As with any manual work, it has a big gap for human error and hell a lot of time it will take if every code path being affected is to be tested, especially when trying to change the underlying concepts of the system.

In such a state, it is not surprising that the urge to hide under the desk after the deploy button is clicked every time.

## Where is the hope?
The last hope, I am thinking of pursuing is to set up a beta environment and set up a traffic splitting between live and beta environment. A traffic split that can be finely controlled. So any risky change can be deployed to a variable percentage of users, monitor and decide to increase of decrease the percentage over time with confidence.

This is not a new technique, this is similar to A/B testing. Nginx like proxies and load balancers pioneered it.

In this particular case, I am thinking of pursuing AWS's Application load balancer to achieve it.

Check out the [A/B testing section in the AWS Load balancing documentation here](https://aws.amazon.com/blogs/devops/introducing-application-load-balancer-unlocking-and-optimizing-architectures/).

I shall share more details on how it went. In the meanwhile, I am to learn from your experience, if you leave comments.
