---
title: "Rust Structs + Method syntax"
date: 2022-05-28T22:44:00+01:00
draft: false
description: "Usefulness of method syntax and impl blocks in rust"
tags: ["rust"]
---

Huh, finished Rust's guide section on structs and method syntax, and found some really neat things.
The first one was the ```impl``` blocks


    ...
    impl Rectangle {
        fn area(&self) -> u32 {
            self.height * self.width
        }
        ...
    }
    ...

Love the organization and readability. It allows to somewhat separate the struct from its methods, and also define them, without needing separate files like C++ (looking at you, header files).

The ```self``` keyword was a bit strange at first. I'm used to just access the struct members directly with a dot or ```->```, so having a dedicated parameter for it feels very foreign. But I can see the value in it, even if it's to tell whether the method will only read, mutate or consume whatever it receives as parameter.

Another strange thing was how I can ```instanceOfObject.method()```. Since the method is declared a ```method(&self)```, I would expect at first to have to use ```method(&instanceOfObject)```. But apparently not, the firstly mentioned way is accepted in Rust. Not that I'm complaining, feels a lot more readable, but the declaration does not initially suggest that.

This lesson unintentionally made me finally interiorize what borrowing and ownership mean, and how I might want to use that on my projects.