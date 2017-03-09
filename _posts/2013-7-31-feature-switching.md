---
layout: post
title: "Feature switches"
date: 2013-07-13
categories:
  - programming
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
---

Thought process behind feature & toggles.

Off late Feature switches are a common practice in software development. The credit goes to short development sprints boosted by Agile practices, where the team works on a new feature / section that will be disabled (better term hidden away from user / are not part of the current processing flow) in the immediate release till all parts of the feature is complete and ready to be used.

Software architects and engineers handle this problem using different tools and techniques.

What is a feature?
To give some examples and put a definition of feature in context, a feature can be a new user interface component (like upgraded text area control in web app), upgrading of data store (moving to a new database), a change in the workflow or simply bringing in a new component into an existing process line (naively achieved using  if.. else clause).

So, What are really features?
My definition - "feature is that it is a functional piece of a program or process that is already part of or going to be part of a software application."

The term Feature is clearly a functional programming term - the most relevant object oriented programming term that I can think of is a module.

How a feature can be viewed from an Object oriented perspective?


To define this in object oriented programming terms, a feature is a new implementation of an interface which will injected

[Martin Fowler reference on feature toggles](http://martinfowler.com/bliki/FeatureToggle.html)

[switch statement smells](http://c2.com/cgi/wiki?SwitchStatementsSmell)

Feature toggling should be restricted to only one point in code.
Typically entry point, which works well if the feature is user interface related.

Incase of features that dont correspond to UI. The features must be designed to be toggled from dependency injection configuration. Typically a class like AutofacConfig.cs or similar.

Examples:

`Unity.DefaultContainer.Register(typeof(ILoginProvider), typeof(CookieBasedLoginProvider));`

CookieBasedLoginProvider is a feature here.

Lets say when the organization needs to have a TokenBasedAuthentication, simply a TokenBasedLoginProvider like feature can be implemented and switched directly.

Depending on the feature switch, corresponding Provider can be injected. This way, we dont have to bother about rest of the application and can keep the change limited to the implementation and configuration.

Advantages
- Unit test only the feature implemented.
- Minimal risk as modifications are limited to existing code
