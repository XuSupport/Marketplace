# Python Typing Conventions

The historical filename remains for template compatibility; this guide is Python-specific.

```python
from collections.abc import Sequence

def names(items: Sequence[str]) -> list[str]:
    """Return normalized names without mutating the caller's sequence."""
    return [item.strip() for item in items]
```

- Use `list[str]`, `dict[str, str]`, `X | None`, and `collections.abc` interfaces.
- Provide explicit parameter and return types for production functions; tests may follow package-level ruff policy.
- Prefer `Protocol`, `TypedDict`, dataclasses, or Pydantic models for structured contracts rather than `dict[str, Any]`.
- Use `cast` only after a real runtime/framework guarantee and keep it local.
- Preserve variance and generics in LangChain/LangGraph extension points; do not erase them to `Any` for convenience.
