---
title: "Automation, automation, automation ..."
tags: [maven, jenkins, ansible, git, svn, stash, ant, websphere, jenkins, nexus, ansible]
---

I was hired to make some changes in an old J2EE application, which actually was very nice designed, state of the arte at its time but the company never updated the base technologies. It lied on EJB 2.1 with giant XML configuration files, Toplink ORM and Ant as the build system. The deployment was fully manual.

I was able to convince my client to invest in some automation. Manual periodic work is *error-prone and boring*. 

The deployment looked like this before:

![manual deployment](/images/blog/2017-01-15-nwm-old-world.png)

1. a developer made some changes to the code base, after he made a code review on his desk, or he didn't ...
2. he commited the changes to SVN
3. now he had to build the whole thing with Ant, twice, because of some cross-over dependencies, there were actually two application in this package; the then the same build again for the batch application which contained similar modules; well and building again the same EARs with the source files
4. then manual deployment on the development environment with the websphere administrator console
5. then shipping the EARs and lots of other documents to operation
6. OM did the some again for the test environment (after approval, they shipped it to the external operation for the integration and production environment); cool, isn't it?

For an developer who has seen an automated world, this was no acceptable state for the application we worked with. 

So I got some budget to make my changes as I know from other project, nothing fancy, just the usual java defaults:

![automated deployment](/images/blog/2017-01-15-nwm-continuous-integration-flow.png)

The new world looks as followed: 

1. a developer implements his tasks on a feature branch based on Git
2. he creates a pull-request with Stash, a colleague does the review
3. the second developer has to approve the pull request
4. the code gets merged to the develop branch
5. a hock triggers a build on Jenkins
6. Jenkins gets the latest state from develop branch and builds the artifacts including running very few unit tests
7. artifacts get stored in Nexus
8. in the night, the deployment gets triggered from Jenkins to Ansible 
9. Ansible gets the latest Websphere configuration for our application
10. Ansible gets the latest snapshot artifacts
11. the applications get installed on Websphere and started

That's the way we want to work, right?
