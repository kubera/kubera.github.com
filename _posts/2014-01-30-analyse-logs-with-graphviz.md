---
title: "Analyse logs with Graphviz"
tags: [graphviz, play-framework]
---

A swiss health insurance has some problems with their telephone system. They are loosing calls and nobody knows why. That system logs a lot and it’s really hard to get information from there. There are state of a call like _initialized, queued, connected_ unordered and mix with other calls.

I started to visualize the states with [Graphviz][graphviz]. There we found out that a call is divided in several sequences. This visualisation helps us a lot to understand better what’s going on.

![analyse result](/images/blog/2014-01-30-log-analysis.png)

So I implemented a java application with the [Play framework][play] which collects the logs and identifies the complete calls with start and end time. The image above shows such a call with all its states. This made it possible to finally see and examine all the incoming calls of the company. 


[graphviz]: http://www.graphviz.org 
[play]: http://playframework.com 
