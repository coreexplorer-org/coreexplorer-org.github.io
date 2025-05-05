---
layout: page
title: Authors and Committers in Git
---

### What is the difference?

From [stackoverflow](https://stackoverflow.com/questions/18750808/difference-between-author-and-committer-in-git/18754896#18754896)

> The **Author** is the person who originally wrote the code. The **Committer**, on the other hand, is assumed to be the person who committed the code on behalf of the original author. This is important in Git because Git allows you to rewrite history, or apply patches on behalf of another person.

![](/assets/author_vs_committer.png)

### The default scenario

On your own PR you are by default both roles unless you 

- cherry pick someone else’s commit(s) 

- or explicitly pass an —author argument in your git commit command

-  or add one or more lines at the end of the commit body like Co-authored-by: <email> (in this last case you are still both roles and the coauthors are authors without being committers)