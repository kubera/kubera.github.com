---
title: "Mavenize an Ant Application"
tags: [maven, ant, svn, git]
---

We're changing our modularized application at work from building and deploying with Ant to Maven. The requirements to that process is:

* my colleagues can go on working without being involved in that task
* not loosing any _svn_ history
* merge the whole task at once into trunk

The plan looks like this:

1. create a branch in _source control_
1. create new directories in `src` the maven standard `src/main/java` and add it to _source control_
1. move all source files `src/*` to `src/main/java/` and `src/main/resources/` with _source control_ not to lose any history
1. create the `pom.xml`
1. merge changes from colleagues to my branch
1. at the end, merge my branch back to trunk

I wanted to be sure that I won't have any disaster with the last steps to merge stuff together. I read about the weekness of _svn_ in merging branches. And indeed, I tried it and run into merge problems.  

So, what was needed is that I had to merge each module manually. Please!?!?

{% highlight bash %}
svn merge http://server/branch/module1/src/com src/main/java/
svn merge http://server/branch/module1/src/ src/main/resource/
svn merge http://server/branch/module1/test/com src/test/java/
svn merge http://server/branch/module1/src/ src/main/resource/
...
{% endhighlight %}

So I came up with the solution to use _git_ on the client site. I got the code from the _svn repository_, which I kept synchronized with _git master_:

{% highlight bash %}
git svn clone file:///some/repo -T trunk -b branches -t tags
{% endhighlight %}

I did my work on a _git branch_ and got the changes from my colleagues on _git master_ once in a while. At the end I merge _git branch_ with _git master_ and with _svn trunk_. Gotya!
