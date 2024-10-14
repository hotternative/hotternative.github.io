---
title: "Use git-crypt with multiple deployments"
date: 2022-11-27
---

Say you have a big repo that many engineers are collaborating on. 
Some should only have access to staging secrets, and some 
should have access to production secrets.


## Structure of the keys
Say you have a staging environment and a production environment, create a structure like this in your repo:
![example](/assets/git-crypt-structure.png)
``
