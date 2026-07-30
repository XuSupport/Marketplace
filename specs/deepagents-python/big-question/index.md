# Recurring Design Decisions

Read a focused decision record when a change risks API compatibility, async correctness, dependency fan-out, or filesystem safety.

| Record | Question |
| --- | --- |
| [public API compatibility](./public-api-compatibility.md) | Can callers keep using this interface? |
| [async boundaries](./async-boundaries.md) | Is this safe for the event loop and cancellation? |
| [dependency upgrades](./dependency-upgrades.md) | Which package and lockfiles own this upgrade? |
| [filesystem security](./filesystem-security.md) | Is filesystem access enforced at runtime? |
