# Pre-Implementation Checklist

Before editing:

1. Identify the owning package and read its `AGENTS.md`/`DEVELOPMENT.md` if present.
2. Search for the target symbol, command, registry, tests, and public exports with `rg` in targeted paths.
3. Determine whether the change is public API, durable state, a permission boundary, or a release-worthy behavior change.
4. Find a real nearby implementation and test pattern.
5. Plan the narrowest validation: focused unit test plus the owning package's lint/type check.

For public API changes, check `__init__.py`, examples, docs, and sibling package imports before changing a signature. For provider/platform registries, search all mirrors first. For dependencies, inspect the package `pyproject.toml` and lockfile before editing.
