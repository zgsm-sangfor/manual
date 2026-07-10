---
sidebar_position: 2
---
# CSC Installation Guide (Beginner)

From opening the terminal to your first successful conversation — a step-by-step guide for beginners.

**For:** First-time CSC users on Windows, macOS, and Linux · **Updated:** 2026-07-03

> **TL;DR:** The core installation is a single command. Most computers with Node.js already installed will complete in about 3 minutes. If you need to install Node.js first, or if your company network has restrictions, it will take longer.

## Before You Start: 30-Second Self-Check

You'll need: a computer with internet access, a terminal (command prompt), and a CoStrict account.

Run the following commands in your terminal. Press Enter after each line:

```bash
node -v
npm -v
```

> Once you see version numbers like `v24.x.x` and `11.x.x`, you're good to go. If you see "command not found", skip to the **Troubleshooting** section item A.
>
> **Windows users** also need to see a git version number (e.g., `git version 2.x.x`). CSC requires Git Bash on Windows. If git is not recognized, install Git for Windows, then close and reopen your terminal.

## 3-Minute Setup

### Step 1: Install CSC

Copy the entire command, paste into your terminal, and press Enter. Wait for the installation to finish and the command prompt to reappear.

```bash
npm install -g @costrict/csc
```

If you see `npm ERR!` at the end or the installation is interrupted, see Troubleshooting. Regular warning messages are not installation failures.

### Step 2: Navigate to Your Project Folder

CSC uses the current folder as its working scope. Replace the path below with your project path:

```bash
cd /path/to/your/project
```

Don't know how to find the path? Type `cd ` (with a trailing space), then drag your project folder into the terminal and press Enter. No project yet? Create a test folder: `mkdir csc-test`, then `cd csc-test`.

### Step 3: Launch CSC

In your project directory, run:

```bash
csc
```

On success, you'll see the CSC welcome screen. Every time you use CSC, run `csc` from within your target project directory.

### Step 4: Sign In and Try It Out

On first launch, follow the prompts to sign in. Choose **CoStrict Enterprise Login** (officially recommended). If no login prompt appears, type `/login` in CSC.

After logging in, send this question:

> "Summarize this project's structure in one sentence"

CSC reads project files as needed — you don't need to add them individually. To change models, use `/model`. If unsure, keep the default. Login credentials are saved; use `/login` again to switch accounts.

> **Success criteria:** All three must be true: ① `csc` opens the interface; ② sign-in is complete; ③ the question above gets a response.

## First-Time Tips: 3 Things to Remember

- CSC works in whichever folder you run `csc` from. If you're in the wrong directory, exit and `cd` to the correct one.
- When CSC needs to modify files, it shows suggestions and asks for permission. Review what it plans to change before approving. If unsure, reject or ask follow-up questions.
- Type `/help` for help; type `exit` or press `Ctrl+D` to quit.

## Troubleshooting

Don't reinstall from scratch. Find the scenario that matches your screen and follow the corresponding steps.

| What You See | Steps to Take |
|---|---|
| **A. "npm not found"** | Node.js/npm isn't available. Visit the Node.js website and install the **LTS** version. Close and reopen your terminal, then run `node -v` and `npm -v` again. Once both show version numbers, return to Step 1. |
| **B. EACCES, permission denied** | **Windows:** Close the terminal, right-click and "Run as administrator", then retry. **macOS/Linux:** Use a Node version manager to reinstall Node/npm, or follow npm's official guide to move the global directory to your user directory. Don't use `sudo` as a first resort. |
| **C. "csc" command not found after install** | Close and reopen your terminal, then try `csc` again. If it still fails, re-run the install command and confirm there's no `npm ERR!`. Then run `npm config get prefix` and provide the result to your IT team — your npm global bin directory isn't in PATH. |
| **D. Download timeout / connection failed / certificate error** | Confirm your browser can reach the internet, then retry. Corporate networks, proxies, or VPNs may block npm. Try a different network, or ask IT to allow `registry.npmjs.org`. Don't disable system certificate verification. |
| **E. No login prompt / login interrupted** | Type `/login` in CSC and select CoStrict Enterprise Login. If the browser doesn't open automatically, check the terminal for a URL and open it manually; complete the web flow and return to the terminal. If it still fails, verify your CoStrict account and corporate network. |
| **F. CSC opened but sees the wrong project** | Type `exit` to quit. Use `cd` to navigate to the correct project folder, then run `csc` again. If unsure of your current location: `pwd` (macOS/Linux) or `Get-Location` (Windows PowerShell). |
| **G. Windows: command execution fails / "bash not found"** | CSC on Windows needs Git for Windows for the Git Bash environment. Run `git --version` in the terminal. If not found, install Git for Windows, close and reopen the terminal, then retry `git --version` and `csc`. If git shows a version but CSC still fails, screenshot the error and send it to support, noting: "CSC on Windows requires Git Bash." |

## Third-Party API Direct Login

This is not the default path for beginners. Only use this if your administrator or provider has given you all of the following: Base URL, API Key, Haiku Model, Sonnet Model, Opus Model. If anything is missing, register a CoStrict account instead.

> **Security reminder:** API Keys are like passwords. Never share them in chat, screenshots, or project code.

## Reinstall or Uninstall

**Reinstall/Update:** Run the install command from Step 1 again.

**Complete uninstall:**
```bash
npm uninstall -g @costrict/csc
```
