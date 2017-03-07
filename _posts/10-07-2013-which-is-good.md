---
layout: post
title: "Good code?"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2013-07-10
---

Good coding Practice

Today, while working along in the new gig, it so happened that we had a
little conversation on this topic. Which is better? to provide easily
maintainable code to the developer or to ensure the cleaner code of the
browser? Example 1: (relevant separation) File 1 default.html

[![](http://4.bp.blogspot.com/-WuvjEExSyJ0/Ud1g_4Av_dI/AAAAAAAAQFU/f_B4U77F_lw/s1600/Untitled.png)](http://4.bp.blogspot.com/-WuvjEExSyJ0/Ud1g_4Av_dI/AAAAAAAAQFU/f_B4U77F_lw/s1600/Untitled.png)

In the default.html shown above, the view contains a script elements
that is responsible for passing information related to view to the
actual behavior - per the example ListViewModel function. Example 2
(complete separation) File 1 default.html

[![](http://1.bp.blogspot.com/-NjhCuIN5G9U/Ud1i31uZWnI/AAAAAAAAQFs/rXnYe8GAeqI/s1600/Untitled.png)](http://1.bp.blogspot.com/-NjhCuIN5G9U/Ud1i31uZWnI/AAAAAAAAQFs/rXnYe8GAeqI/s1600/Untitled.png)


File 2 productsList.js

[![](http://2.bp.blogspot.com/-IpeX4-dYyGg/Ud1jJ0ZaUrI/AAAAAAAAQF0/_pDUTtdMJmQ/s1600/Untitled.png)](http://2.bp.blogspot.com/-IpeX4-dYyGg/Ud1jJ0ZaUrI/AAAAAAAAQF0/_pDUTtdMJmQ/s1600/Untitled.png)


In example 2, I am having 2 files, the first file, default.html has only
the view (html) and the file 2 contains some information relevant to the
view and some behavior. For case of this study, I am calling example 1
as relevant separation and example 2 as complete separation. Following
are points comparing and contrasting the two, **Relevant separation is
developer friendly** Any developer looks at only the default.html can
understand what are the different components of the view that the
behavior expects. Whereas in complete separation, the developer has to
look around to understand what changes in view could break the behavior.
**Complete separation is browser friendly** When I say the browser here,
it relates to the performance in the browser as well as separation of
view and behavior in the browser or in other words the rendered output.
While this could be good example of unobstructive scripts, it causes
pain in development and maintenance **when a standard convention is not
followed.** **** While dwelling a little deeper into this separation of
concerns on the client and unobstructive programming, it helps to
determine what each of the piece of code is responsible for. Although it
is clear that javascript clearly takes care of behavior and html
strictly takes care of view, more clarity could be arrived when relating
it with MVC pattern. In the examples above the html part clearly defines
the view. It is the javascript which actually confuses. Putting MVC into
place, we should be able to relate to the script and determine which
performs the controller like behavior and which part performs the Model
like behavior. I am sticking with MVC **'like'** behavior because i know
it is not exactly the MVC. While some flavor of MVVM (knockout ) is
fairly visible from those examples, I would say it is more in line with
MVC. Though the Models are not exactly domain models, which it need not
be, because we are working on the browser part of the app. I would still
call the ListViewModel object as Model interms of MVC. So to separate
and relate them the html is the View in MVC the implementaiton of
ListViewModel is the Model in MVC while the piece of code that relates
the view and model can be thought of as Controller in MVC With this
understanding in mind and with some convention we can easily achieve
complete separation of html and java script from the developers
perspective as well. Please note - I have tried to stay away from saying
whether unobstructive web development is good or not. Nor from arriving
at conclusions of whether the latest frameworks like angular or knockout
achieves full separation of behavior and views. I do understand that the
definition of view and behavior itself is very thin and such frameworks
have their own way of taking them. Nevertheless, the new framework
definitely help us achieve better and clean web development.
