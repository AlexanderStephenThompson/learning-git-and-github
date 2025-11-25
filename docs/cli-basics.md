# Command Line Interface (CLI) Basics

This guide will help you become comfortable working in the terminal, covering essential commands and concepts for Windows PowerShell.

---

## Table of Contents

1. [What is the CLI?](#what-is-the-cli)
2. [Opening the Terminal](#opening-the-terminal)
3. [Basic Navigation](#basic-navigation)
4. [File and Directory Operations](#file-and-directory-operations)
5. [Viewing and Editing Files](#viewing-and-editing-files)
6. [Tips and Shortcuts](#tips-and-shortcuts)
7. [Common Patterns](#common-patterns)

---

## What is the CLI?

The Command Line Interface (CLI) is a text-based way to interact with your computer. Instead of clicking buttons and icons, you type commands to perform tasks. It's powerful, fast, and essential for working with Git and development tools.

**Why use the CLI?**
- Faster for repetitive tasks
- More control and precision
- Required for Git and many development tools
- Automatable with scripts

---

## Opening the Terminal

**Windows:**
- **PowerShell:** Press `Win + X`, then select "Windows PowerShell" or "Terminal"
- **Command Prompt:** Press `Win + R`, type `cmd`, press Enter
- **Git Bash:** Right-click in a folder → "Git Bash Here" (if Git is installed)

---

## Basic Navigation

### Current Directory

**PowerShell/CMD:**
```powershell
pwd
# Or
Get-Location
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

### Change Directory

**PowerShell:**
```powershell
cd Documents
cd ..           # Go up one level
cd ~            # Go to home directory
cd /            # Go to drive root
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
# Create nested directories
New-Item -ItemType Directory -Path parent\child\grandchild -Force
```

### Creating Files

**PowerShell:**
```powershell
New-Item -ItemType File -Name myfile.txt
# Or create with content
"Hello World" | Out-File myfile.txt
```

### Copying Files

**PowerShell:**
```powershell
Copy-Item source.txt destination.txt
# Copy directory recursively
Copy-Item -Recurse my-folder new-folder
```

### Moving/Renaming Files

**PowerShell:**
```powershell
Move-Item oldname.txt newname.txt
Move-Item file.txt C:\Users\YourName\Documents\
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

### Search File Contents

**PowerShell:**
```powershell
Select-String "search term" file.txt
# Search in multiple files
Select-String "search term" *.txt
```

### Edit Files

**PowerShell:**
```powershell
notepad file.txt
# Or open in VS Code
code file.txt
```

---

## Tips and Shortcuts

### Tab Completion

Press `Tab` to auto-complete file names, directory names, and commands. Press `Tab` multiple times to cycle through options.

```powershell
cd Doc[Tab]  # Completes to "Documents"
git sta[Tab] # Completes to "git status"
```

### Command History

**Navigate history:**
- Up/Down arrows: Browse previous commands
- `history`: View command history

**PowerShell:**
```powershell
Get-History
# Re-run command by ID
Invoke-History 5
```

### Clear Screen

**PowerShell:**
```powershell
clear
# Or
cls
```

### Cancel Command

Press `Ctrl + C` to cancel a running command.

### Copy and Paste

**PowerShell/CMD:**
- Copy: Highlight text, right-click or `Ctrl + Shift + C`
- Paste: Right-click or `Ctrl + Shift + V`

---

## Common Patterns

### Chaining Commands

**PowerShell:**
```powershell
command1 ; command2 ; command3
```

### Redirecting Output

**Save output to file:**
```powershell
command | Out-File output.txt
command | Out-File -Append output.txt
# Or use redirection
command > output.txt      # Overwrite
command >> output.txt     # Append
```

### Piping

Pass output of one command as input to another:

**PowerShell:**
```powershell
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
Get-Content file.txt | Select-String "pattern"
```

### Variables

**PowerShell:**
```powershell
$myVar = "Hello"
Write-Host $myVar
```

### Find Files

**PowerShell:**
```powershell
Get-ChildItem -Recurse -Filter "*.txt"
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
- **PowerShell Tutorial:** [https://www.tutorialspoint.com/powershell/](https://www.tutorialspoint.com/powershell/)

---

**Happy commanding!** 💻
