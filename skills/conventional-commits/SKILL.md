---
name: conventional-commits
description: Conventional Commits specification for consistent, machine-readable git commit messages. Use when writing commit messages, reviewing commit history, or setting up commit linting.
metadata:
  origin: demo
---

# Conventional Commits

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification for all commit messages in this team's repositories.

## When to Activate

- Writing a git commit message
- Reviewing commit history in code review
- Generating changelogs from git history
- Setting up commit linting / changelog tooling

## Commit Message Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Meaning |
|------|---------|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation only changes |
| `style` | Formatting, no code change (whitespace, semicolons) |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf` | A performance improvement |
| `test` | Adding or correcting tests |
| `build` | Build system or external dependencies |
| `ci` | CI configuration files and scripts |
| `chore` | Other changes that don't modify src or test |

### Examples

```
# Good
feat(api): add pagination to list endpoints
fix(auth): handle expired refresh tokens
docs(readme): document local setup steps
refactor(users): extract validation into service layer
perf(cache): reduce TTL for hot keys
test(orders): cover empty-cart checkout path

# Bad
update stuff
fix bug
.
wip
asdf1234
```

## Rules

1. **`feat` and `fix` MUST** be used (breaking change awareness depends on them)
2. **Scope is optional** but recommended for larger repos: `feat(orders): ...`
3. **Breaking changes MUST** be indicated: `feat!:` or a `BREAKING CHANGE:` footer
4. **Description**: imperative mood, lowercase, no trailing period, ≤ 72 chars
5. **One logical change per commit** — don't mix refactor with fix
6. **Body** explains the *why*, not the *what* (the diff shows what)

### Breaking Change Footer

```
feat(api)!: remove deprecated v1 endpoints

BREAKING CHANGE: v1 endpoints removed; migrate to /api/v2 before June 2026.
```

## Changelog Derivation

`feat` → "Added"; `fix` → "Fixed"; `BREAKING CHANGE` → "Changed" / breaking section.

## Verification

Before finalizing a commit:

- [ ] Type is one of the allowed set (or a custom type documented in repo)
- [ ] Scope in parentheses if used
- [ ] Description imperative, ≤ 72 chars, no trailing period
- [ ] Breaking change properly flagged (`!` or footer)
- [ ] Body present for non-obvious changes, explains why
