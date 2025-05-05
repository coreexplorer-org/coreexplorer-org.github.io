---
layout: post
title: 'Repo Explorer: progress update'
date: 2024-04-13 00:00 +0000
author: itsrealfake
category: "progress update"
tags: ["update", "repo_explorer"]
---


## Facts we should derrive:

Given these desired calculations:
1) % of commits per year by contributor
   - (# of commits by contributer this year) / # of commits this year
     - find all commits this year
     - find all committers this year
     - for each committer, count how many commits they have in the year and divide by the number of commits
2) overall % of commits by maintainers
   - TODO find list of maintainers, and the start-date & end-date of their maintainership
     -   Will this be a tad complicated, due to the guy who changes his name a lot?
3) overall % of commits by non-maintainers (breakdown for self-merges)
   - Relies on the question of whether a committer is a maintainer on a given date
4) % PR merged per contributor (PRs merged / total opened)
5) closed rate per contributor (PRs closed / total opened)
below here added later
6) % of PRs merged per maintainer
   - pending

We need these facts:

- Contributor commits / year (implemented)
- Contributor is Maintainer on Commit Date (working on this)
- PR opened per contributor (implemented)
- PR merged per contributor (wat?)
- PR closed per contributor (pending)
- who merged the PR (implemented)
- who authored the PR (implemented, but could be refined with a list of identity/author_name pairs)

Note: maintainers can be derived from this list:https://github.com/bitcoin/bitcoin/blob/master/contrib/verify-commits/trusted-keys