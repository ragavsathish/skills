---
name: c4-diagrams
description: Create, review, refine, or explain C4 software architecture models and diagrams. Use for system context, container, component, code, dynamic, deployment, event-driven, or perspective views; architecture maps for codebases and proposed systems; Mermaid, Structurizr, PlantUML, ASCII, SVG, PNG, or Excalidraw output; and critique of boxes-and-lines diagrams.
---

# C4 Diagrams

Use C4 as a structured map that helps an audience answer an architecture question. Treat the model and its terminology as primary; notation and visual style are representations of that model.

Read `references/c4-guide.md` completely for every non-trivial creation, review, or refinement task.

## Workflow

1. State the audience, decision, and software system in scope. The scope is complete when inside, outside, and the intended question are explicit.
2. Choose the smallest useful view:
   - System Context for people, the system in scope, and external systems.
   - Container for applications, services, data stores, queues, and major technology choices inside one system.
   - Component for responsibilities and interactions inside one container.
   - Code only for implementation structure the audience genuinely needs.
   - Dynamic for an important runtime scenario.
   - Deployment for where container instances run.
   - Perspective for security, ownership, resilience, or another cross-cutting concern.
3. Build an evidence-backed model. Classify every element and relationship before drawing. For codebase-derived views, inspect code and configuration instead of inferring architecture from names alone.
4. Produce the requested notation. When unspecified, use Mermaid for quick Markdown output and Structurizr DSL for a reusable, multi-view model. Keep the textual source as the authoritative artifact.
5. Render visual output when requested and inspect the result. Correct clipping, overlap, unreadable labels, missing boundaries, broken arrows, and semantic differences from the source.
6. Explain the important relationships, assumptions, and open questions concisely.
7. Apply every relevant item in the reference quality checklist.

## Review

Lead with the highest-impact modeling issue, then provide concrete edits or a tightened diagram. Prioritize scope, abstraction level, element classification, boundaries, relationship direction and verbs, hidden event intermediaries, and excess detail.

## Completion

Finish when the diagram has a clear title and scope, one coherent abstraction level, correctly contained and typed elements, meaningful directed relationships, and explicit assumptions. When a rendered artifact is part of the request, finish only after inspecting it against the textual source.
