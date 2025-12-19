# 🔒 Security & Secrets

Vibe Code is built with security as a priority. We use a **Bring Your Own Key (BYOK)** model—your data never goes through our servers.

## 1. Secrets Management

All sensitive information should be stored in `.vibeconfig.secrets.json`. This file is:
- **Gitignored**: The setup process automatically adds it to your `.gitignore`.
- **Local-only**: It exists only on your machine.

### Automatic Variable Resolution
When you add an API key to the `providers` section of your secrets file, it automatically becomes available as a variable.
- `chatgpt.apiKey` → `${OPENAI_API_KEY}`
- `gemini.apiKey` → `${GEMINI_API_KEY}`

You can use these variables in your `.vibeconfig.json` headers:
```json
"headers": {
    "Authorization": "Bearer ${OPENAI_API_KEY}"
}
```

## 2. Environment Variables

If a variable is not found in your secrets file, Vibe Code will look for it in your system's environment variables. This is useful for CI/CD or shared development environments.

## 3. Placeholder Protection

Vibe Code has a built-in safety mechanism. If an API key is still set to a placeholder value (e.g., `YOUR_GEMINI_API_KEY_HERE`), the system will:
1.  Automatically "strip" the value (treating it as an empty string).
2.  Stop any API calls before they happen.
3.  Log a single clear warning instead of multiple 401/403 errors.

## 4. Why we warn about keys in `.vibeconfig.json`

If the extension detects hardcoded keys in `.vibeconfig.json`, it will show a warning in the logs. This is because `.vibeconfig.json` is typically committed to Git, and accidentally committing an API key is a significant security risk.

---
[← Configuration](configuration.md) | [Next: RAG & Indexing →](rag.md)
