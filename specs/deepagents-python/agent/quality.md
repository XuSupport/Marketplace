# Agent Runtime Quality

Every feature or bugfix needs deterministic unit coverage. Prefer `GenericFakeChatModel` from `tests/unit_tests/chat_model.py` over network calls and broad mocks. Async tests use package `asyncio_mode = "auto"`; do not add `@pytest.mark.asyncio`.

Run from `libs/deepagents/`:

```bash
make test TEST_FILE=tests/unit_tests/test_graph.py
make lint
```

Test observable behavior, configuration precedence, and tool-facing error messages. Use integration tests only when the behavior genuinely needs the network. Public functions use concise Google-style docstrings.
