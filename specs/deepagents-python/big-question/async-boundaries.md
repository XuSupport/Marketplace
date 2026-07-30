# Async Boundaries

Do not block the event loop with network, filesystem, or process work on startup or interactive paths. Give background work explicit ownership, cancellation, cleanup, and error reporting. Test cancellation and resource cleanup, not just success.

Package pytest configuration handles async tests automatically; avoid redundant markers.
