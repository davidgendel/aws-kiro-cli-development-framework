# Architecture Decision Records (ADRs)

This folder contains Architecture Decision Records — lightweight documents that
capture *why* a significant technical decision was made, not just *what* was decided.

---

## Why ADRs?

Decisions made without documentation get re-litigated. ADRs prevent that by
recording the context, options considered, and rationale at the time of the decision.

## When to Write an ADR

Write an ADR when a decision:
- Is hard to reverse
- Affects multiple parts of the system
- Involves a meaningful tradeoff between options
- Would confuse a new team member if they encountered it without context

## How to Write an ADR

- One file per decision, numbered sequentially: `adr-001-*.md`, `adr-002-*.md`
- Keep it short — the goal is to capture reasoning, not write an essay
- Status should be one of: `Proposed`, `Accepted`, `Deprecated`, `Superseded`

See `adr-000-example.md` for a full example.
