# Kiro Project Skeleton

A starter scaffold for high-quality software projects using Kiro AI. This skeleton
provides the structure, context files, and conventions that help Kiro generate
consistent, well-reasoned code from day one — and keeps human contributors aligned
on the same principles.

---

## Philosophy

Good AI-assisted development requires the same things good human development requires:
clear goals, agreed rules, and shared standards. This skeleton externalizes those things
into files that both humans and Kiro can read, reference, and reason about.

The structure is intentionally minimal. Every file here earns its place.

---

## Structure

```
.
├── CONTRIBUTING.md              # How to contribute, workflow, and Kiro usage guide
│
├── .kiro/
│   ├── steering/                # Context files loaded by Kiro (see "Using with Kiro" below)
│   │   ├── tenets.md            # Non-negotiable project rules
│   │   ├── strategy.md          # Vision, goals, success criteria, out-of-scope
│   │   └── standards.md         # Coding guardrails and style conventions
│   └── agents/
│       └── project-agent.json   # Kiro CLI agent config that auto-loads steering files
│
├── docs/
│   ├── architecture.md          # Living system design document
│   └── decisions/
│       ├── README.md            # How and when to write ADRs
│       └── adr-000-example.md   # Worked example of an Architecture Decision Record
│
└── specs/
    ├── README.md                # How to write feature specs
    └── features/
        └── example-feature.md  # Worked example of a feature spec
```

---

## What Each Piece Does

### `.kiro/steering/`
The core of this skeleton. These three files define *how* the project operates:

- **`tenets.md`** — Rules that cannot be broken. When there's ambiguity about a decision,
  return here first. Kiro uses these to constrain its suggestions.
- **`strategy.md`** — The north star. What are we building, for whom, and what does success
  look like? Keeps scope honest and prevents drift.
- **`standards.md`** — Universal coding guardrails: naming, error handling, testing, security,
  and PR expectations. Includes commented examples for language-specific tooling (Python,
  TypeScript, branching strategy, commit conventions) that teams can uncomment and adapt.

### `docs/`
Human-facing reference documentation that lives alongside the code.

- **`architecture.md`** — A living document describing the system's structure and key design
  decisions. Update it as the system evolves.
- **`decisions/`** — Architecture Decision Records (ADRs). One file per significant technical
  decision, capturing the context, options considered, and rationale. Prevents re-litigating
  settled decisions as the team grows.

### `specs/features/`
Feature-level specifications written before implementation begins. Each spec defines what
a feature does, who it's for, acceptance criteria, and what's explicitly out of scope.
Specs give Kiro a precise target when generating code and give reviewers a clear definition
of done.

### `.kiro/agents/project-agent.json`
A Kiro CLI agent configuration that eagerly loads all steering files at session start.
Only relevant for Kiro CLI users — see "Using with Kiro" below.

---

## Using with Kiro

### Kiro IDE
Steering files in `.kiro/steering/` are **automatically loaded** on every session.
No setup required — open the project and Kiro has full context.

### Kiro CLI
Steering files are **not** auto-loaded in CLI mode. Two options:

**Option A — Manual (per session):**
```
kiro-cli chat
> #File .kiro/steering/tenets.md
> #File .kiro/steering/strategy.md
> #File .kiro/steering/standards.md
```

**Option B — Agent config (recommended):**
```bash
kiro-cli chat --agent project-agent
```
This uses `.kiro/agents/project-agent.json` to eagerly load all steering files
at session start. The agent config is project-scoped and travels with the repo.
To make it available globally, copy it to `~/.kiro/agents/`.

---

## Getting Started

1. Clone or copy this skeleton into your project
2. Fill in `.kiro/steering/strategy.md` — vision, goals, and non-goals
3. Review and adjust `.kiro/steering/tenets.md` — remove or add rules that fit your context
4. Uncomment the relevant language-specific sections in `.kiro/steering/standards.md`
5. Replace `docs/architecture.md` with your actual system design
6. Write your first feature spec in `specs/features/` before starting implementation
7. Start Kiro with full context: `kiro-cli chat --agent project-agent`

---

## Tradeoff Decisions

**Steering files over plain docs**
We use `.kiro/steering/` rather than a generic `docs/` folder for these files because
Kiro IDE auto-loads them, making them active context rather than passive documentation.
The tradeoff: they're Kiro-specific. We mitigate this by writing them as high-quality
markdown that's useful to humans too — they serve double duty.

**Minimal guardrails over comprehensive standards**
`standards.md` covers universal principles only, with language-specific rules commented
out as examples. The tradeoff: teams must do a small amount of setup to activate
language-specific tooling. The benefit: the skeleton works out of the box for any stack
without requiring teams to delete irrelevant rules.

**Specs as pre-implementation artifacts**
Feature specs live in `specs/features/` and are intended to be written *before* code.
This is a deliberate workflow choice — it forces clarity on acceptance criteria before
Kiro generates an implementation. The tradeoff: it adds a step before coding begins.
The benefit: Kiro-generated code is more accurate and scoped, and reviews are faster.

**ADRs over inline comments for design decisions**
Significant architectural decisions are captured in `docs/decisions/` rather than
code comments or PR descriptions. The tradeoff: requires discipline to write them.
The benefit: decisions are discoverable, searchable, and survive team turnover.

**Project-scoped agent config over global**
`.kiro/agents/project-agent.json` is committed to the repo rather than installed globally.
The tradeoff: each developer needs to be aware of it. The benefit: the agent config
is versioned with the project and consistent across the team.
