# Changelog

## 2026-04-27

### Added

- **OpenAI/GPT model support** — `agent.py` now supports both Anthropic (Claude) and OpenAI (GPT) models hosted in Microsoft Foundry via a `MODEL_PROVIDER` environment variable.
- **`azure-identity`** added to `requirements.txt` for `DefaultAzureCredential` authentication with OpenAI-based Foundry deployments.
- **`.env.sample`** updated with documented configuration blocks for both Anthropic and OpenAI providers.

### Changed

- `agent.py` — Extracted client creation into `_create_chat_client()` which switches between `AnthropicFoundryClient` and `FoundryChatClient` based on `MODEL_PROVIDER` env var. Defaults to `anthropic` for backwards compatibility.
- `open("instructions.md")` now uses `encoding="utf-8"` for cross-platform robustness.

### Validated

- E2E tested with `gpt-5-1` deployment on `leestott-build-resource` (Sweden Central):
  - Hello world (no tools) — PASS
  - MCP Cupcake Store connection — PASS
  - Tool-calling (list flavours, place order) — PASS
