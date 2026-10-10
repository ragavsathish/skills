# C4 Diagram Guide

Use this guide after the `c4-diagrams` skill triggers for any non-trivial creation, review, or refinement task.

## Contents

- Core Model
- Diagram Levels
- Selection Heuristics
- Diagram Construction
- Event-Driven Systems
- Dynamic And Deployment Views
- DDD, Layers, And Organization
- Microservices And Shared Libraries
- Scale And Freshness
- Model-Code Gap
- Notation Guidance
- Rendered Artifacts
- Visual Style
- Quality Checklist
- Common Mistakes

## Core Model

C4 is a small set of named hierarchical abstractions for making software architecture diagrams more precise than ad hoc boxes and arrows. Its value is the vocabulary and discipline, not a fixed visual style.

- Software system: the system being built or a significant external system.
- Container: an application or data store that runs or stores data, such as a web app, API app, mobile app, database schema, object store, queue, topic, or command-line process. It does not mean Docker unless the system context makes Docker relevant.
- Component: a logical building block inside a container.
- Code: classes, interfaces, functions, modules, or other implementation details.

C4 is notation independent and tooling independent. Use the diagram language that fits the user's environment.

C4 is not a design process. It can document or support DDD, ports and adapters, event modeling, layered architecture, cloud architecture, or microservices, but it should not dictate those design choices.

## Diagram Levels

System Context:
Show the software system in scope, the people who use it, and the external systems it depends on. Answer: What is the scope? Who uses it? What do they do? Which integrations must it support?

Container:
Zoom into one software system. Show applications, services, databases, queues/topics, object stores, scheduled jobs, and major technology choices. Answer: What is the overall shape of the architecture?

Component:
Zoom into one container. Show logical components and their interactions. Answer: What responsibilities exist inside this application or service?

Code:
Zoom into one component. Use only when implementation details are needed. Few architecture conversations need this level; prefer code references or UML-style class diagrams only when useful.

Dynamic:
Use a sequence-style or collaboration-style view for one important runtime scenario. Show C4 elements interacting in order. Use sparingly for complicated flows or recurring patterns, not one diagram per feature.

Deployment:
Show C4 container instances mapped onto deployment nodes and infrastructure nodes. Use for runtime topology, cloud resources, environments, regions, load balancers, databases, and network boundaries.

Perspective:
Overlay one quality concern onto an existing view instead of inventing a new diagram type. Use for security, resilience, failover, ownership, performance, scalability, privacy, observability, or operational responsibility.

## Selection Heuristics

- If the user gives only a product/system idea, start with System Context.
- If the user gives services, apps, databases, queues, or runtimes, create a Container diagram.
- If the user asks how one service/module works internally, create a Component diagram for that container.
- If the user asks about classes, functions, interfaces, package boundaries, or refactoring internals, use a Code diagram or code-level explanation.
- If the user asks for "all C4 diagrams", create Context and Container first, then add Components only for the most important containers.
- If the user asks about a workflow over time, choose a dynamic view.
- If the user asks where things run, choose a deployment view.
- If the user asks about security, ownership, failure modes, or other cross-cutting qualities, use a perspective overlay on the smallest useful base diagram.
- If the user asks for decisions, suggest ADRs and show only the resulting structure in the diagram.

## Diagram Construction

Use this sequence:

1. Define the system in scope in one sentence.
2. List people and external systems.
3. List internal containers, their responsibilities, and technologies.
4. Choose which relationships matter for the intended audience.
5. Draw one diagram at a time.
6. Add assumptions and questions after the diagram.

Ask these questions when the input is thin:

- What software system is in scope?
- Who are the users or actors?
- What is inside versus outside that system boundary?
- What external systems does it integrate with?
- What are the major applications and data stores?
- What are their responsibilities?
- How do they communicate?
- Which view would help this audience make a decision?

For each element, include:

- name
- C4 type
- short responsibility
- technology, only when it clarifies the architecture
- boundary or ownership, when relevant

For each relationship, include:

- direction
- action verb
- data/protocol, when useful
- sync/async/event wording, when relevant

Keep labels self-describing. A reader should not need the author in the room to know what a box is or why an arrow exists.

## Event-Driven Systems

C4 can describe event-driven architectures when events and intermediaries are explicit. The main risk is hiding the true story by drawing vague service-to-service dependencies when the actual coupling is through messages.

- Model queues, topics, streams, and message buses as containers when they are part of the software system.
- Label relationships with "publishes", "subscribes to", "consumes", "emits", or "routes".
- Name important event types when they affect design.
- Use a dynamic diagram or sequence-style view for specific workflows.
- Use bounded context boundaries when they clarify ownership or domain language.

Choose one of these event notations deliberately:

- Explicit topic/queue as a container: best when the intermediary is important to understand.
- Service-to-service arrow labeled with the intermediary: compact, but weaker for readers who need to see the messaging topology.
- Publish/subscribe arrows around topic containers: useful for one-to-many flows and when the team uses publish/subscribe language.

Avoid drawing event-driven systems as simple direct service-to-service calls if the queue, topic, stream, event type, or ownership boundary matters.

## Dynamic And Deployment Views

Use dynamic diagrams to explain important scenarios such as sign-in, checkout, report generation, or data ingestion. Dynamic diagrams should use the same C4 elements but order the interactions.

Use deployment diagrams for runtime topology: deployment nodes, infrastructure nodes, containers deployed onto nodes, network boundaries, cloud regions, load balancers, and databases.

These are complementary views. They are not replacements for context/container/component diagrams.

