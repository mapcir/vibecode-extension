# ⚙️ Configuration Guide

Vibe Code uses `.vibeconfig.json` for persistent, project-level settings.

## Core Settings

| Field | Type | Description |
| :--- | :--- | :--- |
| `defaultProvider` | string | The AI provider used by default (e.g., "gemini", "chatgpt"). |
| `proxy` | string | URL for proxy server (e.g., "http://..." or "socks5://..."). |

## Providers

Each provider (gemini, chatgpt, claude, deepseek, ollama) can be configured individually:

```json
"providers": {
    "gemini": {
        "baseURL": "https://...",
        "method": "POST",
        "headers": {
            "Content-Type": "application/json"
        },
        "defaultModel": "gemini-2.5-flash",
        "models": { ... }
    }
}
```

### Advanced Provider Fields
- **`method`**: Custom HTTP method (default: POST).
- **`headers`**: Custom HTTP headers. Useful for custom proxies or specific API requirements. 
    - *Tip*: You can use placeholders like `${OPENAI_API_KEY}` which will be resolved from your secrets file.
- **`models`**: Define available models and their capabilities (`contextWindow`, `supportsImages`, `tags`).

## Terminal Policy

Controls the AI's ability to run terminal commands.

```json
"terminalPolicy": {
    "safe": {
        "blockedCommands": ["rm -rf", "sudo"],
        "autoTest": true
    },
    ...
}
```
- **Modes**: Choose from `Safe`, `Turbo`, or `Off` in the control panel.

## Authority Modes

Vibe Code respects your authority. Configuration for these modes can be found in `.vibeconfig.json`:

- **Autonomous**: Plan, Execute, Verify.
- **Collaborative**: Propose, Review, Approve.
- **Smart**: AI decides based on risk.
- **Optimistic**: Execute and revert if failed.

---
[← Setup](setup.md) | [Next: Security & Secrets →](security.md)
