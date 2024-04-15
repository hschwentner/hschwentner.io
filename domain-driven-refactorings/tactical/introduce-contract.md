---
title: Introduce Contract
---

![](../../images/domain-driven-refactorings/tactical/introduce-contract.drawio.svg){: .align-center}

## Motivation

Every method (and every operation in general for that matter) can only operate under certain conditions. If we express these pre- and post-conditions in the code (following the idea of [Design by Contract](https://en.wikipedia.org/wiki/Design_by_contract)), we make that code both easier to understand and less error-prone.

Unfortunately, most programming languages support only a poor man’s DbC with assertions.

## Mechanics

- Document a method’s pre-conditions with [Introduce Assertion](https://refactoring.com/catalog/introduceAssertion.html).
- Document the method’s post-conditions with [Introduce Assertion](https://refactoring.com/catalog/introduceAssertion.html).
- Check if the class that contains the method follows invariants and document them with [Introduce Assertion](https://refactoring.com/catalog/introduceAssertion.html), too.
- For every condition: If it makes sense, introduce a predicate method that gives the check a name. If applicable use [Extract Method](https://refactoring.com/catalog/extractMethod.html) for that.
- Expose the predicate method by giving it the same visibility as the changed method.

## Example(s)