## DDD, Layers, And Organization

C4 complements DDD and event modeling. It should not compete with them.

- Show bounded contexts as boundaries around C4 elements when the mapping is useful.
- If a bounded context cuts through a software system, show that at the level where it becomes visible.
- Treat controller, service, repository, and similar layers as organizational groupings unless they are independently meaningful architecture elements.
- Do not add arbitrary extra abstraction levels unless the team can define them clearly and consistently.

## Microservices And Shared Libraries

Model a microservice as one of:

- a software system
- a container
- a group of containers

Choose based on ownership, deployability, data ownership, and the audience's mental model. Do not model a microservice's API and database schema as components merely because they are below the microservice in a hierarchy.

For shared libraries:

- Do not model shared code as a C4 container unless it is independently runnable or a data store.
- Prefer showing the shared library's components inside each consuming container.
- Use a grouping, annotation, or build-time boundary to show that the component comes from a shared artifact.

## Scale And Freshness

C4 does not automatically solve scale or stale diagrams. Use modeling and automation when scale matters.

- For small systems, a few manually authored diagrams may be enough.
- For larger landscapes, prefer a reusable model with filtered views rather than hand-copying boxes across many diagrams.
- Use Structurizr DSL, C4-PlantUML, Mermaid export, or another modeling workflow when the user needs source-controlled architecture.
- Generate or refresh model elements from service registries, Backstage, ServiceNow, OpenTelemetry, logs, source analysis, Terraform, CloudFormation, or cloud inventory where practical.
- For exploration questions, a graph view or queryable model may be better than a static diagram.

If a diagram is too dense, split it by story or viewpoint. State the tradeoff: one complete diagram shows everything but is hard to read; several filtered views are readable but hide the full network.

## Model-Code Gap

Use C4 to keep the top-down mental model traceable to code where possible.

- Name components in ways that can be found in code, configuration, package structure, annotations, or conventions.
- For codebase-derived component diagrams, prefer static analysis, reflection, framework metadata, or source parsing over guessing.
- Avoid reverse-engineered class diagrams when they produce a low-value tangle.
- A good component diagram groups code elements that work together at runtime behind one meaningful responsibility.

## Notation Guidance

Mermaid:
Use for quick Markdown-friendly diagrams. Keep labels short. Use comments or nearby prose for richer descriptions. Mermaid is acceptable for conversation, issues, and lightweight docs, but it is not a central architecture model.

Structurizr DSL:
Use when the user wants a reusable model, multiple views, styles, tags, filtered views, generated diagrams, or a source-controlled architecture workspace.

PlantUML:
Use when the repo already uses PlantUML or C4-PlantUML.

Plain text/table:
Use before drawing when the architecture is uncertain; first align the model, then render it.

## Rendered Artifacts

Treat the textual model or diagram source as authoritative. A renderer must preserve its elements, containment, relationship direction, labels, and scope.

For SVG, PNG, Excalidraw, or another visual artifact:

1. Generate the artifact from the accepted source or model.
2. Open and inspect the actual rendered result.
3. Compare it with the source for missing or altered semantics.
4. Correct clipping, overlap, unreadable text, excessive crossings, detached arrows, and ambiguous boundaries.
5. Preserve editable elements when the user asks for an editable diagram. An embedded raster image inside Excalidraw is a preview, not an editable scene.

Keep generated binary artifacts alongside their source when they belong in a repository. Regenerate them when the source changes.

## Visual Style

C4 does not require a fixed palette. Prefer clarity over novelty.

- Use high contrast text.
- Use muted colors to distinguish element types or boundaries.
- Use consistent shapes and labels.
- Avoid using color as the only meaning channel.
- Keep line crossings low and group related elements.
- Do not assume C4 means blue and grey boxes.

## Quality Checklist

Before finalizing, check:

- The diagram has a clear title and scope.
- Every box has a C4 type or an obviously consistent notation.
- The chosen level is coherent.
- People and external systems appear on context diagrams.
- Containers are deployable/runnable things or data stores, not arbitrary code concepts.
- Components are inside exactly one container.
- Relationships have direction and meaningful labels.
- Important protocols, data flows, or event types are named when they matter.
- Boundaries are shown where they change interpretation.
- The diagram is small enough to discuss.
- The explanation captures assumptions and open questions.
- The notation makes the true coupling visible enough for the audience.
- The diagram does not pretend to show decisions that belong in ADRs.
- The diagram will either be cheap to update or clearly marked as a point-in-time view.
- The textual source and rendered artifact express the same model.
- Requested visual output has been opened and inspected.

## Common Mistakes

- Treating C4 as a fixed visual notation instead of a set of abstractions.
- Treating C4 as a design process instead of a diagramming approach.
- Creating all four levels by default.
- Mixing components, containers, and classes in one view.
- Using "service", "module", or "component" without defining what it means in context.
- Drawing organizational layers as architectural abstractions when they are only team or code organization constructs.
- Modeling shared libraries as containers.
- Modeling Kafka, RabbitMQ, or another broker as the only container when topics/queues/events are the real architectural story.
- Modeling microservices inconsistently without deciding whether each is a system, a container, or a group of containers.
- Making diagrams too detailed for the audience.
- Hiding the external systems that explain why the system exists.
- Leaving arrows unlabeled.
- Ignoring important dynamic or deployment views because they are not one of the four static levels.
- Expecting C4 itself to keep diagrams up to date.
- Returning an uninspected render that clips labels, loses relationships, or differs from its source.
