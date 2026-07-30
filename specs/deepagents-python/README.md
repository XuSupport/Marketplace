# Deep Agents Python Development Guidelines

Reusable guidance for the Deep Agents Python monorepo. It records the patterns used by the core SDK, deployment CLI, and terminal coding agent; it is not a generic web-application template.

## Structure

- [Agent runtime](./agent/index.md): `libs/deepagents/` graph assembly, middleware, backends, and public APIs.
- [Shared Python practices](./shared/index.md): typing, dependencies, tests, linting, and release boundaries.
- [Thinking guides](./guides/index.md): pre-change and cross-layer checks.
- [Decision records](./big-question/index.md): recurring high-risk design questions.

## Project map

`libs/deepagents/` is the SDK; `libs/code/` owns the `dcode` interactive coding agent; `libs/cli/` owns `deepagents init`, `dev`, and `deploy`; `libs/acp/`, `libs/evals/`, and `libs/partners/` are separate packages. Work in the package that owns the behavior and run that package's `Makefile` targets. For `libs/code/` or `libs/cli/` work, also read the relevant package-local `AGENTS.md` or `DEVELOPMENT.md`.

Use `uv`, never `pip`, `poetry`, or an ad-hoc virtual environment. See `AGENTS.md` and `libs/DEVELOPMENT.md` before changing code.
