# Dependencies and Environments

Each `libs/*` package owns its `pyproject.toml`, lockfile, Python range, and release version. Use `uv sync` and `uv run`; never invoke `pip`, `poetry`, or `conda`.

- Install dependencies explicitly with `uv sync --all-groups` (or the appropriate group) before running checks.
- Do not add dependencies unless needed; prefer installed framework utilities and document why a new dependency is warranted.
- Update dependencies and the owning lockfile together, then run the package checks and `make -C libs lock-check` when lockfiles change.
- Optional provider/sandbox integrations belong in the relevant optional dependency group and should remain lazily imported.

Do not assume one global Python version: follow the changed package's `requires-python`.
