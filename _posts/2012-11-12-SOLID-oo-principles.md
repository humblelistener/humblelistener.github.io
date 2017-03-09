---
layout: post
title: "SOLID principles - primer"
date: 2012-11-12
categories:
  - programming
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
---

SOLID Principles - primer

**S –Single responsibility principle**

Wikipedia defines it as **every class should have a single
responsibility, and that responsibility should be entirely encapsulated
by the class**

The idea behind this principle is that, any change should only be
limited to a class that is responsible for that feature. None of the
dependent classes or consumers should have to be modified to adjust to
this change.

*What is the advantage?*

By following this principle, we can limit the number of places we have
to change the code for a single change in a feature. This directs
reduces the cyclomatic complexity.

Other than the metric advantage mentioned above, following this
principle leads to


* Simplicity in the design / code
* Makes design / code easily understandable
* Increases maintainability and increases engineers good karma


**O –Open/closed principle**

Wikipedia definition says *software entities (classes, modules,
functions, etc.) should be open for extension, but closed for
modification*

If you know the code that you are writing is susceptible to change when
you are writing it – it is a good candidate for applying this principle.
However if the developer is new for the domain and is not able to
predict that the possible change coming (which happens most of the
time), it is fine to write the simplest piece of code that works.

Although, the moment he realizes that there is change coming, he should
be ready to refactor and apply this principle. The next time change
comes, the code modification should be an extension rather than
modification.

This technique can be summarized by the below funny statements

* “Fool me once, shame on you; fool me twice, shame on me”

Ideally any software design should be closed for modifications and open
for extensions – which is very tough. The best person to guess this is
the developer / designer – who will be the only person knowing what
areas of his code are susceptible to change.

The design patterns that come to rescue when you encounter candidates
for this principle are

* Template method pattern – Rely on abstraction

* Strategy pattern – rely on composition.

Or simply sometimes adding parameters to the function can be very
effective.

**L – Liskov Substitution Principle**

Wikipedia definition - *“if S is a subtype of T, then objects of type T
may be replaced with objects of type ”*

The converse of this theory in simple terms is - “*If it looks like a
duck and sounds like a duck, but needs batteries then it may well not be
a substitutable duck*”.

There is paradigm shift between how you look at inheritance in this
principle - “IS-A” relation is replaced by “IS-SUBSTITUTABLE-FOR”
relationship.

The primary objective of this design is - the calling code should not
know the difference between the base type and a sub type. Irrespective
of the actual type being passed, the calling code should be able to do
all the operation.

Another variance where this principle can be applied is when the subtype
does not implement only one (or few) operations of the base type. This
could well mean that they are not exactly replaceable substitutes.

This happens when either when the interfaces or base classes are not
properly segregated (candidate for the next principle: Interface
segregation) or when “IS-SUBSTITUTABLE-FOR” principle is simply broken.


*How do you identify them in your code?*

Any part of code where you have to convert a base type to a specific
type to do an operation – then the code violates this principle and
requires refactoring.


Any operation that can be performed on a subtype but cannot be done on
another subtype with the same parent, then this principle is
compromised.

**I – Interface Segregation Principle**

For this principle, class and interface are interchangeable terms. Any
class is considered an implementation of interface although interface
may not have been abstracted.

I wasn’t able to find a slick definition of this principle in wiki – so
let use this

*“Clients should not be forced to depend on methods they do not use.”*

*Corollary – prefer small, cohesive interfaces to “fat” interfaces.*

*Whenever possible, let the client define the interface.*

When client unit needs only a few operations, support only those
operation from your interface – any other methods in the interface are
just nonsense for the client and could increase complexity of the code.

Interface segregation violations result in classes that depend on things
they do not need, increasing coupling and reducing flexibility and
maintainability.

Interfaces with unimplemented interface methods are also candid for this
principle (as they are for Liskov Substitution principle)

Doctor’s prescription notes for interface segregation

* Client references an interface but only uses a portion of it – refactor
it using façade without touching the interface until the more pain is
localized in this region (notice façade pattern to the rescue).

* If you have a fat interface and facing problem with it – consider
breaking what you need into smaller interface and let the fat interface
inherit this new one.

* If you have problem using a fat interface that you do not own – consider
creating a smaller interface that acts as an adapter around the fat
interface and use it – (notice adapter pattern to the rescue).

**D – Dependency Inversion / Inversion of control**

Off late this principle has become very common with the advent of a
wonderful reference implementation available with us in the form of
ASP.NET MVC Framework – This statement is targeted only at .NET
developers.

Wikipedia definition –
a. *High level
modules should not depend on low level modules. Both should depend on
abstractions.*

b. *Abstractions should not depend upon details. Details should
depend upon abstractions.*

One very good example that I read about that suits well for dependency
inversion are electrical plugs/ sockets. How? All electrical appliance
depend on electricity, just because it is dependent they are not
directly connected to electrical wires running behind the wall. Instead
we use plugs / sockets. By using this we invert the dependency by giving
the flexibility of connecting to a wire behind the wall or connecting to
UPS box based on the need. Because appliances are not bothered where the
electricity comes from it makes sense. Here plugs / sockets are
abstractions. Appliance and Electricity are details – which depend on
the abstractions.

*How do I identify the candid’s for this principle?*

Anything that you are not able to unit test effectively without
depending on the environment are all candid’s for this principle.

*How do I make them follow this principle?*

In simple one line answer is “use dependency injection”.

*How do I identify them when designing or implementing?*

Honestly identify the dependencies that are in your implementation. Once
you are able to identify it, design your code around to allow these
dependencies to be injected from outside.

I know this statement is cruel, considering Framework classes and static
methods from Framework. Considers Microsoft Fakes if you are bothered
about it. Especially if you are working on a maintenance project and
trying to follow this principle you will appreciate Fakes library’s –
shim concept.

For dependency injection again, there are multiple frameworks available
like (Unity, Ninject etc.. ) which all really good.

More references on dependency injection and this principle

[Dependency injection by Martin Fowler](http://martinfowler.com/articles/injection.html)

[More reference](http://msdn.microsoft.com/en-us/library/hh549175.aspx)

As I wrote, I realized that I can only the surface of these principles
here. You can consider this place to get an idea of these principles and
can dive deep in internet based on the principles of your interest.

I also suggest reading ***Robert C Martin’s – “Clean Code”*** book. I strongly feel every software engineer should have read this book.
