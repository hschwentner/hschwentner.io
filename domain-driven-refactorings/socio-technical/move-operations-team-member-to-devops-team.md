---
title: Move Operations Team Member to DevOps Team
---

![](../../images/domain-driven-refactorings/socio-technical/ops-team-to-devops.drawio.svg)

## Motivation

You are in the following situation:

- There are cross-functional development teams (maybe as a result of [Form Cross-Functional Team out of Layer-Team Members](form-cross-functional-team-out-of-layer-team-members)).
- Operations is done by another team.

That means when one of the development teams is ready for a new deployment, they give their result to the operations team and hope the ops team will bring the new version into production. When the ops team runs into an error during deployment, they have to go back to the dev team. A play of ping-pong starts.

The goal of DevOps is to avoid that ping-pong by pushing the cross-functional idea so far to integrate also the operations know-how into the development team.[^natural-state] With this refactoring we move the organization a step into the DevOps direction.

[^natural-state]: Many people think about this as just bringing software development into its natural state…

[Team Topologies](https://teamtopologies.com) will help you here.

## Mechanics

- Choose a first development team that wants to apply the DevOps idea.
- Choose one of the operators and assign them to the former to team to form the first DevOps team.
- Let the team members educate each other with the knowledge that they didn't have so far. The goal here is to achieve a t-shaped skill profile for both the dev and the op.
- Repeat until you eventually have replaced the former operations team.

## Example(s)
