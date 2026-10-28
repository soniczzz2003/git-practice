# Git Workflow

A lightweight git workflow for learning together. Keep it simple: short-lived feature branches, squash-merge into `develop`, and user-triggered releases from `develop` to `main`.

## Branching Model

```text
feat/short-description ──┐
fix/short-description ───┤
docs/short-description ──┼──> develop ──> main
chore/short-description ─┘
```

All merges use `--no-ff`. No fast-forward merges.

## Branch Naming

```text
feat/add-moving-average
fix/ema-division-by-zero
docs/update-readme
chore/update-dependencies
```

Lowercase. Hyphens as separators. Short and descriptive. Use one of `feat`, `fix`, `docs`, `chore`.

## Commit Format

```text
type(scope): short description
```

Scope is optional. Use imperative mood. Keep the subject under ~50 characters.

### Allowed Types

| Type | Use |
|------|-----|
| `feat` | New feature |
| `fix` | Bug fix |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `test` | Adding or correcting tests |
| `docs` | Documentation only |
| `chore` | Build process, dependencies, tooling |
| `ci` | CI/CD configuration |
| `perf` | Performance improvement |
| `build` | Build system or external dependency changes |

### Examples

```text
feat: add moving average
fix(ema): handle division by zero
test(ema): cover zero-length input
docs(readme): document setup steps
chore: update dependencies
```

## Merge Rules

### Feature → develop

1. Develop on a feature branch (`feat/`, `fix/`, `docs/`, or `chore/`).
2. Squash all commits on the branch into one commit.
3. `--no-ff` merge the branch into `develop`.
4. Delete the branch after merging.

### develop → main

- `develop → main` merges are user-triggered: run them only for releases or milestones.
1. `--no-ff` merge `develop` into `main`.
2. Optionally tag the merge commit (e.g. `v0.1.0`).

### Forbidden

* Fast-forward merges
* Direct commits to `main`
* Direct commits to `develop`

## Tips for Learning Together

* Review each other's pull requests before merging.
* Keep commits small and focused on one thing.
* If something breaks, revert and try again — git makes it safe to experiment.
