# Changelog

## [1.0.0] - 2026-10-04

First release of llm-tui, a terminal client for engineering conversations with local LLMs.

### Added

- Single executable Python 3.8+ script using the standard library and curses.
- llama.cpp and vLLM backends, model selection, streamed responses, cancellation and retry.
- Automatic context discovery, token counting, response token reservation and history trimming.
- System roles, sampling settings and model thinking controls where supported.
- Full reasoning display or an animated Thinking indicator with character count and elapsed time.
- Session restoration, archives, input history and draft persistence.
- UTF-8 source files, aliases and per-request attachments with optional line ranges.
- Transcript navigation and text selection across multiple screens; clipboard transfer through local utilities or OSC52.
- Saving selections with `f` to `save-<date-time>.clb` files; answer and code block export without overwriting existing files.
- Russian help and shortcuts supporting Russian keyboard layouts and Caps Lock.
- Configurable storage, data and log directories; session locking, atomic saves and rotating logs.
- Version displayed in the TUI header and available through `--version`.
- Built-in headless checks through `--self-test`.

### Fixed

- Function keys preserve panel focus; new requests remain visible after command output.
- llama.cpp router context discovery and token counting use the selected model. Metadata requests allow time for model loading.
- Command results and notifications scroll to their final line. Manual scrolling remains stable across redraws and streamed response updates.

