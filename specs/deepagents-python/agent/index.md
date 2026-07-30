# Agent Runtime Guidelines

Applies primarily to `libs/deepagents/`. Read [architecture](./architecture.md) and [quality](./quality.md) for every SDK change. Read the focused guide when the change affects [middleware](./middleware.md), [state and permissions](./state-and-permissions.md), or [public APIs](./public-api.md).

`deepagents.create_deep_agent`, implemented in `deepagents/graph.py`, is the public construction entry point. It delegates to LangChain's `create_agent` and composes the Deep Agents middleware stack.

## Rules

- Preserve exported signatures; add public options as keyword-only parameters with safe defaults.
- Keep deterministic offline tests in `tests/unit_tests/` and network-enabled checks in `tests/integration_tests/`.
- Work in the owning package. `libs/code/` owns `dcode`; `libs/cli/` owns deployment commands.
