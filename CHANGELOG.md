# Changelog

## [1.2.0] - 2026-10-05

### Added

- Manual answer selection for context: `/context answers`, `exclude N...`,
  `include N...` and `keep-last`. User requests and the full transcript are
  retained; selection persists in sessions and archives without altering spent
  token totals. Answer headings display numbers and an exclusion marker.

### Fixed

- Tab completion and unique-prefix execution for `/context` subcommands,
  including `ans`/`answ` for `answers`. Ambiguous prefixes preserve the input
  and display candidates without performing an action.

## [1.1.0] - 2026-10-05

### Added

- Cumulative input/output token usage (`IN`/`OUT`) in the status line and `/tokens`
  details for the last request and current session. Counts restore with the
  conversation and include previous retry attempts; missing server statistics
  are marked with `?` or `+?`.
- `/system show [ROLE]` to inspect the active or specified prompt without changing
  the role or interrupting generation, with Tab completion for the role.

### Changed

- Successfully executed commands typed in the editor are saved alongside requests
  in persistent Ctrl+P/Ctrl+N history.
- Alt+Enter replaces Ctrl+Enter for sending requests and executing commands.
  Ctrl+G remains available; Enter inserts a newline. Legacy Escape-prefixed Enter,
  CSI-u and modifyOtherKeys encodings are supported. PuTTY users must disable
  `Window → Behaviour → Full screen on Alt-Enter` if enabled.
- One system role is selected at a time; additional requirements belong in the task
  text. Older sessions with combined roles restore the first role and retain the
  conversation, with a warning in the log.
- Keyboard disambiguation is enabled in terminals supporting kitty/CSI-u, with the
  previous mode restored on exit.

### Fixed

- Repeated usage updates replace an attempt's token counts without double counting;
  partial updates retain previously received usage fields.

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
