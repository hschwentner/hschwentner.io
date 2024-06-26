---
title: Heal Entity Anemia
---

<!-- ![](../../images/domain-driven-refactorings/YYY/XXXX.drawio.svg){: .align-center} -->

## Motivation

The anemic domain model is an anti-pattern that separates domain logic and domain data. In it, we typically find services and “data bags.” A “data bag” or anemic entity is a class that represent a domain concept and models all its data which it makes accessible via getters and setters. All the domain logic is placed in the services.

In such an architecture the anemic entities cannot ensure their consistency since they don’t encapsulate their data but expose it openly.

A group of smaller refactorings help to get rid of this model anemia and enrichen the entities with behavior.

Depending on what you do first—strategic transformation or tactical transformation—this is often a follow up to [Extract Specialized Anemic Entity](../tactical-for-strategic/extract-specialized-anemic-entity) or followed by [Extract Specialized Entity](../tactical-for-strategic/extract-specialized-entity).

## Mechanics

- Encapsulate data in the anemic entities with [Replace Setter](replace-setter) or [Remove Setter](remove-setter).
- Bring behavior to the entities with [Move Logic from Service to Entity](move-logic-from-service-to-entity).

## Example(s)
