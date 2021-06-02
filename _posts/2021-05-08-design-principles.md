---
title: Chapter 7 - Design Principles
author: Krishnanand Sivaraj
date: 2021-05-08 23:05:00 +0800
categories: [Design, Architecture]
tags: [ooad]
pin: false
---

## Chapter 7 : Design Principles

- The Open-Closed Principle keeps your software reusable, but still flexible, by keeping classes open for extension but closed for modification.
- With classes doing one single thing through the SRP, it is even easier to apply the OCP to your code.
- When you're trying to determine if a method is the responsibility of a class, ask yourself, is it this class's job to do this particular thing? If not, move the method to another class.
- Once you have your OO code nearly complete, be sure that you DRY.  You'll avoid duplicate code, and ensure that each behavior in your code is in a single place.
- DRY applies to requirements as well as your code: you should have each feature and requirement in your software implemented in a single place.
- The LSP ensures that you use inheritance correctly, by requiring that you use inheritance correctly, by requiring that subtypes be substitutable for their base types.
- When you find code that violates the LSP, consider using delegation, composition or aggregation to use behavior from other classes without resorting to inheritance.
- If you need behavior from another class but don't need to change or modify that behavior, you can simply delegate to that class to use the desired behavior.
- Composition lets you choose a behavior from a family of behaviors, often via several implementations of an interface.
- When you use composition, the composing object owns the behaviors from another class without limiting the lifetime of those behaviors.
- Aggregated behaviors continue to exist even after the aggregating object is destroyed.
