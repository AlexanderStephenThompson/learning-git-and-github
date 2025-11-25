# Visual Studio Code (VS Code) Guide

This guide covers the essentials of Visual Studio Code, a popular and powerful code editor that enhances your development workflow.

---

## Table of Contents

1. [What is VS Code?](#what-is-vs-code)
2. [Installation](#installation)
3. [Interface Overview](#interface-overview)
4. [Essential Features](#essential-features)
5. [Extensions](#extensions)
6. [Settings and Customization](#settings-and-customization)
7. [Integrated Terminal](#integrated-terminal)
8. [Git Integration](#git-integration)
9. [Debugging](#debugging)
10. [Tips and Tricks](#tips-and-tricks)

---

## What is VS Code?

Visual Studio Code (VS Code) is a free, open-source code editor developed by Microsoft. It's lightweight yet powerful, with features like:

- IntelliSense (smart code completion)
- Built-in Git integration
- Integrated terminal
- Debugging support
- Extensive extension marketplace
- Cross-platform (Windows, macOS, Linux)

---

## Installation

**Windows:**

1. Download from [code.visualstudio.com](https://code.visualstudio.com/)
2. Run the installer
3. Follow the setup wizard
4. Optionally add "Open with Code" to context menu

---

## Interface Overview

### Main Components

| Component | Description |
|-----------|-------------|
| **Activity Bar** | Left side icons for Explorer, Search, Git, Debug, Extensions |
| **Side Bar** | Shows content for selected activity (file tree, search results) |
| **Editor** | Main area for editing files, supports split views |
| **Panel** | Bottom area for Terminal, Output, Problems, Debug Console |
| **Status Bar** | Bottom bar showing file info, language, Git branch |

### Command Palette

Access all commands with `Ctrl + Shift + P`.

---

## Essential Features

### IntelliSense

VS Code provides intelligent code completion for many languages:

- Auto-completion suggestions
- Parameter hints
- Quick info on hover
- Go to Definition (`F12`)
- Find All References (`Shift + F12`)

### Multi-Cursor Editing

Edit multiple lines simultaneously:

- `Alt + Click` — Add cursor at click position
- `Ctrl + Alt + Up/Down` — Add cursor above/below
- `Ctrl + D` — Select next occurrence of word
- `Ctrl + Shift + L` — Select all occurrences

### Search and Replace

- `Ctrl + F` — Find in file
- `Ctrl + H` — Replace in file
- `Ctrl + Shift + F` — Search across all files
- `Ctrl + Shift + H` — Replace across all files

### File Navigation

- `Ctrl + P` — Quick Open file by name
- `Ctrl + Tab` — Switch between open files
- `Ctrl + G` — Go to line number
- `Ctrl + Shift + O` — Go to symbol in file

---

## Extensions

Extensions add functionality to VS Code. Access via the Extensions view (`Ctrl + Shift + X`).

### Recommended Extensions

| Extension | Purpose |
|-----------|---------|
| **GitLens** | Enhanced Git capabilities |
| **Prettier** | Code formatting |
| **ESLint** | JavaScript/TypeScript linting |
| **Python** | Python language support |
| **Live Server** | Local development server with live reload |
| **Docker** | Docker support |
| **Remote - SSH** | Edit files on remote machines |
| **Markdown All in One** | Markdown editing support |

### Installing Extensions

1. Open Extensions view (`Ctrl + Shift + X`)
2. Search for extension name
3. Click Install
4. Some extensions require reload

---

## Settings and Customization

### User Settings

Open settings with `Ctrl + ,` or via Command Palette.

**Common Settings:**

```json
{
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "editor.formatOnSave": true,
  "files.autoSave": "afterDelay",
  "terminal.integrated.fontSize": 13
}
```

### Themes

Change color theme: `Ctrl + K Ctrl + T`

Popular themes:

- One Dark Pro
- Dracula
- Material Theme
- GitHub Theme

### Keyboard Shortcuts

Customize shortcuts: `Ctrl + K Ctrl + S`

---

## Integrated Terminal

VS Code includes a built-in terminal.

### Terminal Shortcuts

| Shortcut | Action |
|----------|--------|
| `` Ctrl + ` `` | Toggle terminal |
| `Ctrl + Shift + `` ` | New terminal |
| `Ctrl + Shift + 5` | Split terminal |
| `Ctrl + PageUp/Down` | Switch terminals |

### Multiple Terminals

- Create multiple terminal instances
- Split terminals side by side
- Use different shells (PowerShell, Bash, cmd)

---

## Git Integration

VS Code has built-in Git support accessible via the Source Control view (`Ctrl + Shift + G`).

### Features

- View changed files
- Stage/unstage changes
- Commit with message
- Push/pull from remote
- View diff inline
- Create and switch branches
- Resolve merge conflicts

### Common Actions

1. **Stage changes:** Click `+` next to file or `+` next to "Changes"
2. **Commit:** Enter message in text box, click checkmark
3. **Push:** Click `...` menu → Push
4. **Pull:** Click `...` menu → Pull

---

## Debugging

VS Code provides powerful debugging capabilities.

### Setting Up Debugging

1. Open Run and Debug view (`Ctrl + Shift + D`)
2. Click "create a launch.json file"
3. Select environment (Node.js, Python, etc.)
4. Configure breakpoints and run

### Debug Controls

| Control | Action |
|---------|--------|
| `F5` | Start/Continue debugging |
| `F10` | Step Over |
| `F11` | Step Into |
| `Shift + F11` | Step Out |
| `Shift + F5` | Stop debugging |
| `F9` | Toggle breakpoint |

---

## Tips and Tricks

### Productivity Tips

1. **Zen Mode:** `Ctrl + K Z` — Distraction-free editing
2. **Side-by-Side Editing:** Drag tab to split editor
3. **Minimap:** Visual overview of code on right side
4. **Breadcrumbs:** Navigate file structure at top of editor
5. **Emmet:** Built-in for HTML/CSS expansion

### Useful Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + /` | Toggle line comment |
| `Alt + Up/Down` | Move line up/down |
| `Shift + Alt + Up/Down` | Copy line up/down |
| `Ctrl + Shift + K` | Delete line |
| `Ctrl + Enter` | Insert line below |
| `Ctrl + Shift + Enter` | Insert line above |
| `Ctrl + ]` / `Ctrl + [` | Indent/outdent line |

### Workspace Settings

Create `.vscode/settings.json` in your project for project-specific settings:

```json
{
  "editor.tabSize": 4,
  "files.exclude": {
    "node_modules": true
  }
}
```

---

## Further Resources

- **Official Documentation:** [code.visualstudio.com/docs](https://code.visualstudio.com/docs)
- **Keyboard Shortcuts PDF:** [Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- **VS Code Tips and Tricks:** [code.visualstudio.com/docs/getstarted/tips-and-tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
- **Extension Marketplace:** [marketplace.visualstudio.com](https://marketplace.visualstudio.com/vscode)

---

**Happy coding!** 💻
