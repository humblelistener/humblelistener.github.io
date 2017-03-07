---
layout: post
title: "Understanding optional parameters in c#"
modified:
categories: blog
excerpt:
tags: [optional-parameters-c#]
image:
  feature:
date: 2012-12-16
---

C# and its optional parameters - a language feature..


Optional parameters is a language feature, the compiler is responsible for
translating the calls to methods with optional parameters to full call
with values.

Look at this simple piece of code below,</span>


When you disassemble these methods, you will see that the C\# compiler
actually replaced the call to TestMethod with one parameter to a call
with both the parameters. The screen shot from ildasm proves
that,

![](https://raw.githubusercontent.com/humblelistener/humblelistener.github.io/master/images/posts-images/demystify-optional-params-c%23-1.png)


The implication is that methods utilizing optional parameters cannot be
bound at run time. The below line of code will not compile because, the
line is trying to utilize default value set in optional second parameter
of the TestMethod. However, because this bound only during the run time,
compiler will  not have any control to pass the default values like in
the screen shot. Hence this is currently limited by the compiler.

` Func<int, bool> func = TestMethod;`


The work around is to simply bind the func to an anonymous method which
can have the call to TestMethod in its body. Like below,


` Func<int, bool> func = (value) => TestMethod(value);`
