---
title: "Approaches to changing existing code"
date: 2025-02-15T15:44:58Z
draft: false
---

I currently find two approaches to change existing software: 1 - Edit and Pray, 2 - Cover and Modify.

For approach 1, the modus operandi is as follows:

- Identify the code that needs to be changed.
- Edit it.
- Run system, poke around and check behavior.
- See if it behaves as expected.
- Pray it did not break anything unintended.

For approach 2, it's a bit safer:
- Cover the upcoming new code by setting up a test harness.
- Modify the code.
- Run test.
- Run other existing tests to ensure no unexpected behavior was broken.

The goal is to move from approach 1 to approach 2, and unit tests are our best tool. They should benchmark at less than 100ms of execution, and allow for extremely fast implementation - feedback cycles. Provide easy debugging is a must too.

Unit tests cannot:
- Talk to a database.
- Communicate via network.
- Interact with the file system.
- Require editing configuration files.

Tests that validate these interaction are still worth performing, however not in the context of unit testing - they do not provide the extra quickness that unit tests do, and should have their own test battery (integration tests).

Dependency is a major problem in legacy software, and the solution involves the usage of techniques to break it.
It is key to be conservative when changing methods and classes to make them testable. It might be necessary to suspend our sense of aesthetics, and think of these changes as scars after a surgery 😊