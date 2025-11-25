# Markdown on GitHub (GFM)

This is a comprehensive guide to **Markdown** and **GitHub Flavored Markdown (GFM)** — the formatting language used in README files, issues, pull requests, discussions, and documentation on GitHub.

Whether you're writing your first README or crafting detailed documentation, this guide covers everything from basic syntax to advanced GitHub-specific features.

https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax

https://www.markdownguide.org/basic-syntax/

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

Markdown is a lightweight markup language that converts plain text into formatted HTML. It's easy to read and write, making it perfect for documentation.

GitHub Flavored Markdown (GFM) extends standard Markdown with features like task lists, tables, strikethrough, autolinks, mentions, issue references, and code blocks with syntax highlighting.

**Why Use Markdown?**
- Simple & readable
- Version-control friendly
- Portable
- GitHub-native

---

## Basic Syntax

**Paragraphs:**
Separate paragraphs with blank lines. Line breaks within a paragraph are ignored unless you end a line with two spaces or a backslash.

```markdown
This is a paragraph.

This is another paragraph.
```

**Rendered:**
This is a paragraph.

This is another paragraph.

---

## Headings

Create headings using `#` symbols. One `#` is the largest (H1), six `#` symbols is the smallest (H6).

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

**Best Practices:**
- Use headings hierarchically
- Only one H1 per document
- Headings create anchor links: `[link text](#heading-name)`

---

## Emphasis & Text Styling

**Italic, Bold, Bold-Italic, Strikethrough:**
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

**Subscript & Superscript:**
Use HTML tags `<sub>` and `<sup>`.
```markdown
H<sub>2</sub>O
E=mc<sup>2</sup>
```

**Underline:**
Use `<ins>` or `<u>` HTML tags.
```markdown
This is <ins>underlined</ins>.
```

---

## Lists

**Unordered Lists:**
```markdown
- Item 1
- Item 2
  - Nested item 2a
  - Nested item 2b
- Item 3
```

**Ordered Lists:**
```markdown
1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item
```

**Task Lists (GitHub):**
```markdown
- [x] Complete project setup
- [ ] Write documentation
```

---

## Blockquotes

Use `>` at the start of a line. Nest with `>>`.
```markdown
> This is a blockquote.
>> Nested blockquote.
```

Blockquotes can contain lists, code, headings, and emphasis.

---

## Code

**Inline Code:**
Wrap with single backticks: `` `code` ``

**Code Blocks:**
Triple backticks, optionally specify language:
```markdown
```python
print("Hello, world!")
```
```

**Indented Code Blocks:**
Indent by 4 spaces (less common).

---

## Tables

Use pipes `|` and hyphens `-` for headers.
```markdown
| Name  | Age |
|-------|-----|
| Alice | 30  |
| Bob   | 25  |
```

Align columns with colons:
- `:---` left, `:---:` center, `---:` right

---

## Images & Media

**Inline Images:**
```markdown
![Alt text](image-url)
```

**Relative Paths:**
```markdown
![Screenshot](./images/screenshot.png)
```

**Images with Links:**
```markdown
[![Alt text](image-url)](https://example.com)
```

**GIFs & Videos:**
Use GIFs as images, link to videos.

---

## Links & References

**Inline Links:**
```markdown
[GitHub](https://github.com)
```

**Links with Titles:**
```markdown
[GitHub](https://github.com "The GitHub website")
```

**Reference-Style Links:**
```markdown
[GitHub][github-ref]
[github-ref]: https://github.com
```

**Auto-Links:**
```markdown
<https://github.com>
```

---

## GitHub-Specific Features

**Mentions:**
`@username` or `@org/team-name`

**Issue/PR References:**
`Fixes #42`, `Closes owner/repo#123`

**Commit SHA References:**
`This was fixed in 8f5c7d2`

**Emoji:**
`:tada:`, `:bug:`, `:rocket:`, `:heart:`

---

## Advanced Formatting

**Blockquotes:**
`>` for blockquotes, nest with `>>`

**Callout Boxes:**
Use blockquotes with bold headers for notes/warnings/tips.

**Horizontal Rules:**
`---`, `***`, `___`

**HTML Passthrough:**
Inline HTML for advanced formatting.

**Footnotes:**
`This needs a citation[^1]`
`[^1]: Footnote text.`

**Alerts (GitHub):**
`> [!NOTE]`, `> [!TIP]`, `> [!IMPORTANT]`, `> [!WARNING]`, `> [!CAUTION]`

**Color Models:**
`#FF5733`, `rgb(255,87,51)`, `hsl(9,100%,60%)` (color preview in issues/PRs)

**Section Links & Anchors:**
Headings create anchors, custom anchors with `<a name="anchor"></a>`

**Relative Links:**
`[Link](./file.md)`

**Line Breaks:**
Two spaces, backslash, `<br/>`, or blank line.

---

## Mentions & References

Mention users/teams, reference issues/PRs, commit SHAs.

---

## Emojis & Special Formatting

Use `:emoji-name:` for emoji. HTML comments: `<!-- hidden -->`

---

## Escaping Special Characters

Use backslash `\` to escape Markdown formatting characters.

---

## Accessibility Best Practices

- Use descriptive alt text for images
- Use logical heading order
- Don't rely on color alone
- Use clear link text
- Use simple, clear language

---

## Troubleshooting & Tips

- Preview before committing
- Use fenced code blocks
- Keep it simple
- Consistent style
- Check links in PRs
- Use relative paths

---

## Quick Reference Cheatsheet

| Element         | Syntax           | Example                  |
|----------------|------------------|--------------------------|
| Heading        | `# Heading`      | # Heading                |
| Bold           | `**bold**`       | **bold**                 |
| Italic         | `*italic*`       | *italic*                 |
| Strikethrough  | `~~text~~`       | ~~text~~                 |
| Inline code    | `` `code` ``     | `code`                   |
| Code block     | ` ```language `  | (see examples above)     |
| Link           | `[text](url)`    | [GitHub](https://github.com) |
| Image          | `![alt](url)`    | (see examples above)     |
| Unordered list | `- item`         | (see examples above)     |
| Ordered list   | `1. item`        | (see examples above)     |
| Task list      | `- [ ] task`     | (see examples above)     |
| Table          | `| column |`     | (see examples above)     |
| Blockquote     | `> quote`        | (see examples above)     |
| Mention        | `@username`      | @username                |
| Issue ref      | `#123`           | #123                     |
| Horizontal rule| `---`            | (see examples above)     |
| Emoji          | `:tada:`         | 🎉                       |

---

## Badges & Shields

Badges are small images in your README that show project status. Use [Shields.io](https://shields.io) for custom badges.

**Example:**
```markdown
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
```

---

## GitHub Labels & Repository Organization

Labels are tags for issues/PRs. Create custom labels for type, priority, status, scope.

---

## Repository Metadata & Topics

Add a description and topics in repo settings for discoverability.

---

## Repository Templates

Make your repo a template in settings so others can use your structure.

---

## Further Resources

- [CommonMark Spec](https://spec.commonmark.org/)
- [GitHub Flavored Markdown](https://github.github.com/gfm/)
- [GitHub Docs on Markdown](https://docs.github.com/en/get-started/writing-on-github)
- [Markdown Guide](https://www.markdownguide.org/)
- [Emoji Cheatsheet](https://www.webfx.com/tools/emoji-cheat-sheet/)
- [Shields.io](https://shields.io)
- [GitHub Labels Guide](https://docs.github.com/en/issues/using-labels-and-milestones)

---

**Happy writing!** 📝

