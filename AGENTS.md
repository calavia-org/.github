# .github — Agent Instructions

> **MANDATORY READ**: This repository is governed by [`~/Development/Github/AGENTS.md`](../AGENTS.md) (organization-wide rules). Per-repo rules below provide project-specific details and **cannot override** organization rules.

## Project Overview

Special `calavia-org/.github` repository that provides the organization profile (`profile/README.md`). Its own repository-level GitHub Actions workflows live in `.github/workflows/`; all reusable workflows for the org are consumed from `calavia-org/workflows-lib`.

## Repository Layout

```
.
├── profile/README.md                 # Organization public profile
├── .github/workflows/                # This repo's own GitHub Actions workflows
│   ├── check_branch_name.yml
│   └── pr-check-and-test.yml
├── README.md
└── AGENTS.md
```

## Tech Stack

- Markdown
- YAML (GitHub Actions workflows)

## Linting & Formatting

```bash
pre-commit run --all-files
```

## CI/CD

- PR checks:
  - `.github/workflows/pr-check-and-test.yml` calls the org reusable `calavia-org/workflows-lib/.github/workflows/pr-check-and-test.yml@v0` (pre-commit + report).
  - `.github/workflows/check_branch_name.yml` enforces conventional branch prefixes.
- Release: none — this repo has no versioned artifact.

## Commits & Branches

- All commits follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`, `perf:`, `test:`, `build:`, `ci:`).
- Branches use conventional prefixes: `feat/`, `fix/`, `chore/`, `docs/`, `refactor/`, `test/`, `style/`, `perf/`, `ci/`, `major/`.
- Never commit directly to `main`/`master` — every change goes through a PR with squash merge only.

## Key Commands

| Task | Command |
|------|---------|
| Validate branch name locally | `grep -Eq '^(feat\|fix\|chore\|docs\|refactor\|test\|style\|perf\|ci\|major)/' <<< "$BRANCH"` |

## Gotchas & Special Cases

- Even though the repository is named `.github`, its own workflow files still live in the standard `.github/workflows/` directory relative to the repository root.
- `check_branch_name.yml` must allow every conventional prefix from `~/Development/Github/AGENTS.md` §2.

## References

- **profile/README.md**: organization profile
- **Related repos**: `calavia-org/org-standards`, `calavia-org/workflows-lib`

---

**Last Updated**: 2026-10-12
**Maintained By**: calavia-org
