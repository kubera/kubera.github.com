---
title: "Define your Architecture with Maven"
tags: [maven, architecture]
---

Maven is not just a build and dependency management tool, it also offers a way how to define the architecture of your software. You can have your modules in layers like a presentation, a business-logic and a persistence layer.

Lets suppose your architecture looks like the following image.

![Athene Architecture][athene-architecture-image]

The maven root _pom.xml_ defines the layers and the domain model, which is accessible on all layers.

{% highlight xml %}
<project>
 ...
 <modules>
  <module>athene-domain</module>
  <module>athene-service</module>
  <module>athene-ui</module>
  <module>athene-store</module>
 </modules>
 ...
</project>
{% endhighlight %}

Now, you can define layer specific dependencies in a layer _pom.xml_. With this possibility your root _pom.xml_ will be less crowded. I experienced projects where the root _pom.xml_ was totally full with declaration that it was hard to read the file.

{% highlight xml %}
<project>
 <modelVersion>4.0.0</modelVersion>
 <parent>
  <groupId>ch.fhnw.business.iwi</groupId>
  <artifactId>athene</artifactId>
  <version>1.0.0</version>
 </parent>

 <artifactId>athene.service</artifactId>
 <name>Athene Business Layer</name>
 <description>Athene Business Layer</description>
 <packaging>pom</packaging>

 <modules>
  <module>athene-service-model-api</module>
  <module>athene-service-concept-api</module>
  <module>athene-service-model</module>
  <module>athene-service-view</module>
  <module>athene-service-concept</module>
 </modules>

 <dependencyManagement>
  <dependencies>
   <dependency>
    <groupId>org.apache.jena</groupId>
    <artifactId>jena-core</artifactId>
    <version>3.0.1</version>
   </dependency>
  </dependencies>
 </dependencyManagement>

 <dependencies>
  <dependency>
   <groupId>org.springframework</groupId>
   <artifactId>spring-core</artifactId>
  </dependency>
 </dependencies>
</project>
{% endhighlight %}

The main structure looks as following. The source is available [here](https://github.com/kubera/athene/).

    athene
    ├── athene-domain
    │   └── src
    │       └── main
    │           └── java
    │               └── athene
    │                   └── domain
    ├── athene-service
    │   ├── athene-service-concept
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── athene
    │   │                   └── service
    │   │                       └── concept
    │   ├── athene-service-concept-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── athene
    │   │                   └── service
    │   │                       └── concept
    │   │                           └── api
    │   ├── athene-service-model
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── athene
    │   │                   └── service
    │   │                       └── model
    │   ├── athene-service-model-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── athene
    │   │                   └── service
    │   │                       └── model
    │   └── athene-service-view
    │       └── src
    │           └── main
    │               └── java
    │                   └── athene
    │                       └── service
    │                           └── view
    ├── athene-store
    │   ├── athene-store-api
    │   │   └── src
    │   │       └── main
    │   │           └── java
    │   │               └── athene
    │   │                   └── store
    │   │                       └── api
    │   └── athene-store-graph
    │       └── src
    │           └── main
    │               └── java
    │                   └── athene
    │                       └── store
    │                           └── graph
    └── athene-ui
        ├── athene-ui-concept
        │   └── src
        │       └── main
        │           └── java
        │               └── athene
        │                   └── ui
        │                       └── concept
        ├── athene-ui-metamodel
        │   └── src
        │       └── main
        │           └── java
        │               └── athene
        │                   └── ui
        │                       └── metamodel
        └── athene-ui-model-oryx
            └── src
                └── main
                    └── java
                        └── athene
                            └── ui
                                └── model
                                    └── oryx




[athene-architecture-image]: /images/blog/2011-05-03-athene-architecture.png "Athene Architecture"
