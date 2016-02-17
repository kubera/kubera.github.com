---
title: "Fast development with Java Play"
tags: [play-framework]
---

Currently, I work in a project where we use the [Play framework][play] from [Typesafe][typesafe]. I'm really impressed how fast we develop our web application. Actually, after generating the project over the console

{% highlight bash %}
$ play new myFirstApp
{% endhighlight %}

you right away start developing your domain stuff. I'd say, if you start with some J2EE monster which is heavily configurable, until you have all that what the [Play framework][play] offers you, it'd take probably two weeks to set up your application until you're able to start.

Here is some _all included_ stuff the [Play framework][play] gives you for free:

* Code generation
* ORM
* switch between in-memory database H2 for development and a _real_ database
* mechanism to easily insert development data into the database 
* scala based view templating (no xml)
* build and dependency framework 
* modularization 
* logging
* url mapping


[play]: https://www.playframework.com/
[typesafe]: https://www.typesafe.com/
