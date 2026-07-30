# Shared Python Guidelines

These rules apply across packages.

| Guide | Use when |
| --- | --- |
| [code quality](./code-quality.md) | every change |
| [Python typing](./typescript.md) | functions, state, protocols, external data |
| [dependencies](./dependencies.md) | package, lockfile, or interpreter changes |

Before a commit, run the focused package's `make test` and `make lint`; run targeted tests during development. Keep a bump-worthy user-facing change in one releasable component, because release automation scopes by changed path.
