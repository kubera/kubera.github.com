---
title: "Modularize a Grails application"
tags: [grails, architecture]
---

I've just worked in a project where we upgraded a web application from grails 2.x to 3.x. One part of the application was divided into a plugin and three _slim_ grails applications, which kinda _inherited_ from this plugin. One of the grails applications was the official end user application and the other two where some kind of preview applications. We had some issues with this structure because plugins have the following disadvantage while development:

Grails | Application | Plugin
--- | --- | ---
enable/disable Javascript/CSS uglify/minify through asset-pipeline | ![check](/images/system/check.png) | ![check](/images/system/check.png)
do not pack all Javascript/CSS files into one (debugging in browser) | ![check](/images/system/check.png) | ![uncheck](/images/system/uncheck.png)
hot swapping / reload after file changes | ![check](/images/system/check.png) | ![uncheck](/images/system/uncheck.png)
debugging in IDE (Intellij Idea) | ![check](/images/system/check.png) | ![check](/images/system/check.png)
recompile TypeScript after file changes | ![check](/images/system/check.png) | ![uncheck](/images/system/uncheck.png)

We definitely needed hot swapping and separated JavaScript files while development. The solution was to make out of the plugin also a fully executable grails application.

I saw the [blog of Klaus Lehner][klaus-lehner-blog] and his conclusions of grails in bigger projects. In his article he says that you can't really modularize grails applications. With my experience of extending grails plugins to grails applications, I've developed an _prove of concept_ in an modularized web application with a frontend and backend and a common module for both of them. My use-case looks as following:

![examples dependency tree](/images/blog/2016-01-30-dependency-tree.dracula.png)

In order to have full comfort in development, as described above, the common, front and backend are grails plugins and grails applications. You are able to run each one. The main application bundles front and backend to one application. You can find the [code on github][grails-modular].
I used the layout example from [mrhaki][mrhaki] and split it into the three modules.

[klaus-lehner-blog]: https://www.catalysts.cc/diskussion/grails-in-large-projects-part-3/
[grails-modular]: https://github.com/kubera/grails-modular
[mrhaki]: http://mrhaki.blogspot.ch/2011/03/grails-goodness-applying-layouts-in.html
