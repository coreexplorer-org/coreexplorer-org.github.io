---
layout: post
title: 'Metrics of Repository Health'
date: 2024-02-04 00:00 -0000
category: "repository health"
authors: ["juansgalt"]
---

# Metrics for repository health

1. Self merge ratio: it is bad for the health of an open source project if there is a majority of merges to the code base that come from the same person who authored them. This risk can be mitigated by amount of reviews from other authors, which can be measured in `ACK`s
2. Number of ACKs from contributors: The amount of ACKs commented into the code discussion
3. Rank of contributor's ACK: ACKs per author could be weighted by the amount of commits and/or merges made by that author, so that the ACK process does not become trivial to game.
4. Per line index of self-merges: this index rates every line of code merged into the repository and ranks them based on whether they were self-merged or not
5. Heat map: worst form of self merge is one with zero "ACK"s in the comment section of the pull request. The healthiest form of merge is one where the author of the commit differs from the merger, and it has a high number of ACKs, many of which are from healthy and aged contributors.  The heat map would display the lines of code in colors based on quality of merges and reviews.