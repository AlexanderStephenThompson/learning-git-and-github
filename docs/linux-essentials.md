# Linux Essentials

This guide covers essential Linux commands and concepts that every developer and power user should know. It provides a foundation for working with Linux systems, whether on a local machine, server, or in the cloud.

---

## Table of Contents

1. [What is Linux?](#what-is-linux)
2. [The Linux File System](#the-linux-file-system)
3. [Basic Navigation](#basic-navigation)
4. [File and Directory Operations](#file-and-directory-operations)
5. [Viewing and Editing Files](#viewing-and-editing-files)
6. [File Permissions](#file-permissions)
7. [User Management](#user-management)
8. [Package Management](#package-management)
9. [Process Management](#process-management)
10. [Text Processing](#text-processing)
11. [Environment Variables](#environment-variables)
12. [Shell Scripting Basics](#shell-scripting-basics)
13. [Useful Tips and Shortcuts](#useful-tips-and-shortcuts)

---

## What is Linux?

Linux is a free, open-source operating system kernel. It powers everything from smartphones (Android) to servers, supercomputers, and embedded devices.

**Why learn Linux?**

- Most servers run Linux
- Essential for cloud computing, DevOps, and development
- Powerful command-line tools
- Free and open source
- Highly customizable

### Linux Distributions

| Distribution | Description | Use Case |
|--------------|-------------|----------|
| **Ubuntu** | User-friendly, popular | Desktop, servers, beginners |
| **Debian** | Stable, reliable | Servers, advanced users |
| **Fedora** | Cutting-edge features | Developers, workstations |
| **CentOS/Rocky** | Enterprise-focused | Production servers |
| **Arch Linux** | Minimalist, DIY | Advanced users |
| **Alpine** | Lightweight | Containers, embedded |

---

## The Linux File System

Everything in Linux is a file, organized in a hierarchical directory structure starting from the root (`/`).

### Directory Structure

| Directory | Purpose |
|-----------|---------|
| `/` | Root directory |
| `/home` | User home directories |
| `/root` | Root user's home directory |
| `/etc` | Configuration files |
| `/var` | Variable data (logs, databases) |
| `/tmp` | Temporary files |
| `/usr` | User programs and utilities |
| `/bin` | Essential user binaries |
| `/sbin` | System binaries |
| `/opt` | Optional/third-party software |
| `/dev` | Device files |
| `/proc` | Process information |
| `/mnt` | Mount points |

### Path Types

| Type | Example | Description |
|------|---------|-------------|
| **Absolute** | `/home/user/documents` | Full path from root |
| **Relative** | `./documents` or `documents` | Path from current directory |

### Special Directory Symbols

| Symbol | Meaning |
|--------|---------|
| `.` | Current directory |
| `..` | Parent directory |
| `~` | Home directory |
| `-` | Previous directory |

---

## Basic Navigation

### Print Working Directory

```bash
pwd
```

Shows your current location in the file system.

### List Files and Directories

```bash
# Basic listing
ls

# Long format with details
ls -l

# Show hidden files (starting with .)
ls -a

# Long format with hidden files
ls -la

# Human-readable file sizes
ls -lh

# Sort by modification time
ls -lt

# Recursive listing
ls -R
```

### Change Directory

```bash
# Go to a specific directory
cd /path/to/directory

# Go to home directory
cd
cd ~

# Go up one level
cd ..

# Go up two levels
cd ../..

# Go to previous directory
cd -

# Go to another user's home
cd ~username
```

---

## File and Directory Operations

### Creating Directories

```bash
# Create a single directory
mkdir my-folder

# Create nested directories
mkdir -p parent/child/grandchild

# Create multiple directories
mkdir dir1 dir2 dir3
```

### Creating Files

```bash
# Create empty file or update timestamp
touch myfile.txt

# Create multiple files
touch file1.txt file2.txt

# Create file with content
echo "Hello World" > myfile.txt

# Create file using cat (press Ctrl+D to save)
cat > myfile.txt
```

### Copying Files and Directories

```bash
# Copy file
cp source.txt destination.txt

# Copy to directory
cp file.txt /path/to/directory/

# Copy directory recursively
cp -r source-dir destination-dir

# Copy with verbose output
cp -v source.txt destination.txt

# Preserve attributes
cp -p source.txt destination.txt
```

### Moving and Renaming

```bash
# Move file to directory
mv file.txt /path/to/directory/

# Rename file
mv oldname.txt newname.txt

# Move and rename
mv file.txt /path/to/directory/newname.txt

# Move multiple files to directory
mv file1.txt file2.txt /path/to/directory/
```

### Deleting Files and Directories

```bash
# Remove file
rm file.txt

# Remove multiple files
rm file1.txt file2.txt

# Remove with confirmation
rm -i file.txt

# Remove directory recursively
rm -r directory/

# Force remove (no confirmation)
rm -rf directory/
# ⚠️ WARNING: rm -rf is extremely dangerous! It permanently deletes
# files without confirmation and cannot be undone. Always double-check
# the path before running. Consider using trash-cli for safer deletion.

# Remove empty directory
rmdir empty-directory/
```

### Finding Files

```bash
# Find by name
find /path -name "filename.txt"

# Find by name (case insensitive)
find /path -iname "filename.txt"

# Find by type (f=file, d=directory)
find /path -type f -name "*.txt"

# Find by modification time (days)
find /path -mtime -7  # Modified in last 7 days

# Find and execute command
find /path -name "*.log" -exec rm {} \;

# Using locate (faster, uses database)
locate filename.txt
sudo updatedb  # Update the database
```

---

## Viewing and Editing Files

### Viewing File Contents

```bash
# Display entire file
cat file.txt

# Display with line numbers
cat -n file.txt

# View large files page by page
less file.txt
# Navigation: Space=next page, b=previous, q=quit, /=search

# View first lines
head file.txt
head -n 20 file.txt  # First 20 lines

# View last lines
tail file.txt
tail -n 20 file.txt  # Last 20 lines

# Follow file in real-time (great for logs)
tail -f /var/log/syslog
```

### Text Editors

**Nano (beginner-friendly):**

```bash
nano file.txt
```

| Shortcut | Action |
|----------|--------|
| `Ctrl+O` | Save file |
| `Ctrl+X` | Exit |
| `Ctrl+K` | Cut line |
| `Ctrl+U` | Paste |
| `Ctrl+W` | Search |

**Vim (powerful, learning curve):**

```bash
vim file.txt
```

| Mode | Key | Purpose |
|------|-----|---------|
| Normal | `Esc` | Navigation, commands |
| Insert | `i` | Typing text |
| Command | `:` | Execute commands |

| Command | Action |
|---------|--------|
| `:w` | Save |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |
| `dd` | Delete line |
| `yy` | Copy line |
| `p` | Paste |
| `/text` | Search |

---

## File Permissions

Linux uses a permission system to control access to files and directories.

### Understanding Permissions

```bash
ls -l
# Output: -rwxr-xr-- 1 user group 1024 Jan 1 12:00 file.txt
```

| Position | Meaning |
|----------|---------|
| `-` | File type (`-`=file, `d`=directory, `l`=link) |
| `rwx` | Owner permissions |
| `r-x` | Group permissions |
| `r--` | Others permissions |

| Symbol | Permission | Numeric |
|--------|------------|---------|
| `r` | Read | 4 |
| `w` | Write | 2 |
| `x` | Execute | 1 |
| `-` | No permission | 0 |

### Changing Permissions

**Symbolic method:**

```bash
# Add execute for owner
chmod u+x file.txt

# Remove write for group
chmod g-w file.txt

# Add read for others
chmod o+r file.txt

# Add execute for all
chmod a+x file.txt

# Multiple changes
chmod u+x,g-w,o-r file.txt
```

**Numeric method:**

```bash
# rwxr-xr-x = 755
chmod 755 file.txt

# rw-r--r-- = 644
chmod 644 file.txt

# rwx------ = 700
chmod 700 script.sh

# Apply recursively
chmod -R 755 directory/
```

### Common Permission Patterns

| Numeric | Symbolic | Use Case |
|---------|----------|----------|
| `644` | `rw-r--r--` | Regular files |
| `755` | `rwxr-xr-x` | Executable files, directories |
| `600` | `rw-------` | Private files (SSH keys) |
| `700` | `rwx------` | Private directories |

### Changing Ownership

```bash
# Change owner
chown user file.txt

# Change owner and group
chown user:group file.txt

# Change group only
chgrp group file.txt

# Recursive change
chown -R user:group directory/
```

---

## User Management

### User Information

```bash
# Current user
whoami

# User ID and groups
id

# Currently logged in users
who

# User details
finger username

# Switch user
su - username

# Run command as root
sudo command
```

### Managing Users

```bash
# Add new user
sudo adduser username
sudo useradd username  # More basic

# Delete user
sudo deluser username
sudo userdel username

# Change password
passwd          # Current user
sudo passwd username  # Other user

# Modify user
sudo usermod -aG groupname username  # Add to group
```

### Managing Groups

```bash
# Create group
sudo groupadd groupname

# Delete group
sudo groupdel groupname

# List groups for user
groups username

# View group file
cat /etc/group
```

---

## Package Management

### Debian/Ubuntu (apt)

```bash
# Update package list
sudo apt update

# Upgrade installed packages
sudo apt upgrade

# Install package
sudo apt install package-name

# Remove package
sudo apt remove package-name

# Remove with config files
sudo apt purge package-name

# Search for package
apt search keyword

# Show package info
apt show package-name

# Clean up unused packages
sudo apt autoremove
```

### Red Hat/CentOS/Fedora (dnf/yum)

```bash
# Update package list and upgrade
sudo dnf update

# Install package
sudo dnf install package-name

# Remove package
sudo dnf remove package-name

# Search for package
dnf search keyword

# Show package info
dnf info package-name

# List installed packages
dnf list installed
```

### Common Software Installation

```bash
# Git
sudo apt install git

# Node.js (via NodeSource)
# Note: Always review scripts before piping to bash. Download first with:
# curl -fsSL https://deb.nodesource.com/setup_lts.x -o setup_node.sh
# Then inspect and run: sudo -E bash setup_node.sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs

# Python
sudo apt install python3 python3-pip

# Docker
sudo apt install docker.io
```

---

## Process Management

### Viewing Processes

```bash
# List all processes
ps aux

# Process tree
pstree

# Interactive process viewer
top
htop  # More user-friendly (may need install)

# Find specific process
ps aux | grep process-name
pgrep process-name
```

### Managing Processes

```bash
# Run in background
command &

# Bring to foreground
fg

# Send to background
bg

# List background jobs
jobs

# Kill by PID
kill PID
kill -9 PID  # Force kill

# Kill by name
killall process-name
pkill process-name

# Kill with signal
kill -SIGTERM PID  # Graceful termination
kill -SIGKILL PID  # Force kill (same as -9)
```

### System Services (systemd)

```bash
# Check service status
sudo systemctl status service-name

# Start service
sudo systemctl start service-name

# Stop service
sudo systemctl stop service-name

# Restart service
sudo systemctl restart service-name

# Enable service on boot
sudo systemctl enable service-name

# Disable service on boot
sudo systemctl disable service-name

# List all services
systemctl list-units --type=service
```

---

## Text Processing

### grep - Search Text

```bash
# Search in file
grep "pattern" file.txt

# Case insensitive
grep -i "pattern" file.txt

# Show line numbers
grep -n "pattern" file.txt

# Recursive search
grep -r "pattern" directory/

# Invert match (show non-matching lines)
grep -v "pattern" file.txt

# Count matches
grep -c "pattern" file.txt

# Extended regex
grep -E "pattern1|pattern2" file.txt
```

### sed - Stream Editor

```bash
# Replace first occurrence per line
sed 's/old/new/' file.txt

# Replace all occurrences
sed 's/old/new/g' file.txt

# Replace in place
sed -i 's/old/new/g' file.txt

# Delete lines containing pattern
sed '/pattern/d' file.txt

# Print specific lines
sed -n '5,10p' file.txt  # Lines 5-10
```

### awk - Pattern Processing

```bash
# Print specific column
awk '{print $1}' file.txt

# Print multiple columns
awk '{print $1, $3}' file.txt

# With delimiter
awk -F':' '{print $1}' /etc/passwd

# Sum column values
awk '{sum += $1} END {print sum}' file.txt

# Filter by condition
awk '$3 > 100 {print $0}' file.txt
```

### Other Useful Tools

```bash
# Sort lines
sort file.txt
sort -r file.txt  # Reverse
sort -n file.txt  # Numeric

# Remove duplicates
uniq file.txt
sort file.txt | uniq  # Sort first for uniq to work properly

# Count lines, words, characters
wc file.txt
wc -l file.txt  # Lines only

# Cut columns
cut -d':' -f1 /etc/passwd

# Compare files
diff file1.txt file2.txt
```

---

## Environment Variables

### Viewing Variables

```bash
# Show all environment variables
env
printenv

# Show specific variable
echo $PATH
echo $HOME
echo $USER

# Show shell variables
set
```

### Setting Variables

```bash
# Set for current session
export MY_VAR="value"

# Set without export (shell only)
MY_VAR="value"

# Append to PATH
export PATH=$PATH:/new/path

# Unset variable
unset MY_VAR
```

### Common Environment Variables

| Variable | Description |
|----------|-------------|
| `PATH` | Directories to search for commands |
| `HOME` | User's home directory |
| `USER` | Current username |
| `SHELL` | Current shell |
| `PWD` | Current working directory |
| `EDITOR` | Default text editor |
| `LANG` | System language/locale |

### Persistent Variables

```bash
# Add to ~/.bashrc for bash
echo 'export MY_VAR="value"' >> ~/.bashrc
source ~/.bashrc  # Reload

# Add to ~/.profile for all shells
echo 'export MY_VAR="value"' >> ~/.profile
```

---

## Shell Scripting Basics

### Creating a Script

```bash
#!/bin/bash
# This is a comment
echo "Hello, World!"
```

Make it executable:

```bash
chmod +x script.sh
./script.sh
```

### Variables

```bash
#!/bin/bash
NAME="John"
echo "Hello, $NAME"
echo "Hello, ${NAME}!"
```

### User Input

```bash
#!/bin/bash
echo "What is your name?"
read NAME
echo "Hello, $NAME"
```

### Conditionals

```bash
#!/bin/bash
if [ "$1" == "hello" ]; then
    echo "Hello to you too!"
elif [ "$1" == "bye" ]; then
    echo "Goodbye!"
else
    echo "I don't understand"
fi
```

### Loops

```bash
#!/bin/bash
# For loop
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# For loop with range
for i in {1..5}; do
    echo "Number: $i"
done

# While loop
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

### Functions

```bash
#!/bin/bash
greet() {
    echo "Hello, $1!"
}

greet "World"
greet "User"
```

---

## Useful Tips and Shortcuts

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Cancel current command |
| `Ctrl+Z` | Suspend current process |
| `Ctrl+D` | Exit shell / End of input |
| `Ctrl+L` | Clear screen |
| `Ctrl+A` | Move to beginning of line |
| `Ctrl+E` | Move to end of line |
| `Ctrl+U` | Clear line before cursor |
| `Ctrl+K` | Clear line after cursor |
| `Ctrl+R` | Search command history |
| `Tab` | Auto-complete |

### Command History

```bash
# Show history
history

# Run last command
!!

# Run command by number
!123

# Run last command starting with...
!ssh

# Search history interactively
Ctrl+R, then type search term
```

### Useful Aliases

Add to `~/.bashrc`:

```bash
# Navigation
alias ..='cd ..'
alias ...='cd ../..'
alias ll='ls -la'
alias la='ls -A'

# Safety
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

# Git shortcuts
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline'
```

### Chaining Commands

```bash
# Run sequentially
command1 ; command2

# Run if previous succeeds
command1 && command2

# Run if previous fails
command1 || command2

# Pipe output to next command
command1 | command2
```

### Redirection

```bash
# Output to file (overwrite)
command > file.txt

# Output to file (append)
command >> file.txt

# Input from file
command < file.txt

# Redirect errors
command 2> errors.txt

# Redirect output and errors
command > file.txt 2>&1
command &> file.txt
```

---

## Quick Reference

### Essential Commands Cheatsheet

```bash
# Navigation
pwd                    # Print working directory
cd /path               # Change directory
ls -la                 # List files with details

# File operations
cp source dest         # Copy
mv source dest         # Move/rename
rm file                # Remove
mkdir dir              # Create directory
touch file             # Create empty file

# Viewing files
cat file               # Show contents
less file              # Page through file
head -n 10 file        # First 10 lines
tail -n 10 file        # Last 10 lines
tail -f file           # Follow file

# Searching
grep "pattern" file    # Search in file
find /path -name "*.txt"  # Find files

# Permissions
chmod 755 file         # Change permissions
chown user:group file  # Change owner

# Processes
ps aux                 # List processes
top                    # Interactive process view
kill PID               # Kill process

# System
sudo command           # Run as root
apt install pkg        # Install package (Debian/Ubuntu)
systemctl status svc   # Service status
```

---

## Further Resources

- **Linux Command Line Book:** [linuxcommand.org](https://linuxcommand.org/)
- **Linux Journey:** [linuxjourney.com](https://linuxjourney.com/)
- **Explain Shell:** [explainshell.com](https://explainshell.com/)
- **Ubuntu Documentation:** [help.ubuntu.com](https://help.ubuntu.com/)
- **Arch Wiki:** [wiki.archlinux.org](https://wiki.archlinux.org/) (excellent for all distros)
- **TLDR Pages:** [tldr.sh](https://tldr.sh/) (simplified man pages)

---

**Happy Linux-ing!** 🐧
