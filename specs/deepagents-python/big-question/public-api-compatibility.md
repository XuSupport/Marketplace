# Public API Compatibility

Exports from `deepagents/__init__.py`, documented CLI flags, and persisted configuration are public contracts. Prefer additive keyword-only parameters, stable defaults, and a deprecation period over removal or semantic reuse.

Before changing one, search tests, examples, docs, and sibling packages. Add tests for old and new call patterns when compatibility is intentional.
