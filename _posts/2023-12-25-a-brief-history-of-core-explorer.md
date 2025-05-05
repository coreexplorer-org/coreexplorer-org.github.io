---
layout: post
title: A Brief History of Core Explorer
date: 2023-12-25 00:00 +0000
tags: ["historical stuff", "reference"]
---

This post is being updated as the story unfolds for us... and we're just starting to write these details in a public way, so bear with us. or don't. this is an increasingly less rough draft.

## Original process started a bit before Dec 2023

We had the hope that we could quickly and easily get an MVP off the ground.

> To create a website that gathers and displays core development data in Bitcoin, in a way that helps non technical Bitcoiners identify health or lack there of in Bitcoin core development. Some of the ideas around open source health include the amount of review per code base merged, how much code is being merged only after self review, and whether there are small groups of core devs engaging in what may be self serving or in group preference behaviour, and to what degree that is happening.

### What came before us? What motivated us to do this? 

- An old report, titled "[State of the Repo](https://github.com/bitcoin/bitcoin/issues?q=is%3Aissue+practicalswift+is%3Aclosed+%22State+of+the+repo%22)" was written by [practialswift](https://github.com/practicalswift) for some time.
- [Bitcoin Core Contributor Challenges](https://blog.lopp.net/bitcoin-core-contributor-challenges/) by [@lopp](https://x.com/lopp)
- In 2022 Wladimir van der Laan [resigned, named no successor](https://protos.com/bitcoins-longest-serving-lead-maintainer-calls-it-quits-names-no-successor/)
- A lot of the [OG Core Devs were sued by CSW](https://bitcoinnews.com/legal/craig-wright-1-trillion-lawsuit/) (who you might no better as Not Satoshi)

### What we wanted to explore

Initially, we had some objectives to satisfy our curiousity:
- % of commits per year by contributor and overall % by maintainers vs non maintainers with a sub breakdown for self merges
- Also % PR merged and closed rate per contributor (PRs merged or closed / total opened). Highly correlated with staying motivated and long term activity
- Detecting "[Self Merges](/definitions/self-merges)"
    - Especially self merges which have no ACKs
- [Authors vs. Committers](/definitions/author-and-committer)


### Inspriring bits and things we've seen along the way

- A [pretty visualization](https://x.com/fedimint/status/1775185775769833927) of Fedimint's contributions.
- Open dissent about the BIP process on [the socials](https://xcancel.com/francispouliot_/status/1774976931231830327?s=19)
- 


## What we have learned

It's hard to express how much we've learned since beginning to dig into this project. They say that "bitcoin is a type of rabbit hole", and I tend to agree. What's peculiar about it though, is the way that it branches. Wherever you look, it goes that way... seemingly endlessly.

"Bitcoin" is a protocol, and you can explore the BIPs or the history of money. And there are a number of applications that implement the protocol, or variations of it, with differential mempools and sometimes consensus breaking changes. Some of those applications are developed in repositories on Github (owned now by Microsoft).

### Github Organizations which impact "Bitcoin"

There's the ["Bitcoin" org repositories](https://github.com/orgs/bitcoin/repositories).

But there's also the ["Bitcoin Core" organization's repositories](https://github.com/orgs/bitcoin-core/repositories). This is where the devtools ([bitcoin-core/bitcoin-maintainer-tools](https://github.com/bitcoin-core/bitcoin-maintainer-tools)) exist for releasing "Bitcoin Core" which is an application that's supposed to be a reference implementation of the Bitcoin Protocol.


If you're used to writing code with others, and coordinating your efforts in a remote `git` repository (like Github), it might surprise you to learn **Bitcoin Core does not use the merge button**. 

### What's the process to update `bitcoin/bitcoin`?

### Some tidbits of knowledge that were helpful to us at the outset

> If helpful, to recap there can be multiple authors, and usually multiple ACKs, of a PR but normally only one maintainer who does the merge

> The merge script merges the PR branch onto the master branch, scheduled for release. and some commits have multiple authors (“Co-authored-by: name <email>” in the last lines of the commit message body)

> Or commits by different people in the same PR

> Merges are extremely rarely implementations of BIPs

> Definitely important to keep separate stats on merge commits vs normal commits


The script that makes the merge commit, makes the commit on behalf of the maintainer... and the name of the person who actually merged the code. Then the code is shared out as a magnet link.

But we noticed also, the commit & merge commit author, is already tracked.. ACK is not tracked... Merges currently appear as Commits (collections of Commits), and are not disambiguated.

Here's an example of a [merge commit](https://github.com/bitcoin/bitcoin/commit/e1e1e708fa0fbc0c51460305da5d401ed8f218f3)

And the merge commit message. This will become important later.

```
Merge bitcoin-core/gui#125: Enable changing the autoprune block space size in intro dialog
415fb2e GUI/Intro: Move prune setting below explanation (Luke Dashjr)
2a84c6b GUI/Intro: Estimate max age of backups that can be restored with pruning (Luke Dashjr)
e2dcd95 GUI/Intro: Rework UI flow to let the user set prune size in GBs (Luke Dashjr)
f2e5a6b GUI/Intro: Abstract GUI-to-option into Intro::getPrune (Luke Dashjr)
62932cc GUI/Intro: Return actual prune setting from showIfNeeded (Luke Dashjr)

Pull request description:

  ![Screenshot_20200911_095102](https://user-images.githubusercontent.com/1095675/92933661-0c4cea00-f436-11ea-9853-2456091ffab3.png)

  Moved from #18728

ACKs for top commit:
  ryanofsky:
    Code review ACK 415fb2e. Changes since last review: mb/gib suffixes, constexpr QOverload expected_backup_days tweaks, new moveonly layout commit
  jarolrod:
    Tested ACK 415fb2e.
  Talkless:
    tACK 415fb2e, tested on Debian Sid with Qt 5.15.2.
  hebasto:
    ACK 415fb2e, my unresolved comments are not blockers, and they could be resolved in follow ups.

Tree-SHA512: bd4882a9c08e6a6eb14b7fb6366983db8581425b4949fea212785d34d8fad9e32fb81ca8c8cdbfb2c05ea394aaf5a746ba2cf16623795c7252c3bdb61d455f00
```

### Maintaining the maintainers list (TODO)

Bitcoin Core has maintainers... but what is a maintainer?

The definition of bitcoin core maintainer is an interesting one to define. As there is a difference between what they are supposed to be (a service-based janitorial role) versus being gatekeepers and even rulers.

### Builder Keys

Builder Keys are kept in [this list](https://github.com/bitcoin-core/guix.sigs/tree/main/builder-keys)

Here's [the history of "trusted keys" of maintainers for bitcoin](https://github.com/bitcoin/bitcoin/commits/master/contrib/verify-commits/trusted-keys).

### Deadends

We found some deadends too... as the tools have evolved, [people had questions that weren't answered](https://github.com/bitcoin/bitcoin/commit/59ebee3fb4181baf20fab263cf1b587ece1bd5e2#commitcomment-126211284).

