# Contributing

This guide covers everything you need to know to contribute to this project.

---

## Getting Started
<!-- How does a new contributor get the project running locally? -->
1. Clone the repository
2. Install dependencies (see language-specific instructions below)
3. Copy `.env.example` to `.env` and fill in required values
4. Run the test suite to verify your setup

## Development Workflow
<!-- How does work get done on this project? -->
1. Pick up or create an issue before starting work
2. Branch off `main` with a descriptive name: `feat/short-description` or `fix/short-description`
3. Write code and tests together — tests are part of the feature (see `tenets.md`)
4. Open a PR with a clear description of *why* the change is being made
5. Request review from at least one other contributor

## Standards
See `.kiro/steering/standards.md` for coding standards and guardrails.

## Kiro Steering Files

The `.kiro/steering/` directory contains context files that guide Kiro's behavior.

**Kiro IDE** — steering files are auto-loaded every session. No action required.

**Kiro CLI** — steering files are NOT auto-loaded. You have two options:

Option 1 — Reference manually in chat:
```
#File .kiro/steering/tenets.md
#File .kiro/steering/standards.md
```

Option 2 — Use a custom agent config to auto-load them (recommended).
See `.kiro/agents/project-agent.json` for a ready-to-use example.
Start a session with: `kiro-cli chat --agent project-agent`

## Submitting a Pull Request
- Keep PRs small and focused on one concern
- Link to the relevant issue or spec
- Ensure all tests pass before requesting review
- Address review feedback before merging

## Reporting Issues
<!-- How should bugs or feature requests be raised? -->
- Use the issue tracker
- For bugs: include steps to reproduce, expected behavior, and actual behavior
- For features: reference the relevant spec in `specs/features/` or create one
