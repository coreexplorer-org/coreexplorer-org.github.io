---
layout: post
title: Trying to avoid recursive search of commits
date: 2024-04-25 00:00 +0000
author: itsrealfake
---

i think maybe i'm trying too hard to avoid a recursive search of all the commits in a given "merge Bitcoin/bitcoin" when determining if we have a "self-merge"... who knows?

Here we have a commit 4b1196a9855dcd188a24f393aa2fa21e2d61f061 
(identified by our test as a "maybe self merge")


![](/assets/screenshots-2024-04-25/list-packets.png)

today we used `gpg list-packets` to find the fingerprint, and couldn't find that number in the trusted keys... so we spiraled some and decided maybe this was too hard to figure out the way we were trying. we came up with another method that might be easier (@Juan Galt has the note on that).

it's challenging to find a value in the Trusted Key list that is included in a result from using gpg to verify a signature.

![](/assets/screenshots-2024-04-25/trusted-keys.png)

after wrapping up our call for today, i was looking at these outputs, and i see that the GOODSIG value of gpg list-packets printed "2EEB9F5CC09526C1" which is also present in the output of `git verify-commits`.

![](/assets/screenshots-2024-04-25/verify_raw_commit.png)

so we can at least look at all the signatures of the merge commits, and see if we find the key-id that matches one of the key-id for a trusted-key, which would give us a perfect answer to the "is self merge"

grumble... do we have to do a recursive search of every author of every commit in a merge? that is a pain.

are we missing something that we could see by zooming out?

thoughts?