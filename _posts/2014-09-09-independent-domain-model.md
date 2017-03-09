---
title: "Independent Domain Model"
tags: [architecture, maven]
---

In our  current project, we made a design decision for our domain model to be independent of any concrete persistence technology. Due to the fact that the persistence layer had to be replaceable in order to fit in any client environment, we came to the conclusion that we needed to define an API module for the persistence and a temporary or default implementation of it.

![independent domain model](/images/blog/2014-09-09-independent-domain-model.png)

The domain model is overall available, each module depends on it. Besides of representing the domain, it also acts as a _data transfer object_. The implementation of the persistence is capsuled behind a module of interfaces.

This structure has a major disadvantage: we lose all the comfort of JPA. Lazy loading, gone! We have to send all the associated data to the consumer.
