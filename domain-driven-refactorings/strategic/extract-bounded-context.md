---
title: Extract Bounded Context
#title: Carve Bounded Context out of Monolith
---

*Alternative to [Implement Bounded Context from Scratch](implement-bounded-context-from-scratch)*

![](../../images/domain-driven-refactorings/strategic/extract-bounded-context.drawio.svg){: .align-center}

## Motivation

A legacy system is full of domain knowledge that is probably documented nowhere else. Sometimes there’s is even no more domain expert who has this knowledge. To save that knowledge into the modern world, transform it into a new bounded context.

## Mechanics

- Analyze the domain to find out which bounded contexts should be there.
- Identify first carve-out candidate
- Apply the *Tactical 4 Strategic* refactorings that are right for your situation.

## Example(s)
