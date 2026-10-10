# ADR Template

Use this template for ADRs in this fork, following an existing project's ADR conventions when provided. Keep entries concise and focused on the decision and its rationale; put implementation walkthroughs elsewhere. Use the numbering and location guidance in [ADR-FORMAT.md](./ADR-FORMAT.md) and the acceptance rules in [ADR-LIFECYCLE.md](./ADR-LIFECYCLE.md).

The rationale table captures reasons actually influencing the choice. Possible drivers include familiarity, infatuation with a technology, organizational standards, and project requirements. Include only relevant drivers. Familiarity may reduce training or delivery costs; enthusiasm may motivate an experiment. Neither establishes project fit without supporting evidence. Distinguish verified facts, assumptions, and unknowns; investigate weak reasoning rather than rewriting it as a convincing justification.

```markdown
# NNNN: Decision title

Status: Proposed

## Context

The problem, relevant constraints, and assumptions.

## Options Considered

| Option | Benefits | Drawbacks | Evidence or unknowns |
| --- | --- | --- | --- |
| Option A | ... | ... | ... |
| Option B | ... | ... | ... |

## Decision and Rationale

We propose/choose [option] because [evidence] supports [requirement], accepting [trade-off].

| Driver | Initial reason | Evidence or constraint | Trade-off | Assessment |
| --- | --- | --- | --- | --- |
| Relevant driver | Why it influenced us | Supporting evidence, assumption, or unknown | Cost or limitation accepted | Supported, insufficient alone, or needs investigation |

## Consequences

Expected benefits, accepted drawbacks, and remaining risks.
```

Replace placeholders and add or remove option rows to reflect the real comparison. If only one viable option is known, explain the constraint or unresolved investigation instead of inventing alternatives. Keep status explicit and use the project's established status vocabulary; use Proposed until acceptance is established.

For a replacement, link to the prior ADR and explain which assumptions or constraints changed. Mark the prior record superseded only when the replacement is accepted. Include a review date or trigger when useful.

The six core elements follow the talk's outline: title, context, status, decision, options, and consequences. The rationale table is this fork's adaptation of its discussion of familiarity, infatuation, and inherited standards, not a format prescribed by the speaker.
