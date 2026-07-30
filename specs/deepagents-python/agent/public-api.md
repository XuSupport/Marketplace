# Public API, Types, and Errors

Exports in `libs/deepagents/deepagents/__init__.py`, constructor semantics, and persisted runtime behavior are compatibility commitments. Check tests, examples, docs, and sibling packages before changing them. Use the project's deprecation helper for staged removals.

Production functions use explicit Python annotations. Prefer `Protocol`, state subclasses, `TypedDict`, dataclasses, or Pydantic models to `dict[str, Any]`; keep LangChain/LangGraph generics intact at extension points. Use module loggers and specific exceptions—never bare `except`, debug `print`, or sensitive prompt/token logging.

```python
from collections.abc import Sequence
from langchain_core.tools import BaseTool

def normalize_tools(tools: Sequence[BaseTool]) -> list[BaseTool]:
    """Return a concrete tool list for one graph construction."""
    return list(tools)
```
