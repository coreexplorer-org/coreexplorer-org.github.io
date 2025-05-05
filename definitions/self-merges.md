---
layout: page
title: Self Merges
---

# What is a self merge?

A "self merge" is when the author of commits in a pull request is also the maintainer who runs the merge script.

## How can you detect them?

It's hard.

## Why do we think they're problematic

Fair question. We're concerned about bitcoin being [subverted](https://xcancel.com/LukeDashjr/status/1775559587787166056). There are plenty of reasons you might like to do that. One way could be through spoiling the codebase.

## What do they look like? 


### Example 1
Here's an [example of a Self Merge](https://github.com/bitcoin/bitcoin/commit/40310f5e8cd783a8114dc07224b435497bae6817)

`MarcoFalke` has merged two commits which were written by `MarkoFalke`. This is an example of a self merge.

[Commit 1](https://github.com/bitcoin/bitcoin/pull/21792)

```
Merge #21792: test: Fix intermittent issue in p2p_segwit.py
fad6269 test: Assert that exit code indicates failure (MarcoFalke)
faecb72 test: Fix intermittent issue in p2p_segwit.py (MarcoFalke)

Pull request description:

  Calling `start_node` might call `wait_for_rpc_connection`, which will fail.

  https://cirrus-ci.com/task/5669555591708672?logs=ci#L3504

  ```
    File "/tmp/cirrus-ci-build/ci/scratch/build/bitcoin-x86_64-pc-linux-gnu/test/functional/p2p_segwit.py", line 1974, in test_upgrade_after_activation
      self.start_node(2, extra_args=["-reindex", f"-segwitheight={SEGWIT_HEIGHT}"])
    File "/tmp/cirrus-ci-build/ci/scratch/build/bitcoin-x86_64-pc-linux-gnu/test/functional/test_framework/test_framework.py", line 508, in start_node
      node.wait_for_rpc_connection()
    File "/tmp/cirrus-ci-build/ci/scratch/build/bitcoin-x86_64-pc-linux-gnu/test/functional/test_framework/test_node.py", line 224, in wait_for_rpc_connection
      raise FailedToStartError(self._node_msg(
  test_framework.test_node.FailedToStartError: [node 2] bitcoind exited with status 1 during initialization

ACKs for top commit:
  jnewbery:
    ACK fad6269
  dhruv:
    ACK fad6269

Tree-SHA512: 4c5e39ce25e135717ea433258518f93f09d1c528c4538a8627d3da13bc0c0ba4b45911703c26392ff0f5e0cb7831a6c7cc53e6e29102d3da9c8cfce7cef333cc
```