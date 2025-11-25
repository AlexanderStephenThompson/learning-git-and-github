# Command Line Interface (CLI) Basics

This guide will help you become comfortable working in the terminal, covering essential commands and concepts for both Windows PowerShell and Unix-like shells (Git Bash, Linux, macOS).

---

## Table of Contents

1. [What is the CLI?](#what-is-the-cli)
2. [Opening the Terminal](#opening-the-terminal)
3. [Basic Navigation](#basic-navigation)
4. [File and Directory Operations](#file-and-directory-operations)
5. [Viewing and Editing Files](#viewing-and-editing-files)
6. [PowerShell vs Bash](#powershell-vs-bash)
7. [Tips and Shortcuts](#tips-and-shortcuts)
8. [Common Patterns](#common-patterns)

---

## What is the CLI?

The Command Line Interface (CLI) is a text-based way to interact with your computer. Instead of clicking buttons and icons, you type commands to perform tasks. It's powerful, fast, and essential for working with Git and development tools.

**Why use the CLI?**
- Faster for repetitive tasks
- More control and precision
- Required for Git and many development tools
- Automatable with scripts
- Universal across operating systems

---

## Opening the Terminal

**Windows:**
- **PowerShell:** Press `Win + X`, then select "Windows PowerShell" or "Terminal"
- **Command Prompt:** Press `Win + R`, type `cmd`, press Enter
- **Git Bash:** Right-click in a folder → "Git Bash Here" (if Git is installed)

**macOS:**
- Press `Cmd + Space`, type "Terminal", press Enter
- Or go to Applications → Utilities → Terminal

**Linux:**
- Press `Ctrl + Alt + T`
- Or search for "Terminal" in your applications menu

---

## Basic Navigation

### Current Directory

**PowerShell/CMD:**
```powershell
pwd
# Or
Get-Location
```

**Bash:**
```bash
pwd
```

### List Files and Directories

**PowerShell:**
```powershell
ls
# Or
Get-ChildItem
# Show hidden files
ls -Force
```

**Bash:**
```bash
ls
# Show hidden files
ls -a
# Long format with details
ls -la
```

### Change Directory

**PowerShell/Bash:**
```bash
cd Documents
cd ..           # Go up one level
cd ~            # Go to home directory
cd /            # Go to root (Bash) or drive root (PowerShell)
cd -            # Go to previous directory (Bash only)
```

**PowerShell specific:**
```powershell
Set-Location Documents
cd C:\Users\YourName\Documents
```

---

## File and Directory Operations

### Creating Directories

**PowerShell:**
```powershell
mkdir my-folder
# Or
New-Item -ItemType Directory -Name my-folder
```

**Bash:**
```bash
mkdir my-folder
# Create nested directories
mkdir -p parent/child/grandchild
```

### Creating Files

**PowerShell:**
```powershell
New-Item -ItemType File -Name myfile.txt
# Or create with content
"Hello World" | Out-File myfile.txt
```

**Bash:**
```bash
touch myfile.txt
# Or create with content
echo "Hello World" > myfile.txt
```

### Copying Files

**PowerShell:**
```powershell
Copy-Item source.txt destination.txt
# Copy directory recursively
Copy-Item -Recurse my-folder new-folder
```

**Bash:**
```bash
cp source.txt destination.txt
# Copy directory recursively
cp -r my-folder new-folder
```

### Moving/Renaming Files

**PowerShell:**
```powershell
Move-Item oldname.txt newname.txt
Move-Item file.txt C:\Users\YourName\Documents\
```

**Bash:**
```bash
mv oldname.txt newname.txt
mv file.txt ~/Documents/
```

### Deleting Files and Directories

**PowerShell:**
```powershell
Remove-Item file.txt
# Delete directory recursively
Remove-Item -Recurse my-folder
# Force delete (no confirmation)
Remove-Item -Force -Recurse my-folder
```

**Bash:**
```bash
rm file.txt
# Delete directory recursively
rm -r my-folder
# Force delete (be careful!)
rm -rf my-folder
```

---

## Viewing and Editing Files

### View File Contents

**PowerShell:**
```powershell
Get-Content file.txt
# Or
cat file.txt
# View first 10 lines
Get-Content file.txt -Head 10
# View last 10 lines
Get-Content file.txt -Tail 10
```

**Bash:**
```bash
cat file.txt
# View with paging
less file.txt
# View first 10 lines
head file.txt
# View last 10 lines
tail file.txt
```

### Search File Contents

**PowerShell:**
```powershell
Select-String "search term" file.txt
# Search in multiple files
Select-String "search term" *.txt
```

**Bash:**
```bash
grep "search term" file.txt
# Search recursively in directory
grep -r "search term" .
```

### Edit Files

**PowerShell:**
```powershell
notepad file.txt
# Or open in VS Code
code file.txt
```

**Bash:**
```bash
nano file.txt    # Simple editor
vim file.txt     # Advanced editor
code file.txt    # VS Code
```

---

## PowerShell vs Bash

| Task | PowerShell | Bash |
|------|-----------|------|
| List files | `ls` or `Get-ChildItem` | `ls` |
| Current directory | `pwd` or `Get-Location` | `pwd` |
| Change directory | `cd` or `Set-Location` | `cd` |
| Copy file | `Copy-Item` | `cp` |
| Move/rename | `Move-Item` | `mv` |
| Delete | `Remove-Item` | `rm` |
| Create directory | `mkdir` or `New-Item` | `mkdir` |
| View file | `Get-Content` or `cat` | `cat` or `less` |
| Search | `Select-String` | `grep` |
| Pipe operator | `|` | `|` |
| Command separator | `;` | `;` or `&&` |

**Note:** PowerShell supports many Bash aliases (like `ls`, `cat`, `pwd`) for convenience, but the underlying commands are different.

---

## Tips and Shortcuts

### Tab Completion

Press `Tab` to auto-complete file names, directory names, and commands. Press `Tab` multiple times to cycle through options.

```bash
cd Doc[Tab]  # Completes to "Documents"
git sta[Tab] # Completes to "git status"
```

### Command History

**Navigate history:**
- Up/Down arrows: Browse previous commands
- `Ctrl + R`: Search command history (Bash)
- `history`: View command history

**PowerShell:**
```powershell
Get-History
# Re-run command by ID
Invoke-History 5
```

### Clear Screen

**PowerShell/Bash:**
```bash
clear
# Or
cls  # PowerShell
```

### Cancel Command

Press `Ctrl + C` to cancel a running command.

### Copy and Paste

**PowerShell/CMD:**
- Copy: Highlight text, right-click or `Ctrl + Shift + C`
- Paste: Right-click or `Ctrl + Shift + V`

**Bash:**
- Copy: Highlight text, `Ctrl + Shift + C`
- Paste: `Ctrl + Shift + V`

---

## Common Patterns

### Chaining Commands

**PowerShell:**
```powershell
command1 ; command2 ; command3
```

**Bash:**
```bash
command1 && command2 && command3  # Run next only if previous succeeds
command1 ; command2 ; command3     # Run all regardless
```

### Redirecting Output

**Save output to file:**
```bash
command > output.txt      # Overwrite
command >> output.txt     # Append
```

**PowerShell:**
```powershell
command | Out-File output.txt
command | Out-File -Append output.txt
```

### Piping

Pass output of one command as input to another:

**PowerShell:**
```powershell
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
Get-Content file.txt | Select-String "pattern"
```

**Bash:**
```bash
ls -la | grep ".txt"
cat file.txt | grep "pattern"
```

### Variables

**PowerShell:**
```powershell
$myVar = "Hello"
Write-Host $myVar
```

**Bash:**
```bash
myVar="Hello"
echo $myVar
```

### Find Files

**PowerShell:**
```powershell
Get-ChildItem -Recurse -Filter "*.txt"
```

**Bash:**
```bash
find . -name "*.txt"
```

---

## Practice Exercises

Try these exercises to build confidence:

1. **Navigation:**
   - Open your terminal
   - Navigate to your Documents folder
   - List all files and directories
   - Go back to your home directory

2. **File Operations:**
   - Create a directory called `practice`
   - Navigate into it
   - Create a file called `test.txt`
   - Add some text to it
   - Copy the file to `test-copy.txt`
   - Delete the copy

3. **Git Workflow:**
   - Navigate to your project directory
   - Check git status
   - Create and switch to a new branch
   - Make a change to a file
   - Add, commit, and push your changes

---

## Further Resources

- **PowerShell Documentation:** [https://docs.microsoft.com/powershell/](https://docs.microsoft.com/powershell/)
- **Bash Guide:** [https://www.gnu.org/software/bash/manual/](https://www.gnu.org/software/bash/manual/)
- **Command Line Crash Course:** [https://www.learnenough.com/command-line-tutorial](https://www.learnenough.com/command-line-tutorial)
- **PowerShell Tutorial:** [https://www.tutorialspoint.com/powershell/](https://www.tutorialspoint.com/powershell/)

---

**Happy commanding!** 💻
