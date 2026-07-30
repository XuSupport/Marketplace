# Filesystem Security

Filesystem permissions and path validation must be enforced by the backend/middleware, never only by a system prompt. Reject traversal and Windows absolute paths without crashing; POSIX absolute paths identify virtual filesystem locations. Keep human-approval configuration composable with permission-generated interrupts.

See `tests/unit_tests/test_file_system_tools_async.py` for concrete path-validation behavior.
