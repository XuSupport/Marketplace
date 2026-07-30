# State, Persistence, and Permissions

LangGraph checkpointers and stores persist runtime state; filesystem operations pass through `BackendProtocol`. Do not access host paths directly from middleware.

```python
from langgraph.checkpoint.memory import InMemorySaver
from deepagents import create_deep_agent

agent = create_deep_agent(model=model, checkpointer=InMemorySaver())
result = agent.invoke(
    {"messages": "Summarize the repository."},
    config={"configurable": {"thread_id": "review-42"}},
)
```

- Preserve checkpoint-serializable state and the message delta reducer in `graph.py`.
- Enforce filesystem permissions and path validation in backend/middleware, not prompts. Traversal and Windows absolute paths return tool errors; POSIX absolute paths name virtual filesystem locations. See `tests/unit_tests/test_file_system_tools_async.py`.
- Merge permission-generated interrupts with user `interrupt_on` configuration; user settings take precedence.
