---
title: "Define your Architecture with Maven"
tags: [maven, architecture]
---

I find it pretty cool how you can define the architecture of your software in maven. You can have your modules in layers like a presentation, a business-logic and a persistence layer.

Lets suppose your architecture looks like the following image.

![Athene Architecture][athene-architecture-image]

The root _pom.xml_ defines the layers and the domain model, which is accessible on all layers.

{% highlight xml %}
<project>
	<modules>
		<module>athene-domain</module>
		<module>athene-service</module>
		<module>athene-ui</module>
		<module>athene-store</module>
	</modules>
	...
</project>
{% endhighlight %}

The main structure looks as following. The source is available [here](https://github.com/kubera/athene/).

    athene
    ├── athene-domain
    │   └── src
    │       └── main
    │           └── java
    │               └── ch
    │                   └── fhnw
    │                       └── business
    │                           └── iwi
    │                               └── athene
    │                                   └── domain
    ├── athene-service
    │   ├── athene-service-concept
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── ch
    │   │                   └── fhnw
    │   │                       └── business
    │   │                           └── iwi
    │   │                               └── athene
    │   │                                   └── service
    │   │                                       └── concept
    │   ├── athene-service-concept-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── ch
    │   │                   └── fhnw
    │   │                       └── business
    │   │                           └── iwi
    │   │                               └── athene
    │   │                                   └── service
    │   │                                       └── concept
    │   │                                           └── api
    │   ├── athene-service-model
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── ch
    │   │                   └── fhnw
    │   │                       └── business
    │   │                           └── iwi
    │   │                               └── athene
    │   │                                   └── service
    │   │                                       └── model
    │   ├── athene-service-model-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── ch
    │   │                   └── fhnw
    │   │                       └── business
    │   │                           └── iwi
    │   │                               └── athene
    │   │                                   └── service
    │   │                                       └── model
    │   └── athene-service-view
    │       └── src
    │           └── main
    │               └── java
    │                   └── ch
    │                       └── fhnw
    │                           └── business
    │                               └── iwi
    │                                   └── athene
    │                                       └── service
    │                                           └── view
    ├── athene-store
    │   ├── athene-store-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── ch
    │   │                   └── fhnw
    │   │                       └── business
    │   │                           └── iwi
    │   │                               └── athene
    │   │                                   └── store
    │   │                                       └── api
    │   └── athene-store-graph
    │       └── src
    │           └── main
    │               └── java
    │                   └── ch
    │                       └── fhnw
    │                           └── business
    │                               └── iwi
    │                                   └── athene
    │                                       └── store
    │                                           └── graph
    └── athene-ui
        ├── athene-ui-concept
        │   └── src
        │       └── main
        │           └── java
        │               └── ch
        │                   └── fhnw
        │                       └── business
        │                           └── iwi
        │                               └── athene
        │                                   └── ui
        │                                       └── concept
        ├── athene-ui-metamodel
        │   └── src
        │       └── main
        │           └── java
        │               └── ch
        │                   └── fhnw
        │                       └── business
        │                           └── iwi
        │                               └── athene
        │                                   └── ui
        │                                       └── metamodel
        └── athene-ui-model-oryx
            └── src
                └── main
                    └── java
                        └── ch
                            └── fhnw
                                └── business
                                    └── iwi
                                        └── athene
                                            └── ui
                                                └── model
                                                    └── oryx




[athene-architecture-image]: /images/blog/Athene-Architecture.png "Athene Architecture"
