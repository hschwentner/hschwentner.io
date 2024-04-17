---
title: Remove Setter
---

*A special case of [Remove Method](https://refactoring.com/catalog/removeMethod.html)*

![](../../images/domain-driven-refactorings/tactical/remove-setter.drawio.svg){: .align-center}

## Motivation

Unfortunately, many programmers (and IDEs) tend to generate setters for all instance variables/fields. (See [Replace Setter](replace-setter) for reasons of that bad behavior.)

## Mechanics

- Find all calls to the setter.
- If there are none remove it.

**Warning:** you may not find all calls with static code analysis, as many frameworks rely on getters and setters to work their dynamic magic.

## Example(s)
