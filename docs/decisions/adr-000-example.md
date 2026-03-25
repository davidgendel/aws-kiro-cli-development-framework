# ADR-000: [Decision Title]

> This is an example ADR. Copy this file, increment the number, and replace
> all placeholder content with your decision's details.

---

**Status:** Accepted
**Date:** YYYY-MM-DD
**Deciders:** [Names or teams involved in the decision]

---

## Context
<!-- What situation or problem forced this decision?
     Include relevant constraints, requirements, or background. -->
We needed to choose a primary database for the application. The system requires
flexible querying, strong consistency, and must support 10k+ concurrent users.

## Options Considered

| Option | Pros | Cons |
|--------|------|------|
| PostgreSQL | Mature, strong consistency, rich query support | Requires more ops overhead than managed NoSQL |
| DynamoDB | Fully managed, scales automatically | Limited query flexibility, higher cost at low scale |
| MongoDB | Flexible schema, good developer experience | Eventual consistency by default, licensing concerns |

## Decision
<!-- What was decided, and why? -->
We chose **PostgreSQL** (via Amazon RDS). The team has existing expertise,
the query patterns are relational in nature, and strong consistency is a
hard requirement for financial data.

## Consequences
<!-- What becomes easier or harder as a result of this decision? -->
- Easier: complex joins, transactions, and reporting queries
- Harder: horizontal scaling at very high write volumes (acceptable tradeoff for now)
- We will revisit if write throughput exceeds 50k/sec (see strategy.md constraints)
