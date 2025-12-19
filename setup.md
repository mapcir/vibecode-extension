# 🚀 Installation & Setup

This guide will help you get started with Vibe Code in your project.

## 1. Installation

1. Open **VS Code**.
2. Go to the **Extensions** view (`Cmd+Shift+X`).
3. Search for **Vibe Code**.
4. Click **Install**.

## 2. Quick Workspace Setup

When you open a project folder for the first time, Vibe Code will detect it and offer a **Quick Setup**.

1. Click the **"Quick Setup"** button in the notification.
2. Vibe Code will automatically create three files in your root directory:
    - `.vibeconfig.json`: Main configuration (git-tracked).
    - `.vibeconfig.secrets.json`: Your API keys (automatically added to `.gitignore`).
    - `.vibeignore`: Files you want to exclude from AI indexing.

> [!TIP]
> If you missed the notification, you can run the setup manually by opening the Command Palette (`Cmd+Shift+P`) and typing **"Vibe: Setup Workspace"**.

## 3. Adding your API Keys

After running the setup, `.vibeconfig.secrets.json` will open automatically. 

1. Paste your API key into the appropriate provider section.
2. Example for Gemini:
```json
{
    "providers": {
        "gemini": {
            "apiKey": ["YOUR_REAL_API_KEY_HERE"]
        }
    }
}
```

> [!IMPORTANT]
> The `.vibeconfig.secrets.json` file is added to your `.gitignore` by the setup process to ensure your keys are never committed to version control.

## 4. Verify Connection

1. Open the Chat Panel (Click the **Vibe icon** in the activity bar).
2. Type a simple question like "Hello".
3. If configured correctly, the AI will respond.

---
[← Back to README](../README.md) | [Next: Configuration →](configuration.md)
