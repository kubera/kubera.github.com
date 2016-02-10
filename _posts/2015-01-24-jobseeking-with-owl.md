---
title: "Jobseeking with OWL"
tags: [reasoning, protege]
---

In the current [CTI science project][kti], we are testing [OWL][owl] and the possibility to classify objects. The idea is to find the right candidat, a job seeker, for a certain vacancy.

![Setup jobseeker](/images/blog/2015-01-24-stefanwagner.png)

The first screen shows a demo of the setup of the _jobseeker OWL ontology_. There are two job seekers _Peter Muster_ with the property _hasSkill_ set to _some CSharp_ and _Stefan Wagner_ with _hasSkill_ set to _some Java_.

![Demo Vacancy](/images/blog/2015-01-24-vacancy1.png)

Now we see an open position _Vacancy1_ which has a so called _necessary and sufficient_ condition _Job and (hasSkill some Java)_. This setup makes it possible for a [reasoner][reasoner] to determine which vacancy has a possible candidate.

![Reasoning](/images/blog/2015-01-24-inferred.png)

On the last screen, I called the reasoner to classify. The result is that _StefanWagner_ was classified to be a sub class of _Vacancy1_.

This is the simplest use-case. In real, there would be many more job seekers, vacancies and skills. The point is that the machine can assign candidates to an open position by itself out of a model.

I used [Protégé][protege] to model this example but you can also use a java library like [Apache-Jena][jena] or the [OWL-API][owlapi] in our source code.

[kti]: https://www.kti.admin.ch/kti/de/home.html
[owl]: https://www.w3.org/2007/OWL/wiki/OWL_Working_Group
[reasoner]: https://en.wikipedia.org/wiki/Semantic_reasoner
[protege]: http://protege.stanford.edu/
[jena]: https://jena.apache.org/
[owlapi]: http://owlapi.sourceforge.net/
