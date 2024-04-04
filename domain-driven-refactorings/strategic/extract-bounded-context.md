---
title: Extract Bounded Context
---

*Also known as: Carve Bounded Context out of Monolith*

*Alternative to [Implement Bounded Context from Scratch](implement-bounded-context-from-scratch)*

![](../../images/domain-driven-refactorings/strategic/extract-bounded-context.drawio.svg){: .align-center}

## Motivation

A legacy system is full of domain knowledge that is probably documented nowhere else. Sometimes there’s is even no more domain expert who has this knowledge. To save that knowledge into the modern world, transform it into a new bounded context.

## Mechanics

- Analyze the domain to find out which bounded contexts should be there.
- Identify first carve-out candidate.
- Apply the tactical refactorings for strategic transformation that are right for your situation. Often these are [Extract Specialized Entity](../tactical-for-strategic/extract-specialized-entity), [Extract Specialized Anemic Entity](../tactical-for-strategic/extract-specialized-anemic-entity), [Extract Specialized Service](../tactical-for-strategic/extract-specialized-service), and/or [Extract Specialized Table](../tactical-for-strategic/extract-specialized-table).

## Example(s)
