# ADR Lifecycle

Fork extension for creating, reviewing, and revisiting ADRs. Use [ADR-FORMAT.md](./ADR-FORMAT.md) for the concise format. The offer threshold governs unsolicited suggestions; follow explicit requests to record a decision even when it falls outside that threshold.

## Check the reasoning

Before finalizing, connect the choice to the project's constraints and desired outcomes. Familiarity, popularity, or an inherited standard alone does not explain why the choice fits this project. Record an applicable organizational constraint as a constraint; distinguish it from a technical preference.

Capture meaningful alternatives and their trade-offs when they explain the choice, including drawbacks the team accepts. Consider effects on relevant qualities such as performance, scalability, and security. Use the alternatives actually considered; there is no fixed option count. Mark missing evidence or unresolved reasoning explicitly rather than inventing a justification.

## Reassess and supersede

Draft ADRs can evolve during review. Once a decision is accepted, preserve its context and reasoning; status updates, links, and typo corrections can still change.

When revisiting a decision, read the existing ADR and check whether its assumptions and constraints still apply. Where validity depends on changing technology or business conditions, record a useful review date or trigger. A review becoming due prompts reassessment, not automatic reversal.

If the decision changes, create a new numbered ADR explaining what changed and why, link it to the previous record, and mark the previous record as superseded with a link to its replacement. Keep both records accessible in version control. Review proposed decisions through the team's existing review process; describe acceptance only when it has been established.

## Source

The reasoning and lifecycle guidance draws on [ADRs: The Why and How, Venkat Subramaniam](https://youtu.be/wzN6qq08w0U): reasoning at 32:23, reassessment at 33:46, alternatives and consequences at 41:34, and immutability and supersession at 45:30. The three-part threshold in ADR-FORMAT.md is this repository's policy; the talk uses a broader emphasis on impact and preserving decision rationale. Review triggers are a practical adaptation of the talk's review intervals.
