# Claude Code – Custom Provider Guide

> Route Claude Code to any OpenAI-compatible endpoint (MegaLLM, Minimax, Ollama, OpenRouter, etc.) with a single config file. No monkey-patching, no wrappers — just env vars.

---

## Why this exists

Most guides spend pages talking about agents and architecture.  
Nobody just tells you **how to point Claude Code at a different backend**.  
This file does exactly that.

---

## How it works

Claude Code reads environment variables to decide which API endpoint and model to call.  
Override them per-project via `.claude/settings.json` → `env` block, and Claude Code will use your provider instead of Anthropic's servers.

```
.claude/
└── settings.json   ← lives in your project root (add to .gitignore if token is hardcoded)
```

> 💡 **Tip:** Use a secrets manager or shell env vars for tokens in shared repos. The `env` block in `settings.json` is for convenience on local machines.

---

## Minimal template

```jsonc
// .claude/settings.json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://<provider-base-url>",
    "ANTHROPIC_AUTH_TOKEN": "<your-api-token>",
    "ANTHROPIC_MODEL": "<default-model-id>",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "<opus-equivalent>",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "<sonnet-equivalent>",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "<haiku-equivalent>"
  }
}
```

| Variable | Purpose |
|---|---|
| `ANTHROPIC_BASE_URL` | Override the API host |
| `ANTHROPIC_AUTH_TOKEN` | Bearer token sent in `Authorization` header |
| `ANTHROPIC_MODEL` | Model used when no tier is specified |
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | Mapped when Claude Code requests the "Opus" tier |
| `ANTHROPIC_DEFAULT_SONNET_MODEL` | Mapped when Claude Code requests the "Sonnet" tier |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | Mapped when Claude Code requests the "Haiku" tier |
| `ANTHROPIC_SMALL_FAST_MODEL` | Mapped for lightweight/fast calls |
| `API_TIMEOUT_MS` | Request timeout in milliseconds (useful for slow local models) |

---

## Providers

### 🔹 MegaLLM

> Docs: https://docs.megallm.io/en/agents/claude

Claude-native proxy — supports real Anthropic model IDs.

```jsonc
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://ai.megallm.io/v1",
    "ANTHROPIC_AUTH_TOKEN": "<megallm-token>",
    "ANTHROPIC_MODEL": "claude-opus-4-6",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "claude-opus-4-6",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "claude-sonnet-4-5",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "claude-sonnet-4-5"
  }
}
```

---

### 🔹 Minimax

> Docs: https://platform.minimax.io/docs/token-plan/claude-code

Routes all tiers to Minimax's own model (`MiniMax-M2.7`). Also sets a generous timeout for long agentic tasks.

```jsonc
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "<minimax-token>",
    "ANTHROPIC_MODEL": "MiniMax-M2.7",
    "ANTHROPIC_SMALL_FAST_MODEL": "MiniMax-M2.7",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "MiniMax-M2.7",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMax-M2.7",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2.7",
    "API_TIMEOUT_MS": "3000000",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
  }
}
```

---

### 🔹 Ollama (local)

> Docs: https://ollama.com/blog/openai-compatibility

Run models 100% offline. Start Ollama first (`ollama serve`), then pull a model (`ollama pull qwen2.5-coder:32b`).

```jsonc
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://localhost:11434/v1",
    "ANTHROPIC_AUTH_TOKEN": "ollama",
    "ANTHROPIC_MODEL": "qwen2.5-coder:32b",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "qwen2.5-coder:32b",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "qwen2.5-coder:14b",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "qwen2.5-coder:7b",
    "API_TIMEOUT_MS": "600000"
  }
}
```

> ⚠️ Ollama's OpenAI-compatible endpoint (`/v1`) does **not** implement the Anthropic Messages API natively. You may need a shim like [litellm](https://github.com/BerriAI/litellm) or [anthropic-proxy](https://github.com/7rulnik/anthropic-proxy) in front of Ollama.

---

### 🔹 OpenRouter

> Docs: https://openrouter.ai/docs

Access 200+ models (GPT-4o, Gemini, Llama, Mistral…) through a single endpoint and API key.

```jsonc
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api/v1",
    "ANTHROPIC_AUTH_TOKEN": "<openrouter-api-key>",
    "ANTHROPIC_MODEL": "anthropic/claude-opus-4",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "anthropic/claude-opus-4",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "anthropic/claude-sonnet-4-5",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "google/gemini-flash-1.5"
  }
}
```

> 💡 Mix providers per tier — e.g. use Gemini Flash for Haiku-tier calls (cheap/fast) and Claude Opus for heavy reasoning.

---

### 🔹 LiteLLM (self-hosted gateway)

> Docs: https://docs.litellm.ai/docs/proxy/quick_start

Run a local proxy that translates Anthropic API calls to any backend (Ollama, Azure, Bedrock, Vertex, etc.).

```jsonc
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://localhost:4000",
    "ANTHROPIC_AUTH_TOKEN": "<litellm-master-key>",
    "ANTHROPIC_MODEL": "claude-opus-4",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "claude-opus-4",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "claude-sonnet-4-5",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "claude-haiku-3-5"
  }
}
```

Start LiteLLM proxy:
```bash
litellm --model ollama/qwen2.5-coder --port 4000
```

---

## CLI / Desktop (global override)

For Claude Code CLI or Desktop, set env vars globally instead of per-project:

### Shell (bash / zsh)

```bash
# ~/.bashrc or ~/.zshrc
export ANTHROPIC_BASE_URL="https://ai.megallm.io/v1"
export ANTHROPIC_AUTH_TOKEN="<token>"
export ANTHROPIC_MODEL="claude-opus-4-6"
```

### Windows (PowerShell)

```powershell
$env:ANTHROPIC_BASE_URL = "https://ai.megallm.io/v1"
$env:ANTHROPIC_AUTH_TOKEN = "<token>"
$env:ANTHROPIC_MODEL = "claude-opus-4-6"
```

### Windows (System Environment Variables)

Set via **System Properties → Environment Variables** for persistence across sessions.

---

## .gitignore reminder

If your token is hardcoded in `settings.json`, exclude it from version control:

```gitignore
.claude/settings.json
```

Alternatively, keep `settings.json` in git but leave `ANTHROPIC_AUTH_TOKEN` empty and export it from your shell instead.

---

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| `401 Unauthorized` | Wrong or missing token | Check `ANTHROPIC_AUTH_TOKEN` |
| `404 Not Found` | Wrong base URL or model ID | Verify `ANTHROPIC_BASE_URL` and model name in provider docs |
| Request hangs / times out | Slow local model | Increase `API_TIMEOUT_MS` (e.g. `"600000"` = 10 min) |
| Claude Code ignores `settings.json` | Wrong file location | Must be `.claude/settings.json` in project root, not home dir |
| Ollama returns format errors | API schema mismatch | Add a shim (LiteLLM or anthropic-proxy) between Ollama and Claude Code |

---

## Contributing

Found a new provider that works? PRs welcome — just add a new `###` section following the template above.
