# Domain-Driven Refactorings: LLM-Friendly Catalog

> Plain-Markdown, single-file version of the catalog at <https://hschwentner.io/domain-driven-refactorings/> by Henning Schwentner, for LLMs, coding agents and offline reading.
> The content is taken from the Markdown sources in `domain-driven-refactorings/`. The HTML pages remain the source of truth. If this file and a page disagree, the page wins.
> **Status:** work in progress, like the catalog itself. No refactoring has a worked example yet ("Example(s)" sections are empty on every page).

## How to use this file

- Every refactoring has the same fields: **ID**, **Category**, **URL**, **Also known as**, **Special case of**, **Alternative to**, **Related**, **Motivation** and **Mechanics**. A field that does not apply is omitted.
- **Mechanics** are numbered steps. Apply them in order.
- **IDs** are the URL slugs. Use them to refer to a refactoring unambiguously.
- To choose a refactoring, start from the [problem index](#problem-index). Then follow the [relationships](#relationships) to the smaller refactorings it is built from.
- Refactorings in Fowler's *Refactoring* catalog (Extract Class, Move Method, …) are referenced by name with a link to <https://refactoring.com/catalog/>. Database refactorings link to <https://databaserefactoring.com/>.

## Background

Different legacy systems suffer from different diseases and need different cures (the *Anna Karenina principle*). Many legacy systems suffer from one or more of these:

1. **Big ball of mud:** no one controlled the dependencies, and now everything is connected to everything else.
2. **Huge domain model:** the domain knowledge is entangled into one model whose parts fit together only partially or even contradict each other.
3. **Business and technical code are mixed:** replacing obsolete technology or extending the domain logic becomes a Herculean task.
4. **Unsuitable team structure:** people are organized in a way that prevents fast progress.

Carola Lilienthal and Henning Schwentner describe the treatments in the book *Domain-Driven Transformation* (Addison-Wesley, 2024). Performing the transformation requires *domain-driven refactorings*, collected in this catalog. They introduce patterns from Evans' *Domain-Driven Design*, Fowler's *Patterns of Enterprise Application Architecture* and others, in the same way that Fowler's *Refactoring*, Ambler/Sadalage's *Refactoring Databases* and Kerievsky's *Refactoring to Patterns* do for their patterns. Descriptions follow Fowler's format: Motivation, Mechanics, Example(s).

## Categories

| Category | Purpose |
|---|---|
| `strategic` | Split a monolith architecture into bounded contexts. |
| `tactical-for-strategic` | The smaller steps that strategic refactorings are built from. |
| `socio-technical` | Reorganize the teams. Often enabled by or accompanying strategic refactorings. |
| `tactical` | Strengthen domain knowledge in the code: change the inner implementation of a bounded context. |

## Catalog index

| ID | Name | Category | Page status |
|---|---|---|---|
| `extract-bounded-context` | Extract Bounded Context | strategic | described |
| `implement-bounded-context-from-scratch` | Implement Bounded Context from Scratch (and Replace It in the Monolith) | strategic | described |
| `extract-shared-kernel` | Extract Shared Kernel | strategic | described |
| `extract-specialized-service` | Extract Specialized Service | tactical-for-strategic | described |
| `extract-specialized-entity` | Extract Specialized Entity | tactical-for-strategic | described |
| `extract-specialized-anemic-entity` | Extract Specialized Anemic Entity | tactical-for-strategic | described |
| `extract-specialized-table` | Extract Specialized Table | tactical-for-strategic | described |
| `replace-method-call-with-domain-event` | Replace Method Call with Domain Event | tactical-for-strategic | described |
| `form-cross-functional-team-out-of-layer-team-members` | Form Cross-Functional Team out of Layer-Team Members | socio-technical | described |
| `form-enabling-team-out-of-layer-team-members` | Form Enabling Team out of Layer-Team Members | socio-technical | **TODO** (no page yet) |
| `form-second-team-out-of-partly-layer-team-and-first-team-members` | Form Second Cross-Functional Team out of Partly Layer-Team and First-Team Members | socio-technical | described |
| `form-second-team-out-of-layer-team-only` | Form Second Team out of Only Layer-Team Members | socio-technical | described |
| `move-operations-team-member-to-devops-team` | Move Operations Team Member to DevOps Team | socio-technical | described |
| `assign-context-to-existing-team` | Assign Bounded Context to Existing (Cross-Functional) Team | socio-technical | **TODO** (listed, no page yet) |
| `enforce-ubiquitous-language` | Enforce Ubiquitous Language | tactical | described |
| `replace-primitive-with-value-object` | Replace Primitive with Value Object | tactical | described |
| `combine-value-objects` | Combine Value Objects | tactical | **TODO** (listed, no page yet) |
| `heal-entity-anemia` | Heal Entity Anemia | tactical | described |
| `remove-setter` | Remove Setter | tactical | described |
| `replace-setter` | Replace Setter | tactical | described |
| `move-logic-from-service-to-entity` | Move Logic from Service to Entity | tactical | described |
| `introduce-contract` | Introduce Contract | tactical | described |
| `replace-collection-with-entity` | Replace Collection of Entities with Entity in Its Own Right | tactical | **TODO** (listed, no page yet) |
| `replace-collection-with-repository` | Replace Collection of Entities with Repository | tactical | **TODO** (listed, no page yet) |
| `split-active-record-into-aggregate-and-repository` | Split Active Record into Aggregate and Repository | tactical | described |
| `split-repository-into-interface-and-implementation` | Split Repository into Interface and Implementation | tactical | described |
| `extract-entity-from-smart-ui` | Extract Entity from Smart UI | tactical | described |
| `extract-service-from-smart-ui` | Extract Service from Smart UI | tactical | described |

## Problem index

Derived from the *Motivation* sections. "Problem" names the situation that the refactoring's motivation describes.

| Problem in the code or organization | Refactorings |
|---|---|
| Monolith should be split into bounded contexts; the legacy code holds undocumented domain knowledge | `extract-bounded-context` |
| Bounded context needed but the modernization also changes the programming language (e.g. COBOL → Java/C#) | `implement-bounded-context-from-scratch` |
| Parts of the model are needed by several contexts and should not be duplicated | `extract-shared-kernel` |
| A domain service is too big and partly belongs to the context being extracted | `extract-specialized-service` |
| A rich (behavioral) entity is too big and must be split between contexts | `extract-specialized-entity` |
| An anemic entity ("data bag") is too big and must be split between contexts | `extract-specialized-anemic-entity` |
| A database table is too big and must be split between contexts | `extract-specialized-table` |
| A method call couples two objects or contexts too tightly or synchronously | `replace-method-call-with-domain-event` |
| Bad, technical or abbreviated names that do not match the domain | `enforce-ubiquitous-language` |
| Primitive obsession: naked `int`s and `String`s for domain concepts | `replace-primitive-with-value-object` |
| Anemic domain model: entities with getters/setters, all logic in services | `heal-entity-anemia` → `replace-setter`, `remove-setter`, `move-logic-from-service-to-entity` |
| Generated setters that nobody calls | `remove-setter` |
| Setters used where a domain operation is meant | `replace-setter` |
| Service logic that works on a single entity and forces it to expose its data | `move-logic-from-service-to-entity` |
| Pre-/post-conditions and invariants are implicit | `introduce-contract` |
| A class both represents a domain concept and manages its storage (Active Record) | `split-active-record-into-aggregate-and-repository` |
| The domain layer knows about database access through the repository | `split-repository-into-interface-and-implementation` |
| UI code and business logic are mixed (Smart UI); logic uses the UI class's fields | `extract-entity-from-smart-ui` |
| UI code and business logic are mixed (Smart UI); logic uses only its parameters | `extract-service-from-smart-ui` |
| Teams organized by technical layer; a new bounded context needs one owning team | `form-cross-functional-team-out-of-layer-team-members` |
| A second cross-functional team is needed and the first team's experience should be transferred | `form-second-team-out-of-partly-layer-team-and-first-team-members` |
| A second cross-functional team is needed and the first team should stay undisturbed | `form-second-team-out-of-layer-team-only` |
| Deployments ping-pong between development teams and a separate operations team | `move-operations-team-member-to-devops-team` |

## Relationships

Stated on the source pages. `A → B` means "A is carried out using B" unless another verb is given.

- `extract-bounded-context` → `extract-specialized-entity`, `extract-specialized-anemic-entity`, `extract-specialized-service`, `extract-specialized-table` (choose the ones that fit)
- `extract-bounded-context` **alternative to** `implement-bounded-context-from-scratch`
- `extract-shared-kernel` **alternative or prerequisite to** `extract-bounded-context` and `implement-bounded-context-from-scratch`; afterwards proceed with `extract-bounded-context`
- `implement-bounded-context-from-scratch` → assign a team with `form-cross-functional-team-out-of-layer-team-members`, `form-second-team-out-of-layer-team-only` or `form-second-team-out-of-partly-layer-team-and-first-team-members`
- `extract-specialized-entity` **alternative to** `extract-specialized-anemic-entity` (rich model vs. anemic model); both often accompanied by `extract-specialized-table`
- `extract-specialized-anemic-entity` often **follows** `extract-specialized-service`, and is often **followed by** `heal-entity-anemia`
- `heal-entity-anemia` → `replace-setter`, `remove-setter`, `move-logic-from-service-to-entity`; follows `extract-specialized-anemic-entity` (strategic first) or precedes `extract-specialized-entity` (tactical first)
- `move-logic-from-service-to-entity` → then `replace-setter` or `remove-setter`
- `replace-setter` → `remove-setter` (if the setter is unused), then `introduce-contract`
- `split-active-record-into-aggregate-and-repository` often **followed by** `split-repository-into-interface-and-implementation`
- `extract-entity-from-smart-ui` **alternative to** `extract-service-from-smart-ui`
- `form-second-team-out-of-layer-team-only` **alternative to** `form-second-team-out-of-partly-layer-team-and-first-team-members`; both follow `form-cross-functional-team-out-of-layer-team-members`
- `move-operations-team-member-to-devops-team` often follows `form-cross-functional-team-out-of-layer-team-members`

---

## Strategic refactorings

### Extract Bounded Context

- **ID:** `extract-bounded-context`
- **Category:** strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/strategic/extract-bounded-context>
- **Also known as:** Carve Bounded Context out of Monolith
- **Alternative to:** `implement-bounded-context-from-scratch`

**Motivation.** A legacy system is full of domain knowledge that is probably documented nowhere else. Sometimes there is no domain expert left who has this knowledge. To save that knowledge into the modern world, transform it into a new bounded context.

**Mechanics.**

1. Analyze the domain to find out which bounded contexts should be there.
2. Identify the first carve-out candidate.
3. Apply the tactical refactorings for strategic transformation that are right for your situation. Often these are `extract-specialized-entity`, `extract-specialized-anemic-entity`, `extract-specialized-service` and/or `extract-specialized-table`.

### Implement Bounded Context from Scratch

- **ID:** `implement-bounded-context-from-scratch`
- **Category:** strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/strategic/implement-bounded-context-from-scratch>
- **Full name:** Implement Bounded Context from Scratch (and Replace It in the Monolith)
- **Alternative to:** `extract-bounded-context`

**Motivation.** When the idealized context map has been drawn and we know which bounded contexts we want to implement, each bounded context can either be carved out or built anew from scratch. Building from scratch is the only possibility when the modernization also moves to another language, which often happens when a project moves from COBOL to Java or C#. Risks: losing domain knowledge hidden in the monolith, and *second-system syndrome*.

**Mechanics.**

1. Start with the idealized context map to know which bounded context, and which relationships to other bounded contexts (and the monolith), have to be built.
2. Choose the bounded context to carve out and assign a team with the fitting socio-technical refactoring, e.g. `form-cross-functional-team-out-of-layer-team-members`, `form-second-team-out-of-layer-team-only` or `form-second-team-out-of-partly-layer-team-and-first-team-members`.
3. Implement a first prototype.
4. Build the outer interface in the way that is right for the other bounded contexts being in place.
5. Add a connection layer to the monolith that behaves like the interface of the other (not yet carved-out) bounded contexts would.

### Extract Shared Kernel

- **ID:** `extract-shared-kernel`
- **Category:** strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/strategic/extract-shared-kernel>
- **Alternative to / prerequisite of:** `extract-bounded-context`, `implement-bounded-context-from-scratch`
- **Acknowledgement:** idea by Mufrid Krilic

**Motivation.** The analysis of a monolith has identified one or several bounded contexts for extraction. Parts of the model are so common that they should not be duplicated. The common parts go into their own artifact, while the rest of the contexts are clearly separated.

**Mechanics.**

1. Identify the elements that shall be members of the shared kernel.
2. Create a new package/module for the shared kernel.
3. Move the elements to the new package/module. (The source page names the move refactoring only as a placeholder, "XXXX".)
4. After finishing the extraction of the shared kernel, proceed with `extract-bounded-context`.

---

## Tactical refactorings that support strategic refactorings

### Extract Specialized Service

- **ID:** `extract-specialized-service`
- **Category:** tactical-for-strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical-for-strategic/extract-specialized-service>
- **Also known as:** Carve Specialized Anemic Service Out of Monolithic Service
- **Special case of:** [Extract Class](https://refactoring.com/catalog/extractClass.html)

**Motivation.** As one step of `extract-bounded-context` you have found a domain service that has become too big. Its functionality belongs partly to the bounded context being extracted. The decision has been made to split it.

**Mechanics.**

1. Create an empty new class in the carved-out context.
2. Add an instance field of the new class's type to the old class.
3. Copy the first to-be-moved method to the new class with [Move Method](https://refactoring.com/catalog/moveFunction.html).
4. Replace the method body in the old class with a forward to the method in the new class.
5. Step by step, replace calls to the method in the old class with calls to the method in the new class.
6. Delete the implementation in the old class.
7. Repeat steps 3–6 with the other to-be-moved methods.
8. Remove the instance field of the new class's type from the old class.

### Extract Specialized Entity

- **ID:** `extract-specialized-entity`
- **Category:** tactical-for-strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical-for-strategic/extract-specialized-entity>
- **Also known as:** Carve Specialized Entity Out of Monolithic Entity
- **Special case of:** [Extract Class](https://refactoring.com/catalog/extractClass.html)
- **Alternative to:** `extract-specialized-anemic-entity` (use that one if the domain model is anemic)
- **Related:** often accompanied by `extract-specialized-table`

**Motivation.** As one step of `extract-bounded-context` you have found a monolithic domain model with an entity that has become too big. The decision has been made to split it.

**Mechanics.**

1. Create an empty new class in the carved-out context.
2. Add an instance field of the new class's type to the old class.
3. Copy the to-be-moved fields from the old to the new class with [Move Field](https://refactoring.com/catalog/moveField.html).
4. Copy the first to-be-moved method to the new class with [Move Method](https://refactoring.com/catalog/moveFunction.html).
5. Replace the method body in the old class with a forward to the method in the new class.
6. Step by step, replace calls to the method in the old class with calls to the method in the new class.
7. Delete the implementation in the old class.
8. Delete the now unused fields in the old class.
9. Repeat steps 4–8 with the other to-be-moved methods.
10. Remove the instance field of the new class's type from the old class.

### Extract Specialized Anemic Entity

- **ID:** `extract-specialized-anemic-entity`
- **Category:** tactical-for-strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical-for-strategic/extract-specialized-anemic-entity>
- **Also known as:** Carve Specialized Anemic Entity Out of Monolithic Entity
- **Special case of:** [Extract Class](https://refactoring.com/catalog/extractClass.html)
- **Alternative to:** `extract-specialized-entity` (use that one if the domain model is rich)
- **Related:** often follows `extract-specialized-service`; accompanied by `extract-specialized-table`; afterwards often `heal-entity-anemia`

**Motivation.** As one step of `extract-bounded-context` you have found a monolithic *anemic* domain model with an anemic entity (a "data bag") that has become too big. The decision has been made to split it.

**Mechanics.** Same steps as `extract-specialized-entity`:

1. Create an empty new class in the carved-out context.
2. Add an instance field of the new class's type to the old class.
3. Copy the to-be-moved fields from the old to the new class with [Move Field](https://refactoring.com/catalog/moveField.html).
4. Copy the first to-be-moved method to the new class with [Move Method](https://refactoring.com/catalog/moveFunction.html).
5. Replace the method body in the old class with a forward to the method in the new class.
6. Step by step, replace calls to the method in the old class with calls to the method in the new class.
7. Delete the implementation in the old class.
8. Delete the now unused fields in the old class.
9. Repeat steps 4–8 with the other to-be-moved methods.
10. Remove the instance field of the new class's type from the old class.

### Extract Specialized Table

- **ID:** `extract-specialized-table`
- **Category:** tactical-for-strategic (database refactoring)
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical-for-strategic/extract-specialized-table>
- **Also known as:** Carve Specialized Data Model Out of Monolithic Table
- **Special case of:** [Split Table](https://databaserefactoring.com/SplitTable.html)

**Motivation.** As one step of `extract-bounded-context` you have found a monolithic data model (often used to store a monolithic domain model) with a table that has become too big. The decision has been made to separate the parts for the newly extracted bounded context.

**Mechanics, schema update.**

1. Create an empty new table in the database schema of the carved-out context.
2. Copy the to-be-duplicated columns from the old to the new table.
3. Copy the to-be-moved columns from the old to the new table by repeatedly applying [Move Column](https://databaserefactoring.com/MoveColumn.html).
4. Introduce synchronizing triggers on both the monolithic and the carved-out table, invoked by any change to the data in either table. Beware of the triggers triggering each other.
5. Add a drop date to the triggers.

**Mechanics, data migration.**

1. Copy the data from the duplicated columns to the new table. Not all rows of the monolith necessarily belong in the carved-out bounded context.
2. Copy the data from the moved columns to the new table with [Move Data](https://databaserefactoring.com/MoveData.html).

**Mechanics, access programs.**

1. Analyze the accessing program code thoroughly and update it accordingly during the transition period.
2. If applicable, extract a specialized repository for the carved-out bounded context.

### Replace Method Call with Domain Event

- **ID:** `replace-method-call-with-domain-event`
- **Category:** tactical-for-strategic
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical-for-strategic/replace-method-call-with-domain-event>
- **Related:** similar to [Introduce Parameter Object](https://refactoring.com/catalog/introduceParameterObject.html)

**Motivation.** A method call causes relatively strong coupling: the caller has to know the called object, and the communication is synchronous. With a domain event, the caller no longer needs to know the called object; both sides know only the event. The interaction changes from giving an order to another object to informing it.

**Mechanics.**

1. Create a new class for the domain event. Choose the name carefully: because the direction changes, it will usually differ a lot from the name of the replaced method.
2. Add a field to the domain event for every parameter of the to-be-replaced method.
3. Subscribe the called class to the domain event. The subscribed event listener calls the method whose call is being replaced.
4. In the caller, replace the method call with publishing the event.

---

## Socio-technical refactorings

### Form Cross-Functional Team out of Layer-Team Members

- **ID:** `form-cross-functional-team-out-of-layer-team-members`
- **Category:** socio-technical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/socio-technical/form-cross-functional-team-out-of-layer-team-members>
- **Also known as (proposed on the page):** Form Stream-Aligned Team out of Layer-Team Members

**Motivation.** When teams are organized by technical layer, Conway's Law bites: even the smallest change usually involves several teams (adding one field means work for the UI, business-logic and database teams). After `extract-bounded-context` or `implement-bounded-context-from-scratch`, someone has to own the new bounded context. No layer team fits, because the context is a vertical slice with UI, business-logic and database parts, and a bounded context should not belong to more than one team. The solution is a new team with all the required knowledge: a *cross-functional* team.

**Mechanics.**

1. Choose at least one person from every layer team. Pick early adopters, not sceptics.
2. Form a new team of fewer than about nine people.
3. Let the new team take responsibility for the new bounded context.
4. In the new team, encourage a T-shaped skill profile and other agile techniques that break knowledge silos.
5. For the time being, leave the other teams organized as they are. The monolith is still there and has to be maintained.

### Form Second Cross-Functional Team out of Partly Layer-Team and First-Team Members

- **ID:** `form-second-team-out-of-partly-layer-team-and-first-team-members`
- **Category:** socio-technical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/socio-technical/form-second-team-out-of-partly-layer-team-and-first-team-members>
- **Alternative to:** `form-second-team-out-of-layer-team-only`
- **Follows:** `form-cross-functional-team-out-of-layer-team-members`

**Motivation.** A first cross-functional team exists. For the next team, either move someone from the first team into it, or leave the first team alone and staff the new team from layer teams. Advantage of this variant: the experience of the first change is carried into the second team. Disadvantage: the young first team is torn apart and goes through storming-forming-norming-performing again.

**Mechanics.**

1. Choose at least one person from the first cross-functional team. Pick the "teachers", people who like to pass knowledge to peers.
2. Fill up the second cross-functional team with members of the layer teams:
   - Check that all required knowledge is present. If no UI expert came from the first team, add someone from the old UI layer team.
   - Keep the team below about nine people.
3. Let the new team take responsibility for a new bounded context.
4. Leave the remaining teams organized as they are. They should already be shrinking significantly.

### Form Second Team out of Only Layer-Team Members

- **ID:** `form-second-team-out-of-layer-team-only`
- **Category:** socio-technical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/socio-technical/form-second-team-out-of-layer-team-only>
- **Alternative to:** `form-second-team-out-of-partly-layer-team-and-first-team-members`
- **Follows:** `form-cross-functional-team-out-of-layer-team-members`

**Motivation.** Same situation as the alternative. Advantages of staffing follow-up teams only from layer teams: existing cross-functional teams keep working undisturbed, and several new teams can be formed at once. Disadvantage: every new team learns the team change from scratch, because the people who already went through a reorganization stay in their team.

**Mechanics.**

1. Follow the mechanics of `form-cross-functional-team-out-of-layer-team-members`.

### Move Operations Team Member to DevOps Team

- **ID:** `move-operations-team-member-to-devops-team`
- **Category:** socio-technical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/socio-technical/move-operations-team-member-to-devops-team>
- **Related:** often follows `form-cross-functional-team-out-of-layer-team-members`; see *Team Topologies*

**Motivation.** There are cross-functional development teams, but operations is done by another team. Development hands its result to operations and hopes it reaches production. When deployment fails, the work goes back to development, and a game of ping-pong starts. DevOps avoids this by also integrating operations know-how into the development team. This refactoring moves the organization one step in that direction.

**Mechanics.**

1. Choose a first development team that wants to apply the DevOps idea.
2. Assign one of the operators to that team to form the first DevOps team.
3. Let the team members teach each other what they did not know so far, aiming for a T-shaped skill profile for both the developers and the operator.
4. Repeat until the former operations team has eventually been replaced.

### Form Enabling Team out of Layer-Team Members

- **ID:** `form-enabling-team-out-of-layer-team-members`
- **Status:** TODO. Listed in the catalog; no page yet.

### Assign Bounded Context to Existing (Cross-Functional) Team

- **ID:** `assign-context-to-existing-team`
- **Status:** TODO. Listed in the catalog; no page yet.

---

## Tactical refactorings that strengthen domain knowledge in the code

### Enforce Ubiquitous Language

- **ID:** `enforce-ubiquitous-language`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/enforce-ubiquitous-language>

**Motivation.** Whenever the code uses bad names, obscure technical names, strange abbreviations, or names that do not reflect the current understanding of the domain, change them. This is part of DDD's "Refactoring Toward Deeper Insight."

**Mechanics.**

1. In the source code, apply Rename Class, [Rename Method](https://refactoring.com/catalog/changeFunctionDeclaration.html), [Rename Field](https://refactoring.com/catalog/renameField.html), [Rename Variable](https://refactoring.com/catalog/renameVariable.html) and the like.
2. In the data model, apply [Rename Table](https://databaserefactoring.com/RenameTable.html), [Rename Column](https://databaserefactoring.com/RenameColumn.html) and [Rename View](https://databaserefactoring.com/RenameView.html).
3. Change the user interface accordingly.

### Replace Primitive with Value Object

- **ID:** `replace-primitive-with-value-object`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/replace-primitive-with-value-object>
- **Special case of:** [Replace Primitive with Object](https://refactoring.com/catalog/replacePrimitiveWithObject.html)

**Motivation.** Many systems use primitive types excessively for value-like domain concepts: naked `int`s and `String`s everywhere (Fowler's *Primitive Obsession* smell). Types of their own for these concepts make the code more expressive and less error-prone.

**Mechanics.**

1. Create a simple value object class.
2. Make sure the class is identity-less and immutable.
3. Step by step, use the new value class wherever a primitive type was used so far.
4. Where applicable, move domain logic into the value class (typically validation and arithmetic) with [Extract Method](https://refactoring.com/catalog/extractFunction.html), [Move Method](https://refactoring.com/catalog/moveFunction.html) and the like.

### Combine Value Objects

- **ID:** `combine-value-objects`
- **Status:** TODO. Listed in the catalog; no page yet.

### Heal Entity Anemia

- **ID:** `heal-entity-anemia`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/heal-entity-anemia>
- **Composed of:** `replace-setter`, `remove-setter`, `move-logic-from-service-to-entity`
- **Related:** follows `extract-specialized-anemic-entity` (strategic transformation first) or precedes `extract-specialized-entity` (tactical transformation first)

**Motivation.** The *anemic domain model* is an anti-pattern that separates domain logic from domain data. It consists of services plus "data bags": anemic entities that model a domain concept's data and expose all of it through getters and setters, while all domain logic lives in the services. Anemic entities cannot ensure their own consistency, because they expose their data instead of encapsulating it. A group of smaller refactorings removes the anemia and gives the entities behavior.

**Mechanics.**

1. Encapsulate the data in the anemic entities with `replace-setter` or `remove-setter`.
2. Bring behavior into the entities with `move-logic-from-service-to-entity`.

### Remove Setter

- **ID:** `remove-setter`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/remove-setter>
- **Special case of:** [Remove Method](https://refactoring.com/catalog/removeMethod.html)
- **Related:** `replace-setter`

**Motivation.** Many programmers (and IDEs) generate setters for all instance variables (see `replace-setter` for why that is bad).

**Mechanics.**

1. Find all calls to the setter.
2. If there are none, remove it.

**Warning:** static code analysis may not find all calls, because many frameworks rely on getters and setters for their dynamic magic.

### Replace Setter

- **ID:** `replace-setter`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/replace-setter>
- **Related:** similar to [Rename Method](https://refactoring.com/catalog/changeFunctionDeclaration.html); use `remove-setter` if the setter is unused; ends with `introduce-contract`

**Motivation.** Fields are private by default (Parnas's *information hiding*), but many programmers then add a getter and a setter for every field, which breaks the encapsulation again. IDEs and the JavaBeans convention encourage this. The getter may be acceptable; the setter causes serious problems. Instead, give classes methods that resemble domain behavior, named with verbs from the domain. *Set* is a verb that most domains do not use. Unlike a plain rename, the new method often adds business behavior beyond setting the field.

**Mechanics.**

1. Identify the setter to be replaced.
2. Model the corresponding business process with your domain experts to find the right name for the new method.
3. Introduce the new method into the class.
4. Find the calls to the setter.
5. Step by step, replace each call to the setter with a call to the domain-named method.
6. When all calls are replaced, remove the setter from the class.
7. Find out whether the new method has pre- and/or post-conditions and bring them into the code with `introduce-contract`.

### Move Logic from Service to Entity

- **ID:** `move-logic-from-service-to-entity`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/move-logic-from-service-to-entity>
- **Special case of:** [Move Method](https://refactoring.com/catalog/moveFunction.html)
- **Part of:** `heal-entity-anemia`
- **Catalog index note:** also described as "Move Domain Logic from Service Down to Entity" (cf. Fowler's *Move Statements into Function*, *Move Statements to Caller*)

**Motivation.** A domain service contains pure domain logic, which often operates on entities. If a piece of that logic operates on only one entity and forces the entity to expose its data, move it down into the entity. This increases the entity's cohesion and lets it encapsulate its data.

**Mechanics.**

1. Copy the method from the service to the entity. (The source page says "from entity to service"; the motivation and the following steps describe moving it from the service down to the entity.)
2. Change the implementation of the to-be-moved method in the service so that it just forwards to the method in the entity.
3. Identify the code that calls the method and check whether it makes sense for it to work on the entity directly. If yes, change it to call the method on the entity.
4. If no code calls the method in the service anymore, delete it.
5. Check whether you can now encapsulate the data and get rid of setters with `replace-setter` or `remove-setter`.

### Introduce Contract

- **ID:** `introduce-contract`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/introduce-contract>
- **Related:** follows `replace-setter`

**Motivation.** Every method can only operate under certain conditions. Expressing pre- and post-conditions in the code ([Design by Contract](https://en.wikipedia.org/wiki/Design_by_contract)) makes the code easier to understand and less error-prone. Most languages support only a poor man's Design by Contract with assertions.

**Mechanics.**

1. Document the method's pre-conditions with [Introduce Assertion](https://refactoring.com/catalog/introduceAssertion.html).
2. Document the method's post-conditions with Introduce Assertion.
3. Check whether the class containing the method has invariants, and document them with Introduce Assertion too.
4. For every condition, if it makes sense, introduce a predicate method that gives the check a name (use [Extract Method](https://refactoring.com/catalog/extractMethod.html) where applicable).
5. Expose the predicate method with the same visibility as the changed method.

### Replace Collection of Entities with Entity in Its Own Right

- **ID:** `replace-collection-with-entity`
- **Status:** TODO. Listed in the catalog; no page yet.
- **Related:** [Encapsulate Collection](https://refactoring.com/catalog/encapsulateCollection.html)

### Replace Collection of Entities with Repository

- **ID:** `replace-collection-with-repository`
- **Status:** TODO. Listed in the catalog; no page yet.

### Split Active Record into Aggregate and Repository

- **ID:** `split-active-record-into-aggregate-and-repository`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/split-active-record-into-aggregate-and-repository>
- **Related:** often followed by `split-repository-into-interface-and-implementation`

**Motivation.** An [Active Record](https://www.martinfowler.com/eaaCatalog/activeRecord.html) (from *Patterns of Enterprise Application Architecture*) does two things: it represents a domain concept, and it manages the storage of that concept. This refactoring separates the two responsibilities.

**Mechanics.**

1. Classify each method of the active record as domain logic or data-access logic. If a method mixes both, apply [Extract Method](https://refactoring.com/catalog/extractMethod.html) first.
2. Create a repository class and copy all data-access logic into it.
3. Mark all data-access methods in the active record as deprecated (`@Deprecated`, `[Obsolete]` or the like).
4. Replace every call to a data-access method of the active record with a call to the corresponding repository method.
5. Remove the data-access methods from the active record, turning it into an aggregate/entity.

### Split Repository into Interface and Implementation

- **ID:** `split-repository-into-interface-and-implementation`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/split-repository-into-interface-and-implementation>
- **Related:** often follows `split-active-record-into-aggregate-and-repository`

**Motivation.** A *repository* is the place in the domain layer where entities/aggregates are kept while not needed. Typically it stores the aggregate's data in a database. Database access is a technical detail the domain layer should not know about, so separate the repository's definition (domain layer) from its implementation (infrastructure layer).

**Mechanics.**

1. Apply [Extract Interface](https://refactoring.com/catalog/extractInterface.html) to the repository.
2. Move the implementation to the infrastructure layer; keep the interface in the domain layer.
3. Change all uses of the old repository to the new interface. Only the dependency-injection configuration may know the repository implementation.

### Extract Entity from Smart UI

- **ID:** `extract-entity-from-smart-ui`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/extract-entity-from-smart-ui>
- **Special case of:** Separate Domain from Presentation
- **Alternative to:** `extract-service-from-smart-ui`

**Motivation.** *Smart UI* is a pattern (an anti-pattern in DDD, see Evans 2004, p. 76) that mixes UI code and business logic. This refactoring separates the two concerns.

**Mechanics.**

1. In the smart UI class, separate the business logic from the UI logic with [Extract Method](https://refactoring.com/catalog/extractMethod.html).
2. Examine the extracted business-logic method. If it works on fields of the class, this refactoring is right. If it works only on its parameters, use `extract-service-from-smart-ui` instead.
3. Apply [Extract Class](https://refactoring.com/catalog/extractClass.html) and move the business logic and business data into the newly created entity.

### Extract Service from Smart UI

- **ID:** `extract-service-from-smart-ui`
- **Category:** tactical
- **URL:** <https://hschwentner.io/domain-driven-refactorings/tactical/extract-service-from-smart-ui>
- **Special case of:** Separate Domain from Presentation
- **Alternative to:** `extract-entity-from-smart-ui`

**Motivation.** Same as `extract-entity-from-smart-ui`: Smart UI mixes UI code and business logic, and this refactoring separates them.

**Mechanics.**

1. In the smart UI class, separate the business logic from the UI logic with [Extract Method](https://refactoring.com/catalog/extractMethod.html).
2. Examine the extracted business-logic method. If it can work only on its parameters, without using fields of the class, this refactoring is right. Otherwise use `extract-entity-from-smart-ui` instead.
3. Apply [Extract Class](https://refactoring.com/catalog/extractClass.html) and move the business-logic method into the newly created service.

---

## Glossary

Terms as the catalog pages use them.

- **Anemic entity / data bag:** a class that represents a domain concept and exposes all its data through getters and setters, while the domain logic lives in services.
- **Anemic domain model:** an anti-pattern consisting of anemic entities plus services that hold all domain logic.
- **Active Record:** a class that both represents a domain concept and manages its storage (Fowler, PoEAA).
- **Repository:** the place in the domain layer where entities/aggregates are kept while not needed, typically backed by a database.
- **Shared kernel:** model parts so common to several bounded contexts that they are put into their own artifact instead of being duplicated.
- **Smart UI:** UI code mixed with business logic; an anti-pattern in DDD.
- **Cross-functional team:** a team with all the knowledge needed for a vertical slice (UI, business logic, database) of one bounded context.
- **Idealized context map:** the target set of bounded contexts and their relationships, used to plan carving out or rebuilding.

## Bibliography

- Ambler, Scott W. and Pramod J. Sadalage. *Refactoring Databases: Evolutionary Database Design.* Addison-Wesley, 2006.
- Evans, Eric. *Domain-Driven Design: Tackling Complexity in the Heart of Software.* Addison-Wesley, 2004.
- Fowler, Martin. *Patterns of Enterprise Application Architecture.* Addison-Wesley, 2003.
- Fowler, Martin. "Strangler Fig Application." Bliki, June 29, 2004. <https://martinfowler.com/bliki/StranglerFigApplication.html>
- Fowler, Martin. *Refactoring: Improving the Design of Existing Code.* 2nd ed. Addison-Wesley, 2019.
- Gamma, Erich, Richard Helm, Ralph Johnson and John Vlissides. *Design Patterns: Elements of Reusable Object-Oriented Software.* Addison-Wesley, 1995.
- Kerievsky, Joshua. *Refactoring to Patterns.* Addison-Wesley, 2005.
- Lilienthal, Carola and Henning Schwentner. *Domain-Driven Transformation: Modularize and Modernize Legacy Software.* Addison-Wesley, 2024. <http://domain-driven-transformation.com>
- Skelton, Matthew and Manuel Pais. *Team Topologies: Organizing Business and Technology Teams for Fast Flow.* IT Revolution, 2019.

## Acknowledgement

Many of these refactorings were collected at the "Domain-Driven Refactorings" open space at KanDDDinsky 2021.
