# Python Code Quality

- Use absolute imports, descriptive names, type annotations, and concise Google-style public docstrings.
- No bare `except`, `eval`, `exec`, or `pickle` on user-controlled data.
- Prefer an inline, justified `# noqa: RULE` to a file-wide exception. File-wide ruff ignores are only for categorical policy such as tests.
- Remove dead/commented code and do not swallow exceptions.
- Keep functions focused; extract helpers when complexity obscures behavior.

Tests should assert observable behavior and fail if the implementation breaks. Unit tests must not use the network. Do not decorate async tests with `pytest.mark.asyncio` because package configuration handles it.

Use Conventional Commit titles with a required scope, for example `fix(sdk): preserve middleware ordering`.
