---
layout: post
title: "Developer Note: 2026 Jan 22"
date: 2026-01-22 19:48 -0600
author: itsrealfake
tags: ["update", "core_explore_kit"]

---

Listening to the robot too hard.


Cutting and pasting. they tell you not to do it... but sometimes we do it anyway.

Today i was trying to get us (re) launched on our rad hosting provider (we'll see if they wan the credit and maybe edit this into a link later)

We've found ourselves debugging with chatgpt and that leaves us with a lot of cut and paste commands. whoops.

The tool has a route to import all git data as a first step for data initialization, and needs the user to have already provided a `.git` folder in the user supplied directory... docker mounts that, it's tedious & working... 

But we only imported one commit. what the f? 

![fa455d7e077069496faad8208f261478.png](/assets/2026-01-22/fa455d7e077069496faad8208f261478.png)

Well, it turns out we copied our repo for analysis too shallow. Much like our analysis of the code we copy pasted. Oh well.. keep moving.

![07c989bc0c42c89cde29653bb0a51a8d.png](/assets/2026-01-22/07c989bc0c42c89cde29653bb0a51a8d.png)

Now that we've found the bug, we're fixing it & reimporting... 

`match (a:ImportStatus) set a.git_import_complete = false` allows us to reimport. the existing nodes may be merged, or it might break.



So that was an interesting bugfix. Thanks robots.
