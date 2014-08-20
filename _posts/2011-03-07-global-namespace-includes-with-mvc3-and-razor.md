---
layout: post
title: Global Namespace Includes with MVC3 and Razor
date: 2011-03-07 22:10:21
categories: development
tags:
  - .net
  - mvc
  - razor
---

While I'm loving MVC3 and the Razor view engine, I was sorely disappointed when I couldn't use the `system.web/pages/namespaces` collection in `web.config` to add global namespace includes.

After a bit of hunting and looking through the web.config files underneath the views folder (in each Area), I found that this can be accomplished by adding the following to the root `web.config` file:

{% gist 6335507 %}

Now you can add any namespaces you require under the new razor namespaces section.
