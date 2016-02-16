---
title: "Fast development with Java Play"
tags: [play-framework]
---

Currently, I work in a project where we use the [Play framework][play] from [Typesafe][typesafe]. I'm really impressed how fast we develop our web application. Actually, after generating the project over the console

{% highlight bash %}
$ play new myFirstApp
{% endhighlight %}

you ride away start developing your domain stuff. I'd say, if you start with some J2EE monster which is heavily configure able, until you have all that what the [Play framework][play] offers you, it'll take probably two weeks to set up your framework until you can start.

Here is some all included stuff the [Play framework][play] gives you for free:

* Code generation
* ORM
* switch between in-memory database H2 for development and your real production database
* scala based view templating (no xml)
*


[play]: https://www.playframework.com/
[typesafe]: https://www.typesafe.com/
