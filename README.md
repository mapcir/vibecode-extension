# Vibe Code - The AI Partner That Respects Your Authority

<div align="center">

![Vibe Code Icon](icon.png)

**Professional AI Pair Programmer for VS Code**  
*Control. Precision. Automation.*

[![Install](https://img.shields.io/badge/Install-VS%20Code-blue)](https://marketplace.visualstudio.com/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE.md)

</div>

---

## 🚀 Why Vibe Code?

Most AI coding assistants act like eager interns—they type fast but often break things. **Vibe Code** is different. It is built for **Professional Developers** who demand control, yet offers powerful automation for when you just want things done.

We operate on a strict **Authority Contract**: *The AI does exactly what you permit it to do, and nothing more.*

### 🎯 For the Senior Developer (Control & Precision)
*   **🚫 No Blind Edits**: in **Collaborative Mode**, the AI *proposes* changes (Diff View). You review. You approve. Only then is code written.
*   **🛡️ Terminal Policy**: Granular control over shell execution. Block `rm -rf`, allow `npm test`. No surprises.
*   **🔒 Bring Your Own Key (BYOK)**: Use your own Gemini, OpenAI, or DeepSeek API keys. No middleman. No data harvesting.
*   **🏢 Enterprise Ready**: Full SOCKS5/HTTP Proxy support and detailed logging.

### ⚡ For the Junior Developer (Speed & Automation)
*   **🤖 Autonomous Mode**: Give a high-level goal (e.g., "Write tests for this file"), and watch Vibe Code plan, write, and verify independently.
*   **🧠 RAG Context**: The AI reads your entire codebase to understand project structure, imports, and style automatically.
*   **� One-Click Setup**: Auto-detects your environment and configures itself instantly.

---

## 🧠 Authority Modes

Choose the level of autonomy that fits your current task:

| Mode | Behavior | Best For |
| :--- | :--- | :--- |
| **🤝 Collaborative** (Default) | **Propose → Review → Approve.** The AI is a partner. It suggests changes but waits for your explicit click to apply them. | Core architecture, Refactoring, Critical Bug Fixes. |
| **🤖 Autonomous** | **Plan → Execute → Verify.** The AI takes the lead. It iterates, runs commands, and fixes its own errors until the task is done. | Writing Tests, Boilerplate, Documentation, Simple Scripts. |
| **🔍 Reviewer** | **Read Evaluation.** The AI cannot edit code. It only analyzes, finds bugs, and suggests improvements. | Code Review, Security Audit, Learning. |

> **Tip:** Toggle modes instantly from the Status Bar or Control Panel.

---

## ⚙️ Quick Start

1.  **Install** Vibe Code from the VS Code Marketplace.
2.  **Open** any project folder.
3.  **Setup Notification** will appear. Click **"Quick Setup"**.
    *   This creates `.vibeconfig` and `.vibeconfig.secrets.json`.
4.  **Add API Key**: The secrets file will open automatically. Paste your API key (Gemini, OpenAI, etc.).

```json
// .vibeconfig.secrets.json (Gitignored by default)
{
  "providers": {
    "gemini": {
      "apiKey": ["YOUR_GEMINI_API_KEY"]
    }
  }
}
```

5.  **Start Chatting**: Press `Cmd+L` (or open the Vibe icon in the sidebar).

---

## 🛠️ Configuration

### 1. API Keys (Model Agnostic)
Vibe Code supports multiple providers. We recommend using **Google Gemini 2.0 Flash** for the best balance of speed, cost, and window context.

Supported Providers:
*   **Google Gemini** (Recommended, Free Tier available)
*   **OpenAI** (GPT-4o, GPT-3.5)
*   **Anthropic** (Claude 3.5 Sonnet)
*   **DeepSeek** (DeepSeek Coder V2)
*   **Ollama / Local LLM** (Privacy-focused)

### 2. Terminal Policy
Control how the AI interacts with your shell in `.vibeconfig.json`:

```json
{
  "terminalPolicy": {
    "mode": "Safe", // Options: "Off", "Safe", "Turbo"
    "blockedCommands": ["rm -rf", "sudo", "format"],
    "maxExecutionTime": 30000
  }
}
```
*   **Safe**: Blocks dangerous commands, asks confirmation for others.
*   **Turbo**: Auto-executes everything (use with caution in Autonomous mode).
*   **Off**: Always asks for permission.

### 3. Proxy Support
Perfect for corporate environments. Add to `.vibeconfig.json`:
```json
{
  "proxy": "socks5://127.0.0.1:1080"
}
```

---

## 💡 Key Features Highlight

### 📚 Smart Context (RAG)
Vibe Code indexes your codebase locally. It knows your types, your utils, and your coding style without you having to copy-paste snippets.
*   **Command**: `Vibe: Index Codebase` to refresh the knowledge base manually (it also updates automatically on file changes).

### 💰 Token Savings
The extension intelligently trims chat history and summarizes context to keep API costs low without losing the "thread" of the conversation.

### � Auto-Recovery
If an API request fails (Rate Limit 429), Vibe Code automatically:
1.  **Rotates API Keys** (if you provided multiple).
2.  **Switches Models** (falls back to cheaper/faster models).
3.  **Retries** with exponential backoff.

---

## ⌨️ Commands

| Command | Description |
| :--- | :--- |
| `Vibe: Open Chat` | Open the main chat interface. |
| `Vibe: Setup Workspace` | Generate config files for the current folder. |
| `Vibe: Index Codebase` | Scan files for RAG context. |
| `Vibe: Terminal Policy` | Quickly switch between Safe/Turbo/Off modes. |
| `Vibe: Switch Model` | Change the active AI model on the fly. |

---

## 🤝 Contributing & Support

We are open source! Issues and Pull Requests are welcome.
*   **Repo**: [github.com/mapcir/vscode-vibecode](https://github.com/mapcir/vscode-vibecode)
*   **Feedback**: Open an issue on GitHub.

---

**Made for Builders.**
