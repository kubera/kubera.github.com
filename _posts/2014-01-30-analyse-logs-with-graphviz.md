---
title: "Analyse logs with Graphviz"
tags: [graphviz, play-framework]
---

A swiss health insurance has some problems with there telephone system. They are loosing calls and noboy knows why. That system logs a lot and it's really hard to get information from there. There are state of a call like _initialized, queued, connected_ unordered and mix with other calls.

I started visualize the states with [Graphviz][graphviz]. There we found out that a call is divided in serveral sequences. This visualisation helps us a lot to understand better what's going on. 

![analyse result](/images/blog/2016-01-30-dependency-tree.dracula.png)

So I implemented an java application with the [Play framework][play] which collects the logs and identifies the complete calls with start and end time. The image above shows such a call with all its states. This made it possible to finaly see and examin all the incoming calls of the company. 


[graphviz]: http://www.graphviz.org 
[play]: http://playframework.com 
