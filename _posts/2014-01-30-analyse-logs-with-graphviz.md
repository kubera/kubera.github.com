---
title: "Analyse logs with Graphviz"
tags: [graphviz, play-framework]
---

A swiss health insurance has some problems with their telephone system and keeps loosing calls. Nobody knows ther reason. The system logs a lot and it’s really hard to get information from there. There is a state of a call like _initialized, queued, connected_ unordered and mix with other calls.

I've started to visualize the states with [Graphviz][graphviz], where we've found out that a call is divided in several sequences. This visualisation helped us a lot to better understand what was happening.

![analyse result](/images/blog/2014-01-30-log-analysis.png)

Therefore I've implemented a java application with the [Play framework][play] that collects the logs and identifies the complete calls with start and end time. The image above shows such a call with all its states. This made possible to finally see and examine all the incoming calls of the company. 


[graphviz]: http://www.graphviz.org 
[play]: http://playframework.com 
