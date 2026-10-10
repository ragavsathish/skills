# ADR Format

ADRs live in `docs/adr/` and use sequential numbering: `0001-slug.md`, `0002-slug.md`, etc.

Create the `docs/adr/` directory lazily: only when the first ADR is needed.

## Template

```md
# {Short title of the decision}

{1-3 sentences: what's the context, what did we decide, and why.}
```

That's it. An ADR can be a single paragraph. The value is in recording *that* a decision was made and *why*, not in filling out sections.

## Optional sections

Only include these when they add genuine value. Most ADRs won't need them.

- **Status** frontmatter (`proposed | accepted | deprecated | superseded by ADR-NNNN`): useful when decisions are revisited
- **Considered Options**: only when the rejected alternatives are worth remembering
- **Consequences**: only when non-obvious downstream effects need to be called out

## Numbering

Scan `docs/adr/` for the highest existing number and increment by one.

## Check the reasoning

Before finalizing, connect the choice to the project's constraints and desired outcomes. Familiarity, popularity, or an inherited standard alone does not explain why the choice fits this project. Record an applicable organizational constraint as a constraint; distinguish it from a technical preference.

Capture meaningful alternatives and their trade-offs when they explain the choice, including drawbacks the team accepts. Consider effects on relevant qualities such as performance, scalability, and security. Use the alternatives actually considered; there is no fixed option count. Mark missing evidence or unresolved reasoning explicitly rather than inventing a justification.

## Reassess and supersede

Draft ADRs can evolve during review. Once a decision is accepted, preserve its context and reasoning; status updates, links, and typo corrections can still change.

When revisiting a decision, read the existing ADR and check whether its assumptions and constraints still apply. Where validity depends on changing technology or business conditions, record a useful review date or trigger. A review becoming due prompts reassessment, not automatic reversal.

If the decision changes, create a new numbered ADR explaining what changed and why, link it to the previous record, and mark the previous record as superseded with a link to its replacement. Keep both records accessible in version control. Review proposed decisions through the team's existing review process; describe acceptance only when it has been established.

## When to offer an ADR

All three of these must be true:

1. **Hard to reverse**: the cost of changing your mind later is meaningful
2. **Surprising without context**: a future reader will look at the code and wonder "why on earth did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives and you picked one for specific reasons

If a decision is easy to reverse, skip it: you'll just reverse it. If it's not surprising, nobody will wonder why. If there was no real alternative, there's nothing to record beyond "we did the obvious thing."

### What qualifies

- **Architectural shape.** "We're using a monorepo." "The write model is event-sourced, the read model is projected into Postgres."
- **Integration patterns between contexts.** "Ordering and Billing communicate via domain events, not synchronous HTTP."
- **Technology choices that carry lock-in.** Database, message bus, auth provider, deployment target. Not every library: just the ones that would take a quarter to swap out.
- **Boundary and scope decisions.** "Customer data is owned by the Customer context; other contexts reference it by ID only." The explicit no-s are as valuable as the yes-s.
- **Deliberate deviations from the obvious path.** "We're using manual SQL instead of an ORM because X." Anything where a reasonable reader would assume the opposite. These stop the next engineer from "fixing" something that was deliberate.
- **Constraints not visible in the code.** "We can't use AWS because of compliance requirements." "Response times must be under 200ms because of the partner API contract."
- **Rejected alternatives when the rejection is non-obvious.** If you considered GraphQL and picked REST for subtle reasons, record it; otherwise someone will suggest GraphQL again in six months.

## Source

The reasoning and lifecycle guidance draws on [ADRs: The Why and How, Venkat Subramaniam](https://youtu.be/wzN6qq08w0U): reasoning at 32:23, reassessment at 33:46, alternatives and consequences at 41:34, and immutability and supersession at 45:30. The three-part threshold above is this repository's policy; the talk uses a broader emphasis on impact and preserving decision rationale. Review triggers are a practical adaptation of the talk's review intervals.
