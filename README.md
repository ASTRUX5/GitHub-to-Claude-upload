# 🤖 Claude → GitHub Auto-Upload Bridge

> Upload, update, and delete files in any GitHub repo — directly from the **Claude mobile app**. No VS Code. No terminal. No Claude Code.

![Claude](https://img.shields.io/badge/Claude-Mobile%20App-blueviolet?style=for-the-badge)
![Supabase](https://img.shields.io/badge/Supabase-Edge%20Functions-3ECF8E?style=for-the-badge&logo=supabase)
![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

---

## 🧠 How It Works



---

## ✨ Features

| Feature | Status |
|---|---|
| Upload files to any repo | ✅ |
| Update existing files | ✅ |
| Delete files | ✅ |
| Create new repos | ✅ |
| Works from Claude mobile app | ✅ |
| No terminal required | ✅ |
| No VS Code required | ✅ |
| No Claude Code required | ✅ |

---

## 🏗️ Architecture

### 1. Supabase
- **github_sync** table — queues file operations from Claude
- **github-trigger** Edge Function — receives payload and dispatches to GitHub Actions
- **pg_net** extension — enables SQL to make HTTP calls

### 2. GitHub Actions
- Triggered via  event
- Clones target repo using PAT
- Writes or deletes the specified file
- Marks record as done in Supabase

### 3. Claude
- Uses Supabase MCP connector
- Pure natural language — no code execution needed

---

## 🔐 Required Secrets

### GitHub Actions Secrets
| Secret | Description |
|---|---|
|  | Classic PAT with  and  scopes |
|  | Your Supabase project URL |
|  | Supabase anon public key |

### Supabase Edge Function Secrets
| Secret | Description |
|---|---|
|  | Same GitHub PAT |
|  | Your GitHub username |
|  | This repo name |

---

## 🚀 Usage

Just tell Claude:

- *Upload this file to repo X*
- *Delete file Y from repo Z*
- *Create a new repo called W and add these files*

Claude handles the rest automatically.

---

## 📁 Repo Structure



---

*Built entirely using the Claude mobile app. Not a single line typed in an IDE.*