# Automations

This document describes the project's automations, where they live, and what they enforce.

## Local automations (Git hooks)

Git hooks are configured through `core.hooksPath`, pointing to `.githooks/`. Run `./setup-hooks.sh` once from the repository root to enable them.

| Hook file | Trigger | What it does |
|---|---|---|
| `.githooks/commit-msg` | `git commit` | Validates that the first line of the commit message follows [Conventional Commits](https://www.conventionalcommits.org/), using the format `type[(scope)][!]: description`. |

The local hook is a convenience for immediate feedback. The CI workflow also checks pull request titles so that the convention is validated for contributions made without the local hooks.

## Development environment

The repository includes two complementary ways to obtain the Node.js toolchain:

| File | Tool | What it does |
|---|---|---|
| `mise.toml` | Mise | Pins the Node.js and npm versions for local development. |
| `.node-version` | Node version file | Lets Node version managers and GitHub Actions use the same major version. |
| `flake.nix` | Nix | Provides a reproducible development shell. |
| `.envrc` | direnv | Enters the Nix development shell automatically after `direnv allow`. |

The Nix shell prepends the Mise shims to `PATH`, so Mise can manage the pinned versions when it is installed and enabled.

## Continuous integration

All GitHub Actions workflows live in `.github/workflows/`. Node.js is pinned to the version declared in `.node-version` and `mise.toml`.

### `ci.yml` — Core CI

**Trigger:** every push to `main` and every pull request. New commits to a branch cancel the previous run. The workflow can also be dispatched manually.

| Job | Tool | What it checks |
|---|---|---|
| PR title | `amannn/action-semantic-pull-request` | Pull request titles follow Conventional Commits. |
| Checks | npm scripts | Formatting, ESLint, Knip dependency analysis, TypeScript type checking, tests, and the production build. |

Dependencies are installed with `npm ci`, which requires the committed `package-lock.json` file.

### `security.yml` — Security audit

**Trigger:** pushes and pull requests to `main`, plus a weekly scheduled run. It can also be dispatched manually.

The workflow runs `npm audit --audit-level=high` against the locked dependency tree.

## Releases

### `release.yml` — Release pull request and GitHub release

**Trigger:** pushes to `main` and manual dispatch.

`googleapis/release-please-action` uses Conventional Commits to determine whether a release is needed. It opens or updates a release pull request, updates the package version and changelog, and creates a GitHub release when that pull request is merged.

## Configuration files

| File | Purpose |
|---|---|
| `package.json` | Package metadata, scripts, and development dependencies. |
| `package-lock.json` | Reproducible npm dependency resolution. |
| `tsconfig.json` | TypeScript compiler and declaration output settings. |
| `eslint.config.mjs` | ESLint flat configuration. |
| `.prettierrc.json` | Prettier formatting configuration. |
| `.editorconfig` | Editor-independent basic formatting conventions. |
| `knip.json` | Knip entry points and project files for dependency analysis. |
| `.githooks/commit-msg` | Local Conventional Commits validation. |
| `setup-hooks.sh` | Enables the repository's Git hooks. |
| `flake.nix` | Nix development shell. |
| `mise.toml` | Pinned Node.js and npm toolchain versions. |
