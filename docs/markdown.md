# Markdown on GitHub (GFM)

This is a comprehensive guide to **Markdown** and **GitHub Flavored Markdown (GFM)** — the formatting language used in README files, issues, pull requests, discussions, and documentation on GitHub.

Whether you're writing your first README or crafting detailed documentation, this guide covers everything from basic syntax to advanced GitHub-specific features.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Syntax](#basic-syntax)
3. [Headings](#headings)
4. [Emphasis & Text Styling](#emphasis--text-styling)
5. [Lists](#lists)
6. [Code](#code)
7. [Tables](#tables)
8. [Images & Media](#images--media)
9. [Links & References](#links--references)
10. [GitHub-Specific Features](#github-specific-features)
11. [Advanced Formatting](#advanced-formatting)
12. [Accessibility Best Practices](#accessibility-best-practices)
13. [Troubleshooting & Tips](#troubleshooting--tips)
14. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

---

## Introduction

### What is Markdown?

Markdown is a lightweight markup language that converts plain text into formatted HTML. It's easy to read and write, making it perfect for documentation.

### What is GitHub Flavored Markdown (GFM)?

GitHub Flavored Markdown extends standard Markdown with additional features like:
- Task lists (checkboxes)
- Tables
- Strikethrough text
- Autolinks
- Mentions and issue references
- Code blocks with syntax highlighting

### Why Use Markdown?

- **Simple & readable** — looks good in plain text and rendered HTML
- **Version-control friendly** — easy to track changes in Git
- **Portable** — works across all platforms
- **GitHub-native** — first-class support for all GFM features

---

## Basic Syntax

### Paragraphs

Paragraphs are separated by one or more blank lines. Line breaks within a paragraph are ignored unless you end a line with two spaces or a backslash.

**Example:**

```markdown
This is a paragraph.

This is another paragraph.

This is a single paragraph
with a line break.
```

**Rendered:**

This is a paragraph.

This is another paragraph.

This is a single paragraph
with a line break.

---

## Headings

Headings are created using `#` symbols. One `#` is the largest (H1), six `#` symbols is the smallest (H6).

**Example:**

```markdown
# Heading 1 (H1)
## Heading 2 (H2)
### Heading 3 (H3)
#### Heading 4 (H4)
##### Heading 5 (H5)
###### Heading 6 (H6)
```

**Best Practices:**

- Use headings hierarchically (start with H1 or H2, don't jump to H4)
- Only one H1 per document
- Use consistent heading levels for better accessibility
- Headings automatically create anchor links: `#heading-1` (spaces become hyphens)

**Tip:** Link to a heading with `[link text](#heading-name)` (convert spaces to hyphens and lowercase).

---

## Emphasis & Text Styling

### Italic, Bold, and Bold-Italic

```markdown
*italic* or _italic_
**bold** or __bold__
***bold italic*** or ___bold italic___
~~strikethrough~~
```

**Rendered:**

*italic* or _italic_  
**bold** or __bold__  
***bold italic*** or ___bold italic___  
~~strikethrough~~

### Combinations

You can combine emphasis styles:

```markdown
**bold with _italic_ inside**
_italic with **bold** inside_
```

**Rendered:**

**bold with _italic_ inside**  
_italic with **bold** inside_

---

## Lists

### Unordered Lists

Use `-`, `*`, or `+` for unordered lists. Mix and match for nested lists.

**Example:**

```markdown
- Item 1
- Item 2
  - Nested item 2a
  - Nested item 2b
- Item 3
```

**Rendered:**

- Item 1
- Item 2
  - Nested item 2a
  - Nested item 2b
- Item 3

### Ordered Lists

Use numbers followed by a period or parenthesis. Nesting uses 2-space indentation.

**Example:**

```markdown
1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item
```

**Rendered:**

1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item

### Task Lists (GitHub Feature)

Task lists allow interactive checkboxes in issues and PRs. Use `- [ ]` for unchecked and `- [x]` for checked items.

**Example:**

```markdown
## Project Checklist

- [x] Complete project setup
- [ ] Write documentation
- [ ] Run tests
- [ ] Deploy to production
```

**Rendered:**

- [x] Complete project setup
- [ ] Write documentation
- [ ] Run tests
- [ ] Deploy to production

**Note:** In issues and PRs, you can click to toggle checkboxes on GitHub!

---

## Code

### Inline Code

Wrap code snippets with single backticks for inline code (within text).

**Example:**

```markdown
Use the `git commit` command to save changes.
```

**Rendered:**

Use the `git commit` command to save changes.

### Code Blocks

Use triple backticks (` ``` `) for multi-line code blocks. Optionally specify a language for syntax highlighting.

**Example without syntax highlighting:**

```
function hello() {
  console.log('Hello, world!');
}
```

**Example with syntax highlighting (JavaScript):**

```javascript
function hello() {
  console.log('Hello, world!');
}
```

**Supported languages include:** `javascript`, `python`, `bash`, `json`, `yaml`, `markdown`, `html`, `css`, `sql`, and many more.

**Example with PowerShell:**

```powershell
$greeting = "Hello, world!"
Write-Host $greeting
```

**Example with Python:**

```python
def hello():
    print("Hello, world!")

hello()
```

### Indented Code Blocks

Indent code by 4 spaces (less common, fenced blocks are preferred).

```markdown
    function hello() {
      console.log('Hello');
    }
```

**Tip:** Always use fenced code blocks with language hints for better readability and syntax highlighting.

---

## Tables

Tables are a GitHub Flavored Markdown feature. Use pipes `|` to separate columns and hyphens `-` for headers.

**Example:**

```markdown
| Name      | Age | City       |
| ---       | --- | ---        |
| Alice     | 30  | New York   |
| Bob       | 25  | San Diego  |
| Charlie   | 35  | Austin     |
```

**Rendered:**

| Name      | Age | City       |
| ---       | --- | ---        |
| Alice     | 30  | New York   |
| Bob       | 25  | San Diego  |
| Charlie   | 35  | Austin     |

### Column Alignment

Use colons to align columns:
- `:---` — left-aligned (default)
- `:---:` — center-aligned
- `---:` — right-aligned

**Example:**

```markdown
| Left    | Center  | Right   |
| :---   | :---:  | ---:   |
| A      | B      | C      |
| 1      | 2      | 3      |
```

**Rendered:**

| Left    | Center  | Right   |
| :---   | :---:  | ---:   |
| A      | B      | C      |
| 1      | 2      | 3      |

### Table Tips

- You can include inline markdown (emphasis, links, code) in table cells
- Use `<br>` for line breaks within cells
- Tables cannot have row or column spans (GitHub limitation)
- Keep tables simple — very wide tables are hard to read

---

## Images & Media

### Inline Images

Use the syntax `![alt text](image-url)` to embed images. Always include descriptive `alt` text for accessibility.

**Example:**

```markdown
![GitHub logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

### Relative Image Paths

For images stored in your repository, use relative paths:

```markdown
![Project screenshot](./docs/images/screenshot.png)
![Diagram](../images/architecture.png)
```

### Images with Links

Wrap the image syntax with link syntax to make images clickable:

```markdown
[![Alt text](image-url)](https://example.com)
```

### GIF and Video Embeds

While GitHub doesn't support native `<video>` tags in Markdown, you can:
- Link to video files directly
- Use MP4 or WebM formats
- Embed YouTube links as regular links
- Use animated GIFs (same as static images)

**Example:**

```markdown
![Animation demo](./demo.gif)

Or link to a video:
[Watch the demo video](./demo.mp4)
```

---

## Links & References

### Inline Links

Use square brackets for link text and parentheses for the URL:

```markdown
[GitHub](https://github.com)
[Learn Markdown](https://commonmark.org)
```

**Rendered:**

[GitHub](https://github.com)  
[Learn Markdown](https://commonmark.org)

### Links with Titles (Hover Text)

Add a title in quotes after the URL:

```markdown
[GitHub](https://github.com "The GitHub website")
```

**Rendered:** (hover over the link to see the title)

### Reference-Style Links

Define links once and reuse them multiple times:

```markdown
[GitHub][github-ref]
[Google][google-ref]

[github-ref]: https://github.com
[google-ref]: https://google.com
```

### Auto-Links

URLs wrapped in angle brackets are automatically converted to links:

```markdown
<https://github.com>
<user@example.com>
```

**Rendered:**

<https://github.com>  
<user@example.com>

---

## GitHub-Specific Features

### Mentions

Mention users or teams with `@` followed by their username/team name. They'll receive a notification.

```markdown
@AlexanderStephenThompson, please review this.
Thanks to @github for the platform!
```

### Issue & Pull Request References

Reference issues and PRs within the same repository or across repositories:

```markdown
Fixes #42
Related to #10
Closes owner/repo#123
See also @username's comment in #456
```

**Rendered:** (GitHub automatically links these references)

GitHub recognizes keywords like `Fixes`, `Resolves`, `Closes` to auto-close issues when the PR is merged.

### Commit SHA References

Reference commits by their SHA (full or shortened):

```markdown
This was fixed in 8f5c7d2
See commit e0c2b7e8f for details
```

### Emoji

Use `:emoji-name:` to add emoji. GitHub supports hundreds of emoji codes:

```markdown
:tada: Celebration
:bug: Bug report
:rocket: Feature
:heart: Love
:+1: Thumbs up
:-1: Thumbs down
:eyes: Eyes
:memo: Documentation
```

**Rendered:**

🎉 Celebration  
🐛 Bug report  
🚀 Feature  
❤️ Love  
👍 Thumbs up  
👎 Thumbs down  
👀 Eyes  
📝 Documentation

### Mentions in Code

Mention users in code blocks (won't trigger notifications; prevents spam):

```markdown
```
# @username please note this change
```
```

---

## Advanced Formatting

### Blockquotes

Use `>` to create blockquotes. Nest blockquotes with multiple `>` symbols.

**Example:**

```markdown
> This is a blockquote.
>
> It can span multiple paragraphs.
>
> > And be nested too.
```

**Rendered:**

> This is a blockquote.
>
> It can span multiple paragraphs.
>
> > And be nested too.

### Callout Boxes (Common Pattern)

While GitHub doesn't have native callouts, use blockquotes with bold headers:

```markdown
> **Note:** This is important information.

> **Warning:** Be careful with this step.

> **Tip:** Here's a helpful hint.
```

**Rendered:**

> **Note:** This is important information.

> **Warning:** Be careful with this step.

> **Tip:** Here's a helpful hint.

### Horizontal Rules

Use three or more hyphens, asterisks, or underscores on a line by themselves:

```markdown
---
***
___
```

**Rendered:** (displays as a horizontal line)

---

### HTML Passthrough

GitHub Markdown supports inline HTML. This is useful for features Markdown doesn't support natively:

```markdown
<div align="center">
  <strong>Centered text</strong>
</div>

<details>
  <summary>Click to expand</summary>
  
  Hidden content goes here.
  
</details>
```

### Escaping Special Characters

Use backslash `\` to escape Markdown special characters:

```markdown
\# This is not a heading
\*This is not italic\*
\[Not a link\]
```

**Rendered:** (shows the literal characters)

### Line Breaks

- Two spaces at end of line: `line 1  ` (then newline)
- `<br>` HTML tag: `line 1<br>`
- Backslash: `line 1\` (then newline)

---

## Accessibility Best Practices

### Alt Text for Images

Always include descriptive alt text (the first parameter in `![alt text](url)`):

```markdown
✅ Good:
![A screenshot showing the GitHub profile page with dark mode enabled](./profile-screenshot.png)

❌ Bad:
![screenshot](./profile-screenshot.png)
```

### Heading Hierarchy

Use headings in logical order (H1 → H2 → H3, not H1 → H3):

```markdown
✅ Good:
# Main Title
## Section 1
### Subsection 1.1

❌ Bad:
# Main Title
### Subsection (skips H2)
```

### Color Alone Not Sufficient

Don't rely on color to convey meaning. Use text, icons, or other visual cues:

```markdown
✅ Good:
**Status:** ✅ Complete (or ⏳ In Progress)

❌ Bad:
Status: <span style="color:green">Complete</span>
```

### Link Text Should Be Descriptive

Avoid vague link text like "click here":

```markdown
✅ Good:
[Learn more about GitHub Pages](https://pages.github.com)

❌ Bad:
[Click here](https://pages.github.com) to learn more
```

### Language & Clarity

- Use simple, clear language
- Break content into short paragraphs
- Use lists to organize information
- Define acronyms on first use: "GitHub Flavored Markdown (GFM)"

---

## Troubleshooting & Tips

### Common Issues

**Problem:** Links aren't rendering correctly.
- **Solution:** Ensure URL starts with `http://` or `https://`. Relative paths must start with `./` or `../`.

**Problem:** Images not showing.
- **Solution:** Check file path is correct. For public images, use full HTTPS URLs. For repo images, use relative paths.

**Problem:** Code block syntax highlighting not working.
- **Solution:** Specify the language name correctly (e.g., `javascript` not `js`, though both often work).

**Problem:** Table formatting looks broken.
- **Solution:** Ensure each row has the same number of columns separated by `|`. Use `<br>` for multi-line cells.

**Problem:** Special characters or emojis not displaying.
- **Solution:** Use valid UTF-8 encoding. For emoji, use the `:emoji-name:` syntax or paste the emoji directly.

### Pro Tips

1. **Preview before committing** — GitHub shows a preview pane; use it to check your formatting.
2. **Use fenced code blocks** — Always prefer triple backticks over indenting with spaces.
3. **Keep it simple** — Markdown is meant to be readable in plain text. Avoid excessive HTML.
4. **Consistent style** — Pick a convention (emphasis style, list markers) and stick with it.
5. **Check links in PRs** — GitHub Actions can lint and check links automatically.
6. **Use relative paths** — Makes docs portable if you rename folders or repos.

---

## Quick Reference Cheatsheet

| Element | Syntax | Example |
| --- | --- | --- |
| Heading | `# Heading` | # Heading |
| Bold | `**bold**` | **bold** |
| Italic | `*italic*` | *italic* |
| Strikethrough | `~~text~~` | ~~text~~ |
| Inline code | `` `code` `` | `code` |
| Code block | ` ```language ` | (see examples above) |
| Link | `[text](url)` | [GitHub](https://github.com) |
| Image | `![alt](url)` | (see examples above) |
| Unordered list | `- item` | (see examples above) |
| Ordered list | `1. item` | (see examples above) |
| Task list | `- [ ] task` | (see examples above) |
| Table | `\| column \|` | (see examples above) |
| Blockquote | `> quote` | (see examples above) |
| Mention | `@username` | @username |
| Issue ref | `#123` | #123 |
| Horizontal rule | `---` | (see examples above) |
| Emoji | `:tada:` | 🎉 |

---

## Badges & Shields

### What Are Badges?

Badges (shields) are small, clickable images placed in your README that display project status at a glance. They typically show build status, version, license, language support, test coverage, and more.

### Using Shields.io

The most popular badge service is [Shields.io](https://shields.io). Syntax:

```markdown
https://img.shields.io/badge/LABEL-MESSAGE-COLOR
```

**Examples:**

```markdown
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)
![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
```

### Making Badges Clickable

Wrap badges in link syntax:

```markdown
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/user/repo/actions)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
```

**Rendered:**

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()  
[![License](https://img.shields.io/badge/License-MIT-blue.svg)]()

### Recommended Badges for This Repo

```markdown
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Docs](https://img.shields.io/badge/Docs-Complete-brightgreen.svg)](./docs/markdown.md)
[![GitHub Pages](https://img.shields.io/badge/Pages-Live-brightgreen.svg)](https://AlexanderStephenThompson.github.io/learning-git-and-github)
```

### Common Badge Types

- **License** — `https://img.shields.io/badge/License-MIT-blue.svg`
- **Version** — `https://img.shields.io/badge/version-1.0.0-blue.svg`
- **Status** — `https://img.shields.io/badge/Status-Active-brightgreen.svg`
- **Language** — `https://img.shields.io/badge/language-Python-blue.svg`
- **Platform** — `https://img.shields.io/badge/platform-Windows-blue.svg`

### Badge Colors

Common colors: `blue`, `green`, `brightgreen`, `red`, `orange`, `yellow`, `purple`, `ff69b4` (pink)

---

## GitHub Labels & Repository Organization

### What Are Labels?

Labels are tags for issues and pull requests. GitHub provides default labels (`bug`, `documentation`, `enhancement`, `good first issue`, etc.), but you can create custom ones.

### Creating Custom Labels

Via GitHub UI:

1. Go to repo → **Issues** → **Labels** (right sidebar)
2. Click **New label**
3. Enter name (e.g., `type: bug`, `priority: high`, `scope: docs`)
4. Choose color and add description
5. Click **Create label**

### Recommended Custom Labels

**By type:**
- `type: bug` — bug or defect
- `type: feature` — feature request
- `type: docs` — documentation
- `type: question` — question

**By priority:**
- `priority: critical` — must fix immediately
- `priority: high` — important
- `priority: low` — nice to have

**By status:**
- `status: in-progress` — actively being worked on
- `status: blocked` — waiting on something
- `status: review-needed` — needs review

**By scope:**
- `scope: frontend` — frontend code
- `scope: backend` — backend code
- `scope: docs` — documentation

### Using Labels

When creating/editing an issue or PR:
1. Click **Labels** (usually right panel)
2. Select one or more labels
3. Labels appear on the issue card for filtering

---

## Repository Metadata & Topics

### Adding a Repository Description

1. Go to **Settings** → **General**
2. Under "Repository name", add **Description** (shown on repo list and GitHub search)
3. Optionally add **Website** link
4. Click **Save**

### Adding Topics

Topics help users discover your repo. Add up to 30 topics:

1. Go to **Settings** → **General**
2. Under "Topics", enter keywords (e.g., `github markdown documentation tutorial learning`)
3. Press Enter to add each topic

**Good topics for a GitHub guide repo:**
- `github`
- `markdown`
- `documentation`
- `tutorial`
- `learning-resource`
- `gfm` (GitHub Flavored Markdown)
- `git`

Topics appear below your repo name and are searchable on GitHub.

### Repository Visibility

- **Public** — visible to everyone, searchable
- **Private** — only visible to you and collaborators
- **Internal** — visible to your organization (GitHub Enterprise)

Change in **Settings** → **General** → **Change repository visibility**.

---

## Repository Templates

### Creating a Template Repository

If you want others to use your repo structure as a starting point:

1. Go to **Settings** → **General**
2. Check **Template repository**
3. Click **Save**

Users can then click **Use this template** when viewing your repo to create a new repository with your structure.

### Using a Repository Template

1. Navigate to a template repository
2. Click **Use this template** → **Create a new repository**
3. Choose name, visibility, and click **Create**

The new repo will have all your files but clean Git history.

---

## Further Resources

- **CommonMark Spec** — [https://spec.commonmark.org/](https://spec.commonmark.org/)
- **GitHub Flavored Markdown** — [https://github.github.com/gfm/](https://github.github.com/gfm/)
- **GitHub Docs on Markdown** — [https://docs.github.com/en/get-started/writing-on-github](https://docs.github.com/en/get-started/writing-on-github)
- **Markdown Guide** — [https://www.markdownguide.org/](https://www.markdownguide.org/)
- **Emoji Cheatsheet** — [https://www.webfx.com/tools/emoji-cheat-sheet/](https://www.webfx.com/tools/emoji-cheat-sheet/)
- **Shields.io** — [https://shields.io](https://shields.io) (badge generator)
- **GitHub Labels Guide** — [https://docs.github.com/en/issues/using-labels-and-milestones](https://docs.github.com/en/issues/using-labels-and-milestones)

---

**Happy writing!** 📝
