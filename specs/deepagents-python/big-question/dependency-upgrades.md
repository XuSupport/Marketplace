# Dependency Upgrades

Dependencies are package-scoped. Start in the owning `pyproject.toml`, verify the supported Python range and sibling constraints, update the owning lockfile, then run that package's checks. Do not create cross-package lockfile churn in a user-facing release PR.

Use optional groups and lazy imports for providers/sandboxes that are not core runtime requirements.
