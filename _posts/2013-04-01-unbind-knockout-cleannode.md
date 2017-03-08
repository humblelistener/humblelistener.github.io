---
layout: post
title: "Unbind element in knockout using cleanNode"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2013-01-04
---

Unbind element in Knockout using cleanNode

Recently, I came upon this problem where my JavaScript events were firing multiple times,
I use both knockout and backbone in my application, where data-binding feature of knockout and Routing, &nbsp;Events, history, Model of backbone are being used.

Here are some gist of my code

My nav view model shown below, has a movePrevious event, that is where the event is being triggered
<div class="gistLoad" data-id="4455383" id="gist-4455383">
Loading ....</div>

By business view model handles the save group event as shown in the gist below
<div class="gistLoad" data-id="4455377" id="gist-4455377">
Loading ....</div>

Here, though the "saveGroup" backbone event is being turned off during dispose the event still seemed to be firing.

Further looking into my view, gist below
<div class="gistLoad" data-id="4455354" id="gist-4455354">
Loading ....</div>

you can see that my view uses knockout click binding.

Upon debugging the DOM element, I found that, for every time this view is being bound using ko.applyBinding the event is getting added to the dom element by knockout.

So, when I click on the hyperlink, the event is firing the number of times that view is bound to the view model.

To solve this, I have to unbind the view / DOM element every time before applying a fresh knockout binding.

Fortunately, knockout had this feature already that is available through ko.cleanNode function.

So, once I started calling this function every time before binding the view to view model the issue was fixed.

<b>Points to note:</b>
<ul>
<li>You have to unbind the DOM element / view every time before binding it with knockout again.</li>
<li>Turn off the Backbone events before you are about to lose the reference to your JavaScript object.</li>
</ul>

<b>References:</b>
While debugging this, I found <a href="http://lostechies.com/derickbailey/2011/09/15/zombies-run-managing-page-transitions-in-backbone-apps/">this wonderful article</a> that helped be understand the cleaning up required in javascript.

<script src="https://raw.github.com/moski/gist-Blogger/master/public/gistLoader.js" type="text/javascript"></script>
