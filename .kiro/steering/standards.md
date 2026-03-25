# Development Standards

This document defines the coding standards and guardrails for this project.
It is intentionally minimal — covering universal principles that apply regardless
of language or framework. Language-specific tooling should be configured separately.

---

## Universal Guardrails

### Naming
- Use meaningful, descriptive names for variables, functions, and classes.
- Avoid abbreviations unless they are universally understood (e.g. `url`, `id`).
- No single-letter variable names outside of loop counters or math contexts.

### Functions and Methods
- Each function should do one thing and do it well (single responsibility).
- If a function needs a comment to explain what it does, consider renaming it first.
- All public functions, methods, and classes must have a docstring or doc comment.

### Error Handling
- Handle errors explicitly. Do not silently swallow exceptions.
- If a no-op is intentional, add a comment explaining why.

### Security
- No secrets, API keys, or credentials in source code or committed files.
- No PII in logs, comments, or test fixtures.
- Use environment variables or a secrets manager for sensitive configuration.

### Testing
- Unit tests are required for all business logic.
- Tests should be co-located with or clearly mapped to the code they cover.
- Test names should describe the behavior being tested, not the implementation.

### Pull Requests
- One concern per PR — keep changes small and focused.
- PR descriptions should explain *why* the change is being made, not just *what*.

---

## Language-Specific Configuration (Examples)

The following are examples of how teams typically extend these guardrails
for specific languages. Uncomment and adapt as needed for your stack.

<!--
### Python
- Style: PEP 8, enforced via `ruff` or `flake8`
- Type hints required on all public function signatures
- Formatter: `black` with default line length (88)
- Test framework: `pytest`
- Minimum test coverage: 80% on business logic modules
  Example config (pyproject.toml):
    [tool.coverage.report]
    fail_under = 80

### JavaScript / TypeScript
- Style: enforced via ESLint + Prettier
- TypeScript strict mode enabled (`"strict": true` in tsconfig.json)
- Test framework: Jest or Vitest
- Minimum test coverage: 80% on src/ (excluding generated files)
  Example config (jest.config.js):
    coverageThreshold: { global: { lines: 80 } }

### Branching Strategy
- Option A (Trunk-based): all work branches off `main`, short-lived feature branches, merge frequently
- Option B (Gitflow): `main` is production, `develop` is integration, feature branches off `develop`
- Recommended for small teams: trunk-based development with feature flags

### Commit Message Convention
- Format: `<type>(<scope>): <short summary>`
- Types: feat, fix, docs, refactor, test, chore
- Example: `feat(auth): add JWT refresh token support`
- Tool: enforce with `commitlint`
-->
