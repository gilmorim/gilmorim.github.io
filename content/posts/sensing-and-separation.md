---
title: "Sensing and Separation"
date: 2025-02-15T16:53:28Z
draft: false
---

Sensing:
- Break dependency to sense where code breaks (as in, cannot compute or access values).

Separation:
- For when we can't even get a piece of code into a test harness

Techniques for sensing:
- Fake collaborators (fake classes that can be used instead of the real class) - replace real black boxes with a fake object. If it is impossible, use the real one.
- For non-object oriented languages, define a method that stores data on a global variable, and then the test code can read it.
- Mocks - fakes that assert predicates on their logic.