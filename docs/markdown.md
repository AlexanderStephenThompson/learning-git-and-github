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
6. [Blockquotes](#blockquotes)
7. [Code](#code)
8. [Tables](#tables)
9. [Images & Media](#images--media)
10. [Links & References](#links--references)
11. [GitHub-Specific Features](#github-specific-features)
12. [Advanced Formatting](#advanced-formatting)
    - [HTML & Details Elements](#html-passthrough)
    - [Footnotes](#footnotes)
    - [Alerts](#alerts-github-feature)
    - [Color Models](#supported-color-models)
    - [Section Links & Anchors](#section-links--anchors)
    - [Relative Links](#relative-links)
    - [Line Breaks](#line-breaks)
13. [Mentions & References](#mentions--references)
14. [Emojis & Special Formatting](#emojis--special-formatting)
15. [Escaping Special Characters](#escaping-special-characters)
16. [Accessibility Best Practices](#accessibility-best-practices)
17. [Troubleshooting & Tips](#troubleshooting--tips)
18. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

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

### Strikethrough

Use `~~text~~` to create strikethrough text (GitHub feature).

**Example:**

```markdown
~~This text is strikethrough~~
This text is ~~deleted~~ updated.
```

**Rendered:**

~~This text is strikethrough~~
This text is ~~deleted~~ updated.

### Subscript & Superscript

Use HTML tags `<sub>` and `<sup>` for subscript and superscript text.

**Example:**

```markdown
H<sub>2</sub>O is water.

E=mc<sup>2</sup> is Einstein's famous equation.

x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>
```

**Rendered:**

H<sub>2</sub>O is water.

E=mc<sup>2</sup> is Einstein's famous equation.

x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>

### Underline

Use HTML `<ins>` tag to underline text. Note: Standard Markdown doesn't have native underline syntax.

**Example:**

```markdown
This is <ins>underlined text</ins>.

This is <u>also underlined</u>.
```

**Rendered:**

This is <ins>underlined text</ins>.

This is <u>also underlined</u>.

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

## Blockquotes

Create blockquotes using `>` at the start of a line. Blockquotes are commonly used for highlighting important information or quoting other sources.

**Example:**

```markdown
> This is a blockquote.
> It can span multiple lines.
>
> And include multiple paragraphs.
```

**Rendered:**

> This is a blockquote.
> It can span multiple lines.
>
> And include multiple paragraphs.

### Nested Blockquotes

Use `>>` to create nested blockquotes within a blockquote.

**Example:**

```markdown
> This is a blockquote.
>
>> This is a nested blockquote inside the first one.
>
> Back to the first level of blockquote.
```

**Rendered:**

> This is a blockquote.
>
>> This is a nested blockquote inside the first one.
>
> Back to the first level of blockquote.

### Blockquotes with Other Elements

Blockquotes can contain other Markdown elements like lists, code blocks, headings, and emphasis.

**Example:**

```markdown
> #### Important Notice
>
> - **Bold statement** here
> - _Italicized point_ here
>
> This is a code example:
> ```
> const result = true;
> console.log(result);
> ```
>
> *This blockquote contains multiple types of formatting.*
```

**Best Practices:**

- Add blank lines before and after blockquotes for compatibility
- Use blockquotes for citations, important information, or highlighted content
- Avoid overusing blockquotes to prevent visual clutter

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

### Footnotes

GitHub supports footnotes for references and citations. Create a footnote reference with `[^1]` and define it anywhere in your document.

**Example:**

```markdown
This statement needs a citation[^1].

Here's more information[^2].

[^1]: This is the first footnote.
[^2]: This is the second footnote with multiple lines.
    You can indent continuation lines with 4 spaces.
```

**Rendered:** (footnotes appear at the bottom with links)

**Key Points:**
- Footnote definitions can appear anywhere in the document
- They automatically collect at the bottom
- Position of definition doesn't matter
- Footnotes work in issues, PRs, and `.md` files

### Alerts (GitHub Feature)

GitHub supports alerts (also called callouts or admonitions) for highlighting critical information. Five alert types are available:

**Example:**

```markdown
> [!NOTE]
> Useful information that users should know, even when skimming.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent information that needs immediate user attention.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```

**Best Practices:**
- Use alerts only when critical for user success
- Limit to 1-2 per article to avoid overload
- Avoid placing alerts consecutively
- Alerts cannot be nested within other elements

### Supported Color Models

In issues, pull requests, and discussions, you can display color previews by wrapping color codes in backticks. Supported formats include HEX, RGB, and HSL.

**Example:**

```markdown
The primary color is `#0969DA`.

Use `rgb(9, 105, 218)` for the accent.

Try `hsl(212, 92%, 45%)` for darker shade.
```

**Rendered:** (displays small colored circles next to codes)

**Supported formats:**
- HEX: `` `#RRGGBB` `` (e.g., `` `#FF5733` ``)
- RGB: `` `rgb(R,G,B)` `` (e.g., `` `rgb(255, 87, 51)` ``)
- HSL: `` `hsl(H,S,L)` `` (e.g., `` `hsl(9, 100%, 60%)` ``)

**Note:** Color visualization only appears in issues, PRs, and discussions—not in `.md` files.

### Section Links & Anchors

#### Automatic Heading Anchors

GitHub automatically creates anchor links from headings. Hover over a heading to see the link icon.

**Anchor rules:**
- Letters → lowercase
- Spaces → hyphens
- Punctuation → removed
- Markup → stripped (e.g., `_italic_` becomes `italic`)

**Examples:**
- `# My Section` → `#my-section`
- `## Advanced Topics` → `#advanced-topics`
- `### Best Practices & Tips` → `#best-practices--tips`

#### Linking to Headings

```markdown
[Jump to headings section](#headings)
[Link to table of contents](#table-of-contents)
[Back to top](#markdown-on-github-gfm)
```

#### Custom Anchors

Create custom anchor points using HTML:

```markdown
<a name="my-custom-anchor"></a>

This text has a custom anchor that you can link to directly.

[Jump to custom anchor](#my-custom-anchor)
```

**Note:** Custom anchors won't appear in GitHub's automatic Table of Contents.

### Relative Links

Link to other files in your repository using relative paths. This is better than absolute URLs for cloning and collaboration.

**Examples:**

```markdown
[Link to CONTRIBUTING](./CONTRIBUTING.md)
[Link to docs folder](./docs/getting-started.md)
[Link to parent folder file](../README.md)
[Link to file on different branch](../main/README.md)
[Link from nested folder to root](../../README.md)
```

**Best Practices:**
- Use `./` for files in the same directory
- Use `../` to go up one directory level
- Use `/` at the start to reference from repository root
- Relative links work in cloned repositories (absolute URLs don't)
- Makes documentation portable if you move files

### Line Breaks

There are multiple ways to create line breaks in Markdown:

**Method 1: Two Trailing Spaces**

```markdown
This is line one.  
This is line two.
```

**Method 2: Backslash**

```markdown
This is line one.\
This is line two.
```

**Method 3: HTML Break Tag**

```markdown
This is line one.<br/>
This is line two.
```

**Method 4: Blank Line (for paragraph breaks)**

```markdown
This is paragraph one.

This is paragraph two.
```

**Best Practices:**
- For compatibility, use trailing whitespace or `<br/>` HTML tags
- Blank lines are better for separating paragraphs
- Two trailing spaces or backslash creates soft line breaks
- HTML break tag is most explicit and widely supported

---

## Mentions & References

### Mentioning Users

Mention a user with `@` followed by their username. They'll receive a notification if they have repository access.

```markdown
@AlexanderStephenThompson What do you think about this approach?

Reviewers: @myorg/team-name
```

**Note:** Users must have read access to the repository to be notified.

### Mentioning Teams

Teams within organizations can be mentioned the same way:

```markdown
@myorg/backend-team
@myorg/frontend-team
```

### Referencing Issues & Pull Requests

Reference issues or PRs to link them and trigger automation:

```markdown
#123 — references issue 123
#456 — references pull request 456
Fixes #789 — closes issue 789 when merged
Closes #123 — closes issue 123 when merged
Resolves #456 — resolves PR 456 when merged
```

**Automation Keywords:**
- `close`, `closes`, `closed`
- `fix`, `fixes`, `fixed`
- `resolve`, `resolves`, `resolved`

These keywords automatically close the referenced issue when the PR is merged.

### Commit SHA References

Reference specific commits by their SHA:

```markdown
This was fixed in 8f5c7d2.
See commit e0c2b7e8f for details.
```

---

## Emojis & Special Formatting

### Using Emoji

Add emojis using the `:emoji-name:` shortcode syntax. GitHub supports hundreds of emoji codes.

**Example:**

```markdown
:+1: Great job!
:tada: Celebration!
:bug: Found a bug
:rocket: Launch time!
:warning: Warning
:information_source: Information
:white_check_mark: Done
:x: Failed
:books: Documentation
:lock: Security
:eyes: Review needed
:heart: Love
```

**Tip:** Start typing `:` in GitHub's web interface to get autocomplete suggestions.

### HTML Comments

Use HTML comments to add notes that won't appear in rendered Markdown:

```markdown
<!-- This is a comment that won't show up -->

<!-- 
Multi-line comments work too.
You can write internal notes here for other contributors.
This is perfect for TODOs or explanations.
-->
```

**Use cases:**
- Leaving notes for future edits
- Hiding sections during development
- Adding internal documentation
- Tracking TODOs

---

## Escaping Special Characters

Use backslash `\` to escape Markdown formatting characters:

```markdown
\*This won't be italic\*
\#This won't be a heading
\[This won't be a link\]
\`This won't be code\`
```

**Rendered:**

\*This won't be italic\*
\#This won't be a heading
\[This won't be a link\]
\`This won't be code\`

**Escapable characters:**

`\` `` ` `` `*` `_` `{}` `[]` `<>` `()` `#` `+` `-` `.` `!` `|`

Use backslash escaping when you need to display special characters literally.

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

### Badge Gallery & Practical Examples

Here's a curated collection of practical badge examples with actual rendered badges you can copy and customize:

#### Project Status & Maintenance

**Code:**
```markdown
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Status: Maintained](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/user/repo)
[![Status: Deprecated](https://img.shields.io/badge/Status-Deprecated-red.svg)]()
[![Status: Beta](https://img.shields.io/badge/Status-Beta-orange.svg)]()
[![Status: Stable](https://img.shields.io/badge/Status-Stable-brightgreen.svg)]()
```

**Rendered:**

[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Status: Maintained](https://img.shields.io/badge/Maintained%3F-yes-green.svg)]()
[![Status: Deprecated](https://img.shields.io/badge/Status-Deprecated-red.svg)]()
[![Status: Beta](https://img.shields.io/badge/Status-Beta-orange.svg)]()
[![Status: Stable](https://img.shields.io/badge/Status-Stable-brightgreen.svg)]()

---

#### License Badges

**Code:**
```markdown
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](LICENSE)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-red.svg)](LICENSE)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)](LICENSE)
```

**Rendered:**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)]()
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-orange.svg)]()
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-red.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)]()

---

#### Version & Release Badges

**Code:**
```markdown
[![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-blue.svg)](https://github.com/user/repo/releases)
[![Latest Release](https://img.shields.io/badge/Latest%20Release-v2.5.1-blue.svg)](https://github.com/user/repo/releases/latest)
[![Release Date](https://img.shields.io/badge/Release%20Date-Nov%202025-blue.svg)]()
```

**Rendered:**

[![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-blue.svg)]()
[![Latest Release](https://img.shields.io/badge/Latest%20Release-v2.5.1-blue.svg)]()
[![Release Date](https://img.shields.io/badge/Release%20Date-Nov%202025-blue.svg)]()

---

#### Language & Framework Badges

**Code:**
```markdown
[![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Node.js: 14+](https://img.shields.io/badge/Node.js-14%2B-green.svg)](https://nodejs.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-yellow.svg)]()
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0%2B-blue.svg)]()
[![Go 1.19+](https://img.shields.io/badge/Go-1.19%2B-cyan.svg)]()
```

**Rendered:**

[![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)]()
[![Node.js: 14+](https://img.shields.io/badge/Node.js-14%2B-green.svg)]()
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-yellow.svg)]()
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0%2B-blue.svg)]()
[![Go 1.19+](https://img.shields.io/badge/Go-1.19%2B-cyan.svg)]()

---

#### Platform & OS Badges

**Code:**
```markdown
[![Platform: Windows](https://img.shields.io/badge/Platform-Windows-blue.svg)]()
[![Platform: macOS](https://img.shields.io/badge/Platform-macOS-silver.svg)]()
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-orange.svg)]()
[![Cross-Platform](https://img.shields.io/badge/Cross%20Platform-Yes-brightgreen.svg)]()
```

**Rendered:**

[![Platform: Windows](https://img.shields.io/badge/Platform-Windows-blue.svg)]()
[![Platform: macOS](https://img.shields.io/badge/Platform-macOS-silver.svg)]()
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-orange.svg)]()
[![Cross-Platform](https://img.shields.io/badge/Cross%20Platform-Yes-brightgreen.svg)]()

---

#### Build & CI/CD Badges

**Code:**
```markdown
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)](https://github.com/user/repo/actions)
[![Build Status](https://img.shields.io/badge/Build-Failing-red.svg)](https://github.com/user/repo/actions)
[![Tests: 42/42 Passing](https://img.shields.io/badge/Tests-42%2F42%20passing-brightgreen.svg)]()
[![Coverage: 95%](https://img.shields.io/badge/Coverage-95%25-brightgreen.svg)]()
```

**Rendered:**

[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)]()
[![Build Status](https://img.shields.io/badge/Build-Failing-red.svg)]()
[![Tests: 42/42 Passing](https://img.shields.io/badge/Tests-42%2F42%20passing-brightgreen.svg)]()
[![Coverage: 95%](https://img.shields.io/badge/Coverage-95%25-brightgreen.svg)]()

---

#### Documentation & Links

**Code:**
```markdown
[![Documentation](https://img.shields.io/badge/Documentation-Available-blue.svg)](./docs/)
[![Wiki](https://img.shields.io/badge/Wiki-Complete-blue.svg)](./wiki/)
[![API Docs](https://img.shields.io/badge/API%20Docs-Live-blue.svg)](https://docs.example.com)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Active-brightgreen.svg)](https://user.github.io/repo/)
```

**Rendered:**

[![Documentation](https://img.shields.io/badge/Documentation-Available-blue.svg)]()
[![Wiki](https://img.shields.io/badge/Wiki-Complete-blue.svg)]()
[![API Docs](https://img.shields.io/badge/API%20Docs-Live-blue.svg)]()
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Active-brightgreen.svg)]()

---

#### Contribution & Community

**Code:**
```markdown
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Good First Issue](https://img.shields.io/badge/Good%20First%20Issue-Available-brightgreen.svg)](https://github.com/user/repo/issues?q=label%3A%22good+first+issue%22)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Open Issues](https://img.shields.io/badge/Open%20Issues-5-blue.svg)](https://github.com/user/repo/issues)
```

**Rendered:**

[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)]()
[![Good First Issue](https://img.shields.io/badge/Good%20First%20Issue-Available-brightgreen.svg)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen.svg)]()
[![Open Issues](https://img.shields.io/badge/Open%20Issues-5-blue.svg)]()

---

#### Development Status

**Code:**
```markdown
[![Development: Active](https://img.shields.io/badge/Development-Active-brightgreen.svg)]()
[![Last Commit: 2 days ago](https://img.shields.io/badge/Last%20Commit-2%20days%20ago-blue.svg)]()
[![Last Updated: Nov 2025](https://img.shields.io/badge/Last%20Updated-Nov%202025-blue.svg)]()
[![Code Quality: Good](https://img.shields.io/badge/Code%20Quality-Good-brightgreen.svg)]()
```

**Rendered:**

[![Development: Active](https://img.shields.io/badge/Development-Active-brightgreen.svg)]()
[![Last Commit: 2 days ago](https://img.shields.io/badge/Last%20Commit-2%20days%20ago-blue.svg)]()
[![Last Updated: Nov 2025](https://img.shields.io/badge/Last%20Updated-Nov%202025-blue.svg)]()
[![Code Quality: Good](https://img.shields.io/badge/Code%20Quality-Good-brightgreen.svg)]()

---

#### Support & Chat

**Code:**
```markdown
[![Chat on Slack](https://img.shields.io/badge/Chat-Slack-blue.svg)](https://slack.example.com)
[![Discord](https://img.shields.io/badge/Discord-Active-blue.svg)](https://discord.gg/example)
[![Discussions](https://img.shields.io/badge/Discussions-Welcome-blue.svg)](https://github.com/user/repo/discussions)
[![Email](https://img.shields.io/badge/Email-Contact-blue.svg)](mailto:contact@example.com)
```

**Rendered:**

[![Chat on Slack](https://img.shields.io/badge/Chat-Slack-blue.svg)]()
[![Discord](https://img.shields.io/badge/Discord-Active-blue.svg)]()
[![Discussions](https://img.shields.io/badge/Discussions-Welcome-blue.svg)]()
[![Email](https://img.shields.io/badge/Email-Contact-blue.svg)]()

---

#### Full README Header Example

Here's how to combine badges into a professional README header:

**Code:**
```markdown
# My Awesome Project

A brief, compelling description of your project.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)](https://github.com/user/repo/actions)
[![Coverage: 95%](https://img.shields.io/badge/Coverage-95%25-brightgreen.svg)]()
[![Documentation](https://img.shields.io/badge/Documentation-Available-blue.svg)](./docs/)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](CONTRIBUTING.md)

## Features

- Feature 1
- Feature 2
- Feature 3

## Quick Start

...
```

**Rendered:**

# My Awesome Project

A brief, compelling description of your project.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)]()
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Python: 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)]()
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)]()
[![Coverage: 95%](https://img.shields.io/badge/Coverage-95%25-brightgreen.svg)]()
[![Documentation](https://img.shields.io/badge/Documentation-Available-blue.svg)]()
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)]()

---

### Common Badge Types

- **License** — `https://img.shields.io/badge/License-MIT-blue.svg`
- **Version** — `https://img.shields.io/badge/version-1.0.0-blue.svg`
- **Status** — `https://img.shields.io/badge/Status-Active-brightgreen.svg`
- **Language** — `https://img.shields.io/badge/language-Python-blue.svg`
- **Platform** — `https://img.shields.io/badge/platform-Windows-blue.svg`

### Badge Colors

Common colors: `blue`, `green`, `brightgreen`, `red`, `orange`, `yellow`, `purple`, `ff69b4` (pink)

**Color meanings:**
- `brightgreen` / `green` — success, passing, active
- `blue` — information, neutral
- `orange` — warning, beta, in development
- `red` — failure, critical, deprecated
- `yellow` — caution
- `purple` / `ff69b4` — special, custom

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
