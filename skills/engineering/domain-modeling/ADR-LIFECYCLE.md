# ADR Lifecycle

Fork extension for creating, reviewing, and revisiting ADRs. Read [ADR-TEMPLATE.md](./ADR-TEMPLATE.md) when drafting or reviewing an ADR, including its decision rationale table. Use [ADR-FORMAT.md](./ADR-FORMAT.md) for numbering and location. The offer threshold governs unsolicited suggestions; follow explicit requests to record a decision even when it falls outside that threshold.

## Check the reasoning

Before finalizing, connect the choice to the project's constraints and desired outcomes. Familiarity, popularity, or an inherited standard alone does not explain why the choice fits this project. Record an applicable organizational constraint as a constraint; distinguish it from a technical preference.

Capture meaningful alternatives and their trade-offs, including drawbacks the team accepts. Consider effects on relevant qualities such as performance, scalability, and security. Challenge a consequential choice with no meaningful comparison; investigate alternatives or explain the constraint that rules them out. There is no fixed option count. Mark missing evidence or unresolved reasoning explicitly rather than inventing a justification.

## Reassess and supersede

Draft ADRs can evolve during review. Once a decision is accepted, preserve its context and reasoning; status updates, links, and typo corrections can still change.

When revisiting a decision, read the existing ADR and check whether its assumptions and constraints still apply. Where validity depends on changing technology or business conditions, record a useful review date or trigger. A review becoming due prompts reassessment, not automatic reversal.

If a replacement is proposed, create a new numbered ADR explaining what changed and why, and link it to the previous record. Keep the previous decision active during review. Once the replacement is accepted, mark the previous record as superseded with a link to its replacement. Keep both records accessible in version control. Review proposed decisions through the team's existing review process; describe acceptance only when it has been established.

## Source

The reasoning and lifecycle guidance draws on [ADRs: The Why and How, Venkat Subramaniam](https://youtu.be/wzN6qq08w0U): reasoning at 32:23, reassessment at 33:46, alternatives and consequences at 41:34, and immutability and supersession at 45:30. The three-part threshold in ADR-FORMAT.md is this repository's policy; the talk uses a broader emphasis on impact and preserving decision rationale. Review triggers are a practical adaptation of the talk's review intervals. The speaker recommends at least three options; this fork requires a meaningful comparison without a fixed quota.
