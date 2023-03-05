---
title: Implement Bounded Context from Scratch
---

*Alternative to [Carve Bounded Context out of Monolith](extract-bounded-context)*

![](../../images/domain-driven-refactorings/strategic/implement-bounded-context-from-scratch.drawio.svg){: .align-center}

## Motivation

When the idealized context map has been drawn and we know which bounded contexts we want to implement, for every bounded context, we can either carve it out or build if newly from scratch.

Implementing newly from scratch is the only possibility when the modernization is also moving to another language.
This happens, for example, often when a project moves from Cobol to Java or C#.

Building a bounded context from scratch risks losing domain knowledge that is hidden in the monolith. Also, such a bounded context may suffer from *second-system syndrome*.

## Mechanics

- Start with the idealized context map to know which bounded context and which relationships to other bounded contexts (and the monolith) have to be build.
- Choose the bounded context to carve out and assign a team with the [team patterns]().
- Implement a first prototype.
- Build the outer interface in the way that is right for other bounded contexts being in place.
- Add a connection layer to the monolith that behaves like the interface of the other (not yet carved-out) bounded contexts would do.

## Example(s)
