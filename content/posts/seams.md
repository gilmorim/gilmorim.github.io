---
title: "Seams"
date: 2025-02-15T17:07:01Z
draft: true
---

Seam: A place where we can alter behavior without changing existing code (by adding new code, for example).

Tools such as "virtual" from C++, or interfaces from .NET allow for this:
- One override for production code.
- One override for test code.

Examples:
- The C preprocessor: use macros to redirect calls from unnecessary and complex methods to simpler ones.
- Use a class with same name on a different classpath/namespace.
- Using abstract types in argument lists, like .NET interfaces.

Types of seams:
- Preprocessing seam: on languages with a preprocessor, use a #define macro to override the production method call. Also define a compile time variable that will enable/disable the call.

- Link seam: create a stub third-party library that redefines or overrides cumbersome third-party calls. Define at compile-time which class shall be loaded.

Object seams:
- Create a virtual function on production code and have it be overridden on both test and production code, suiting production and test needs.
- Enabling point is at the the arguments list depending on which type was passed.

Sprout method:
- Find in the code where the changes are needed. If the change can be condensed in a single method, write the call to it and comment it out.
- Which variables from the original method are needed? List them as arguments to the commented method.
- With the method return things? If so, assign the return to a variable.
- Write the method, uncomment it and test it.

Notes:
- Can the method be written or is it so tightly coupled that I need to have it instantiate a ton of complex and heavy objects? If so, pass null as argument, or make it a static method.

Sprout class:
- New class that folds some complex logic into separate methods, each into its own responsibility that in the end can do the same as the original logic.

Steps:
- See where change needs to be done
- Write the code that would instantiate the sprout class
- See which variables would be needed from the original method/class and pass them as arguments
- If values need to be returned, add a method to the sprouted class that returns the data
- Create a test class for the sprouted class