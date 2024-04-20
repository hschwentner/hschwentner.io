---
title: Extract Entity from Smart UI
---

*Special Case of [Separate Domain from Presentation](XXXXXX)*

![](../../images/domain-driven-refactorings/tactical/extract-entity-from-smart-ui.drawio.svg){: .align-center}

## Motivation

Smart UI is a pattern (in DDD considered an “anti-pattern,” see [Evans2004, p. 76]) that mixes up UI code and business logic. This refactoring helps to separate the two concerns.

## Mechanics

- In the smart UI class separate the business logic from the UI logic with [Extract Method](https://refactoring.com/catalog/extractMethod.html).
- Examine the extracted business logic method. Does it work on fields fom the class? Then this refactoring is right, if iorks only on its parameters, [*Extract Service from Smart UI*](extract-service-from-smart-ui) might fit better.
- Apply [Extract Class](https://refactoring.com/catalog/extractClass.html) and move the business logic and business data into the newly created entity.

## Example(s)
