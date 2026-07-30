# Middleware Composition

Middleware ordering and `.name` are behavioral contracts: custom middleware with an existing name replaces that member in place, while new middleware is inserted according to the core-stack rules in `graph.py`. Preserve and test ordering when modifying the stack.

`FilesystemMiddleware` and `SubAgentMiddleware` are required because they implement file tools and task delegation. Do not make them silently excludable.

Use the contracts in `middleware/subagents.py` for delegation, including compiled LangGraph subagents. Extend existing middleware rather than recreating agent-loop behavior in an isolated graph.
