---
title: "Independent Domain Model"
tags: [architecture, maven]
---

In the current project we made a design decision for our domain model to be independent of any concrete persistence technology. Because the persistence layer had to be replaceable to fit in any clients environment, we came to the conclusion that we had to define an API module for the persistence and an current temporary implementation of it.

![independent domain model](/images/blog/independent-domain-model.png)

The domain model is overall available, each module depends on it. Beside of representing the domain, it also acts as a data transfer object. The implementation of the persistence is capsuled behind a module of interfaces.

This structure has a major disadvantage: we lost all the comfort of JPA. Lazy loading, gone! We had to send all the associated data to the consumer.
