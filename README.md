# ✨ Vibe - Your Autonomous AI Pair Programmer

**Vibe** is a lightweight, autonomous **AI Pair Programmer** for VS Code.

It's designed to act like a true assistant: Vibe can understand your project structure, read relevant files, write and edit code across multiple files, and even execute terminal commands to build, test, or run your project.

---

## 🤔 How It Works

Vibe operates with an "agentic" workflow, which makes it smarter and more efficient than a standard chat assistant.

> 1.  **Analyze Context**: When you make a request, Vibe first analyzes your project's **File Tree**, your **currently active file**, and any **selected code**.
> 2.  **Plan & Reason**: It decides which files it needs to read for full context or which commands it needs to run.
> 3.  **Execute Tools**: It uses its tools (`read_files`, `edit_file`, `run_terminal`) to perform the necessary actions.
> 4.  **Learn & Iterate**: Vibe reviews the output of its actions and continues the cycle until your request is complete.

This process allows Vibe to handle complex tasks like refactoring across multiple files or setting up a new feature from scratch.

### 🤖 Agentic Workflow
For complex tasks, Vibe uses a structured **Agentic Workflow** triggered by the `/plan` command or complex requests.
1.  **Task Tracking**: Creates a `.vibe/task.md` checklist in your workspace.
2.  **Implementation Plan**: Drafts a `.vibe/implementation_plan.md` for your approval before writing code.
3.  **Walkthrough**: Generates a `.vibe/walkthrough.md` report after completion.

---

## 🚀 Key Features

### ⌨️ Slash Commands
*   `/plan`: Start a complex task (Agentic Mode).
*   `/fix`: Debug and fix selected code.
*   `/explain`: Explain the selected code logic.

### ⚡ Multi-Provider Support
*   **Gemini, ChatGPT, DeepSeek, Grok**: Vibe now supports multiple AI providers.
*   **Dynamic Model Fetching**: Automatically fetches the latest available models from your provider.

### 🔄 Smart API Key Rotation
*   **Multiple Keys**: Add multiple API keys for each provider in your configuration.
*   **Auto-Retry & Fallback**: If a key hits a `429 Quota Exceeded` error, Vibe instantly and automatically switches to the next available key and retries the request. If all keys fail for a powerful model, it can even fall back to a faster one to get the job done.

### 🧠 Smart Context Awareness
*   **Token-Efficient File Tree**: Vibe analyzes your file structure first.
*   **Live Context Updates**: RAG Index automatically updates when you save, edit, or delete files.
*   **Manual Context Control**: You have full control over what Vibe reads. Drag and drop files or use `#file` to add them to the chat context.
*   **Selection-Aware**: Highlight any code block, and Vibe will focus its attention on that specific section.
*   **Project Sandbox**: Strictly limited to the current workspace.

### 🛡️ Safety & Security
*   **Native Undo Support**: All file edits are performed using VS Code’s native `WorkspaceEdit` API.
*   **Diff Previews**: Clear `diff` previews before applying changes.
*   **Terminal Policies**: Control terminal execution (Off/Auto/Turbo).

### 🎮 Enhanced UI
*   **Open File Button**: One-click access to files Vibe has just created or edited.
*   **Interactive Control Panel**: Switch providers, models, and policies instantly.

*   **Switch Provider & Models**: Instantly switch between providers and models.
*   **Set Policy**: Change the terminal execution policy on the fly.
*   **Manage Session**: Reload config or clear the AI's memory.

---

## 📖 Usage Guide

### 1. Configuration
1.  In the root of your project, create a file named **`.vibeconfig`**.
2.  Configure your providers and keys.

**Example `.vibeconfig`:**
```json
{
  "defaultProvider": "gemini",
  "providers": {
    "gemini": {
      "baseURL": "https://generativelanguage.googleapis.com/v1beta/",
      "apiKey": ["AIzaSy...Key1...", "AIzaSy...Key2..."],
      "defaultModel": "gemini-2.0-flash",
      "models": ["gemini-2.0-flash", "gemini-2.0-pro-exp"]
    },
    "chatgpt": {
      "baseURL": "https://api.openai.com/v1",
      "apiKey": ["sk-..."],
      "defaultModel": "gpt-4-turbo"
    },
    "deepseek": {
      "baseURL": "https://api.deepseek.com",
      "apiKey": ["sk-..."],
      "defaultModel": "deepseek-chat"
    },
    "grok": {
      "baseURL": "https://api.x.ai/v1",
      "apiKey": ["xai-..."],
      "defaultModel": "grok-beta"
    }
  }
}
```

### 2. Start a Chat
*   Open the VS Code Chat panel (usually in the sidebar).
*   Start your prompt with **`@vibe`**.

**Example Prompts:**
*   `@vibe create a simple Express server in server.js that serves "Hello, World!"`
*   `@vibe refactor the functions in 'src/utils/old-utils.js' to use modern async/await syntax and move them to 'src/utils/api-helpers.js'`
*   *(Highlight a block of buggy code)* `@vibe find and fix the bug in this selected code.`
*   `@vibe install the 'axios' package and then create a function in 'api.js' to fetch data from an endpoint.`

### 3. Use the Control Panel
*   Click the **`$(sparkle) Vibe: <Model> | 🛡️ <Policy>`** text in the bottom status bar.
*   From here, you can easily switch models or adjust the terminal policy.

---

## ⌨️ Commands

You can access these commands via the VS Code Command Palette (`Ctrl+Shift+P`):

| Command                      | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| **Vibe: Open Control Panel** | Opens the main Vibe menu in the status bar.                  |
| **Vibe: Switch Provider**    | Switch between configured AI providers (Gemini, ChatGPT, etc).|
| **Vibe: Switch Model**       | Shows a list of available models to switch to.               |
| **Vibe: Terminal Policy**    | Allows you to set the terminal execution policy (Off/Auto/Turbo). |
| **Vibe: Reload Models**      | Refreshes the list of available models and checks their status. |
| **Vibe: Clear Session**      | Clears the current chat history and resets the AI's memory.  |

---

## 🔧 Ignoring Files

To prevent Vibe from accessing sensitive or irrelevant files, you can add them to a `.vibeignore` file. The format is the same as `.gitignore`.

**Note:** Vibe automatically respects the rules in your project's `.gitignore` file.

**Example `.vibeignore`:**
```
# Vibe will ignore these files
package-lock.json
dist/
logs/
*.csv
secret_config.json
```

---

## 📬 Author

Vibe is proudly developed by **Mapcir**.

*   **Email**: `mapcir@outlook.com`

---

**Happy Coding with Vibe! 🚀**
