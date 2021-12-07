# Domain-Driven Refactorings

Many legacy system suffers from model anemia, from being a big ball if mud, or from bad team organization. Most of them suffer from a combination of these diseases. Domain-Driven Design can help transform such systems into a healthier state.

In [@Fowler2019] many standard refactorings are described; [@Kerievsky20XX] shows how to refactor the patterns from [@Gamma1995].
On this page, I'm collecting refactorings that help to introduce patterns originally described in [@Evans2004], [@Fowler2004], and others.
The catalog is split into three categories:

- **Tactical Refactorings:** Change the inner implementation of a bounded context
- **Strategic Refactorings:** Help with splitting a monolith architecture into bounded contexts.
- **Socio-technical Refactorings:** Reorganize the teams. This is often enabled by and/or accompanying strategic refactorings.

In the descriptions I follow the classic Fowlerian format of Introduction/Motivation/Mechanics/Example(s).

## Big Bang Approach vs. Strangler Fig Application Approach


## The (Currently Evolving) Catalog

### Strategic Refactorings

- [Carve Out Bounded Context (out of Monolith)](strategic/carve-bounded-context-out-of-monolith)
- [Implement Bounded Context from Scratch (and Replace it in the Monolith)](implement-bounded-context-from-scratch)
- Carve Out Data Model First
- Carve Out Domain Model First

- Extract Shared Kernel From Entangled Bounded Contexts/Monolith (=> Mufrid)

### Socio-technical Refactorings (and Patterns)

- [Form Cross-Functional Team out of Layer-Team Members](socio-technical/form-cross-functional-team-out-of-layer-team-members)
- [Form Second Team out of Partly Layer-Team and First-Team Members](socio-technical/form-second-team-out-of-partly-layer-team-and-first-team-members)
- [Form Second Team out of Only Layer-Team Members](socio-technical/form-second-team-out-of-partly-layer-team-and-first-team-members)
- [Move Operations Team Member to DevOps Team](socio-technical/move-operations-team-member-to-devops-team)
- Assign Bounded Context to Existing (Cross-Functional) Team

- Give Core Domains to Best Team
- Give Every Team one Core Domain (and additional supporting)

### Tactical Refactorings

- [Enforce Ubiquitous Language](tactical/enforce-ubiquitous-language)
- [Replace Primitive with Value Object](tactical/replace-primitive-with-value-object)
- [Split Active Record into Aggregate and Repository](tactical/split-active-record-into-aggregate-and-repository)
- [Split Repository into Interface and Implementation](tactical/split-repository-into-interface-and-implementation)
- Combine Value Objects
- Replace Collection of Entities with Entity in Its Own Right (=> there is a relationship to *Encapsulate Collection*)
- Replace Collection of Entities with Repository
- Heal Entity Anemia
  - Remove Setter
  - Replace Setter with Domain-Named Method
  - Move Domain Logic from Service Down to Entity (=> *Move Statements into Function*, *Move Statements to Caller*)
- Introduce Contract (=> relationship to *Introduce Assertion*)

#### Tactical 4 Strategic

- Split Big Model into Two Small Models
- Replace Method Call with Domain Event

## Acknowledgement

![Flip chart of refactorings gathered at KanDDDinsky 2021](../images/domain-driven-refactorings/domain-driven-refactorings-kandddinsky.jpeg)

I thank the participants of the open space “Domain-Driven Refactorings” at [KanDDDinsky](https://kandddinsky.de/) 2021 conference.
