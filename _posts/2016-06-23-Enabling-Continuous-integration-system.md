---
layout: post
title: "An Enabling CI system"
comments: true
date: 2016-06-23
categories:
  - programming
  - continuous-integration
  - continuous-deployment
  - travis-ci
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
---
# My two cents on CI,

One of the important features for agile continuously delivered Microservice is a lean process both in engineering and in systems. The CI system is critical to it. Abilities like
- Self-contained build specification
- Simple specification
- Good community support and references
- No hassle of managing agents
- Easy to onboard

 immensely simplify and let the developers concentrate on delivering the working software.

And Travis CI fits this bill, very well.

## A brief on what self contained build specification

If you can mention all about a built process in just one place, one file and include it along with the code in the same repository, in a convenient specification, _how awesome is it?_ That is exactly the Travis yml file.

Of course there are other build systems like CircleCI, Codeship, AppVeyor (for Windows) etc that take the similar route.

### Disadvantage of having build script scattered
Traditional build systems have this problem, where part of the scripts required for build-deploy pipeline gets included along with the source code in its repository, while the build agent also holds intelligence and knowledge has knowledge as to how to build and deploy.

This scattered nature of such build process itself impedes the transparency and simplicity of a autonomous self contained system. This kind of system worked fine when the development team need not have to bother about deployment.

This even worked when we need to deploy regularly but had an expert and his time to get this correct (remember the role called Build manager?). But, do we need need to depend on a expert every time? Especially with a microservice architecture, where new services come up every day? I say no.


## My take on some widespread limitations with Travis CI

#### Cannot build windows based .NET code
This is only a limitation for time being, till we all move on to platform agnostic dotnet frameworks.

#### Cannot pipe the build process
This one came up several times when deciding on CI system. However for the last one year, I haven’t heard anyone needing it. In my opinion, the need for pipelining builds smells an incorrect coupling. Most of the times either
a. domain boundaries are incorrect, so we have to queue builds to get one functionality out
or
b. code boundaries are incorrect, so we have to get more than repo built to get a functionality out.

#### Only limited agents
If a build is taking less than 5 mins including deployment, Do you think the availability of agent will block you? I bet not. We have been living with 2 concurrent jobs / agents for almost one year. We currently have around 15 active repositories using Travis CI and haven’t had a blocking build situation.

After all, when it is getting blocked, we can simply shell some money and get more concurrent jobs.

#### What is your CI story?
Is something not working in your Microservice journey?

What causes the most frustration in your CI process?
