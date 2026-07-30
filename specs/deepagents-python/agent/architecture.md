# Graph Assembly, Models, and Tools

`create_deep_agent` assembles a LangGraph agent with Deep Agents filesystem, subagent, skills, memory, and summarization middleware. Keep core behavior in `libs/deepagents/deepagents/`: graph assembly in `graph.py`, focused features in `middleware/`, backends in `backends/`, and profiles in `profiles/`.

Use an explicit model in new code; `model=None` is deprecated. Provider resolution belongs in `deepagents._models` and profiles, not unrelated middleware.

```python
from deepagents import create_deep_agent

agent = create_deep_agent(
    model="openai:gpt-5.5",
    tools=[search_documents],
    system_prompt="Research the supplied documents and cite evidence.",
)
```

Avoid eager provider imports, network calls, or filesystem scans during graph construction. Graph construction benchmarks live in `tests/benchmarks/test_benchmark_create_deep_agent.py`.
