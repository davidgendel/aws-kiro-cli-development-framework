# Project Tenets

Tenets are non-negotiable rules that govern every decision made in this project.
When in doubt, return to these. They exist to resolve ambiguity and prevent drift.

---

## 1. Security is not optional
Never store secrets, credentials, or PII in source code or version control.
Sensitive data must be handled via environment variables, secret managers, or vaults.

## 2. Clarity over cleverness
Code is read far more than it is written. Prefer readable, explicit code over
clever or terse solutions. Future maintainers (including yourself) will thank you.

## 3. Every public interface must be documented
All public functions, methods, classes, and modules must have a docstring or
comment that explains *what* it does and *why* it exists — not just *how*.

## 4. Errors must be handled explicitly
Silent failures are bugs waiting to surface in production. Every error path
must be acknowledged and handled intentionally, even if the handling is a
deliberate no-op with a comment explaining why.

## 5. Tests are part of the feature
Business logic is not complete without a corresponding unit test. Tests are
not an afterthought — they are part of the definition of done.

## 6. Small, focused changes
Pull requests should address one concern. Large, multi-purpose PRs are harder
to review, harder to revert, and harder to understand in git history.

## 7. Explicit over implicit
Avoid magic. Configuration, dependencies, and behavior should be visible and
traceable. If something isn't obvious from reading the code, it needs a comment.
