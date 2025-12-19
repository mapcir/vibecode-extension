# 🧠 Smart Context (RAG)

Vibe Code uses RAG (Retrieval-Augmented Generation) to give the AI a deep understanding of your codebase without sending your entire code and overwhelming the context window.

## How it works

1.  **Index**: Vibe Code scans your files and generates vector embeddings.
2.  **Store**: These embeddings are stored in a local cache (`.vibe/embeddings/`).
3.  **Retrieve**: When you ask a question, Vibe Code finds the most relevant code snippets and includes them in the conversation.

## Configuration

You can tune the RAG behavior in `.vibeconfig.json`:

```json
"rag": {
    "enabled": true,
    "indexOnStartup": true,
    "maxFiles": 500,
    "topK": 5
}
```

- **`enabled`**: Toggle the entire RAG feature.
- **`indexOnStartup`**: If true, Vibe Code scans your files in the background when you open a project.
- **`maxFiles`**: The maximum number of files to index (prevents slowing down huge repos).
- **`topK`**: Number of relevant code snippets to retrieve for each query.

## Commands

- **`Vibe: Index Codebase`**: Manually trigger a full scan of your project. Useful after large refactors or git pulls.

---
[← Security](security.md) | [Next: Proxy Configuration →](proxy.md)
