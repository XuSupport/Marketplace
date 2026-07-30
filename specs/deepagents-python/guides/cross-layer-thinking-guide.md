# Cross-Layer Thinking Guide

Trace a feature through its actual boundaries before coding:

```text
public SDK constructor
  -> graph assembly and middleware order
  -> model/tools/backend/checkpointer contracts
  -> LangGraph execution and persisted state
  -> CLI or terminal-agent configuration and user-visible behavior
```

Ask:

- Does the constructor change preserve exports, defaults, and positional compatibility?
- Does middleware ordering, replacement by `.name`, or an excluded profile change behavior?
- Does state remain serializable and compatible with existing checkpoints?
- Does a permission change enforce safety at runtime rather than only in prompts?
- Does a provider, command, or config change require a mirror update in another package?
- Which unit test proves the end-to-end contract without the network?

Document deliberate trade-offs in the PR when a change crosses package or release boundaries.
