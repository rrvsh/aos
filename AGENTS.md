# aos

This repository is a work-in-progress project to build a personal and consistent cross-platform computing experience.

## Git workflow

All changes should reach the main branch through squash merging.
All commit messages that touch the main branch must be hand-authored.
Commits messages on branches that will later be squash-merged are not subject to any restrictions.

## Architectural guidelines

- We should use one shared core across all platforms.
  - Differences should be limited to unavoidable platform capabilities.
- Each machine runs as one node in a system of other machine nodes.
- The user should interact with the system, not each individual or machine node.
- The other networked machine nodes should only be used for progressive enhancement.
  - Features must work locally as much as possible.
  - Features which are impossible locally must be available in a degraded form locally.
  - Degraded features and impossible features should be made progressively available based on the machine nodes (or presence thereof) available.
- Every capability of the system must have an interface that is usable by humans, agents, and automations.
- Dependencies that could constrain the system should be isolated so they can later be replaced or moved in-house piecemeal.
- The system must make each view, action, cause, state transition, and consequence:
  - observable
  - traceable
  - configurable
  - modifiable
- Begin every story with the smallest usable vertical slice.
  - This is so it can be dogfooded, then later modified or extended in response.
  - Avoid premature optimisation for performance or UX.
- Every important decision must be recorded in an ADR.
- Boundaries for LLM agents must not be handled through a policy engine; instead, use the principle of least access. Each agent should only be given the access it needs to accomplish its task.

## Codebase understanding and learning

As a core part of the computing experience is education, and building it is a core part of a software engineering curriculum, a major focus when working in this repository is the user's understanding of the codebase and their learning while developing it.

Some learning goals, not limited to only this list:

- avoiding accidental complexity and keeping it only to essential complexity

Tasks should generally be split into three phases:

### Planning/research

This phase is a conversation between the user and the agent where the goal is to isolate the exact shape of the problem, ground it in the codebase, and propose a change plan to implement.

The user must make every non-obvious decision.

### Implementation

Here, agents should be limited to mechanical work where all the decision-making has been done. Any ambiguity that surfaces during implementation should stop it and ask the user to write the code themselves.

The user will write all the code that:

- has no existing pattern in the codebase
- contains interesting or important (to the system) algorithms or techniques
- requires strict understanding of the domain

### Documentation

Always consider whether documentation is needed after a task is finished.
In general, all changes need at minimum an entry in a changelog file.

All documentation prose in this repository must be entirely human-written.
LLM agents may only review files and propose changes in chat.
