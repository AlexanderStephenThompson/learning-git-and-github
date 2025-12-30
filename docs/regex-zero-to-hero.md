# Regex Zero to Hero

A practical, end-to-end guide to regular expressions (regex): from the simplest matches to advanced techniques and real-world troubleshooting.

> **Note on flavors:** Regex syntax varies by engine (“flavor”). This tutorial focuses on broadly supported concepts and calls out differences for **PCRE/PCRE2**, **JavaScript**, and **Python `re`** where it matters.

---

## Table of contents

1. [What is regex?](#what-is-regex)
2. [Your first matches](#your-first-matches)
3. [Character classes](#character-classes)
4. [Quantifiers and greediness](#quantifiers-and-greediness)
5. [Anchors and boundaries](#anchors-and-boundaries)
6. [Grouping and alternation](#grouping-and-alternation)
7. [Escaping, raw strings, and readability](#escaping-raw-strings-and-readability)
8. [Flags / modifiers](#flags--modifiers)
9. [Captures, named groups, and backreferences](#captures-named-groups-and-backreferences)
10. [Lookarounds (advanced)](#lookarounds-advanced)
11. [Practical recipes](#practical-recipes)
12. [Testing and debugging workflow](#testing-and-debugging-workflow)
13. [Performance and catastrophic backtracking](#performance-and-catastrophic-backtracking)
14. [Common pitfalls](#common-pitfalls)
15. [Exercises (with solutions)](#exercises-with-solutions)
16. [Cheat sheet](#cheat-sheet)

---

## What is regex?

A **regular expression** is a mini-language for describing patterns in text. You can use regex to:

- validate input (emails, IDs, formats)
- search text
- extract parts of text (capture groups)
- replace text (find/replace)
- tokenize or split strings

Regex is powerful—but it’s easy to write patterns that are fragile, slow, or accidentally match the wrong thing. This guide aims to make you confident and careful.

### Regex engines (flavors)

Common engines include:

- **PCRE/PCRE2** (many tools, PHP, ripgrep features, etc.)
- **JavaScript** (ECMAScript regex)
- **Python `re`**
- **RE2** (Google; used by Go’s `regexp`, many cloud products) — notably avoids some advanced features to guarantee linear-time performance.

When a feature differs by engine, this tutorial indicates it.

---

## Your first matches

### Literal characters

The simplest regex is just literal text.

- Pattern: `cat`
- Matches: `cat` in `the cat sat`

Most regex searches are “find a substring.” Unless you add anchors, regex will match **anywhere**.

### The dot: `.`

- `.` matches “any character” (except newline in many modes).

Examples:

- Pattern: `c.t`
- Matches: `cat`, `cot`, `c9t`
- Doesn’t match: `ct` (missing a character), `coat` (extra character)

> Pitfall: `.` matches a literal dot only if escaped: `\\.`

### Quick exercise

1. Write a regex to match `color` or `colour`.
2. Write a regex that matches `a` followed by any single character followed by `z`.

(Answers later.)

---

## Character classes

Character classes let you match one character from a set.

### Bracket classes: `[...]`

- `[abc]` matches `a` **or** `b` **or** `c`
- `[a-z]` matches any lowercase letter a–z
- `[A-Za-z0-9_]` matches “word-ish” characters

Examples:

- `gr[ae]y` matches `gray` or `grey`
- `file[0-9]` matches `file0` … `file9`

### Negated classes: `[^...]`

- `[^0-9]` matches any character that is **not** a digit

Example:

- `[^\\s]+` matches a “token” of non-whitespace characters

### Important: `-`, `]`, `^` placement rules

Inside `[...]`:

- `-` creates ranges unless it’s first/last or escaped: `[a-z]`, `[-az]`, `[az-]`, `[a\\-z]`
- `]` ends the class unless first or escaped: `[]a]` matches `]` or `a`
- `^` negates only if it’s the first character: `[^a]` (negated) vs `[a^]` (literal `^`)

### Shorthand classes

Most flavors support:

- `\\d` digit (`[0-9]` typically)
- `\\D` not a digit
- `\\w` “word” character (letters/digits/underscore; may include more in Unicode mode)
- `\\W` not a word character
- `\\s` whitespace
- `\\S` not whitespace

> Unicode note: In JS and Python, `\\w` behavior depends on Unicode flags/modes.

### POSIX classes (some tools)

In some tools (e.g., `grep -E`), you may see:

- `[[:digit:]]`, `[[:alpha:]]`, `[[:space:]]`

They can be more portable in POSIX contexts.

---

## Quantifiers and greediness

Quantifiers say how many times the preceding item repeats.

### Basic quantifiers

- `?` → 0 or 1
- `*` → 0 or more
- `+` → 1 or more
- `{n}` → exactly n
- `{n,}` → at least n
- `{n,m}` → between n and m

Examples:

- `colou?r` matches `color` and `colour`
- `\\d+` matches `7`, `42`, `2025`
- `\\d{4}-\\d{2}-\\d{2}` matches a date like `2025-12-30`

### Greedy vs lazy

By default, quantifiers are **greedy**: they match as much as possible.

- Greedy: `.*` eats a lot.
- Lazy (non-greedy): `*?`, `+?`, `??`, `{n,m}?` match as little as possible.

Example text:

```
\"a\" \"b\" \"c\"
```

- Pattern: `\".*\"` matches from the first `\"` to the **last** `\"` (one big match)
- Pattern: `\".*?\"` matches each quoted chunk: `\"a\"`, `\"b\"`, `\"c\"`

> RE2 note: RE2 supports lazy quantifiers. Some older POSIX ERE tools do not.

### Quantifying groups

Quantifiers apply to the **immediately preceding token**.

- `ab+` means `a` then one-or-more `b`
- `(ab)+` means one-or-more repetitions of `ab`

---

## Anchors and boundaries

Anchors match positions, not characters.

### Line/string anchors

- `^` start of line/string
- `$` end of line/string

Text: `hello`

- `^hello$` matches the **entire** string exactly
- `hello$` matches `hello` at the end

### Word boundaries

- `\\b` word boundary (between `\\w` and `\\W`)
- `\\B` not a word boundary

Examples:

- `\\bcat\\b` matches `cat` as a whole word
- In `concatenate`, `\\bcat\\b` does **not** match

> Pitfall: `\\b` depends on `\\w` definition. It isn’t “letter boundary” in Unicode-aware contexts; it’s “word-char boundary.”

### Multiline behavior

In many flavors, `^` and `$` match per-line only in **multiline mode**:

- JavaScript: flag `m`
- Python: `re.MULTILINE`

---

## Grouping and alternation

### Alternation: `|`

- `cat|dog` matches `cat` or `dog`

Use grouping to limit alternation scope:

- `I like (cats|dogs)`

### Capturing groups: `(...)`

Groups capture the matched substring.

Example:

- Pattern: `([A-Za-z]+)\\s+(\\d+)`
- Text: `Room 42`
- Group 1: `Room`
- Group 2: `42`

### Non-capturing groups: `(?:...)`

Use when you need grouping but don’t want capture numbering.

- `(?:https?)://` matches `http://` or `https://`

This keeps your capture groups stable and often improves readability.

---

## Escaping, raw strings, and readability

### Escaping special characters

Regex metacharacters commonly include:

- `. ^ $ * + ? ( ) [ ] { } | \\

To match them literally, escape them: `\\.` `\\+` `\\?` etc.

### Double-escaping in string literals

In many languages, backslash is also special in strings.

#### Python

Prefer raw strings:

```py
import re
re.search(r"\\d+\\.\\d+", "Version 1.23")
```

Without raw strings, you must double escape:

```py
re.search("\\\\d+\\\\.\\\\d+", "Version 1.23")
```

#### JavaScript

Regex literal:

```js
/\\d+\\.\\d+/.test("Version 1.23")
```

String-based constructor:

```js
new RegExp("\\\\d+\\\\.\\\\d+")
```

### Readability tips

- Build incrementally
- Use `(?:...)` for structure
- Prefer explicit character classes over `.`
- Comment / use verbose mode where available (Python `re.VERBOSE`)

---

## Flags / modifiers

Flags change how the engine interprets the pattern.

Common flags:

- **i**: case-insensitive
- **m**: multiline (`^`/`$` match line boundaries)
- **s**: dotall (dot matches newline)
- **g** (JS): global (find all matches)
- **u** (JS): Unicode mode

### Examples

#### JavaScript

```js
const re = /^hello$/im;
```

#### Python

```py
re.compile(r"^hello$", re.IGNORECASE | re.MULTILINE)
```

---

## Captures, named groups, and backreferences

### Named capturing groups

Named groups improve clarity.

#### Python

```py
m = re.search(r"(?P<user>[A-Za-z0-9_]+)@(?P<domain>[A-Za-z0-9.-]+)", "alice@example.com")
print(m.group("user"))   # alice
print(m.group("domain")) # example.com
```

#### JavaScript

```js
const m = "alice@example.com".match(/(?<user>[A-Za-z0-9_]+)@(?<domain>[A-Za-z0-9.-]+)/);
console.log(m.groups.user);
```

### Backreferences

Backreferences match the **same text** as a prior capturing group.

- Pattern: `\\b(\\w+)\\s+\\1\\b`
- Matches repeated words like: `the the`, `is is`

> RE2 note: RE2 does **not** support backreferences.

### Replacement with capture groups

Different tools use different replacement syntax.

- Many use `$1`, `$2`, ...
- Python uses `\\1` in replacement strings (or `\\g<name>`)

Example (Python):

```py
re.sub(r"(\\w+),(\\w+)", r"\\2, \\1", "last,first")
```

---

## Lookarounds (advanced)

Lookarounds assert that something **is** or **is not** next to your match without consuming it.

### Lookahead

- Positive: `X(?=Y)` → match X only if followed by Y
- Negative: `X(?!Y)` → match X only if not followed by Y

Example: match `foo` only when followed by `bar`:

- `foo(?=bar)` matches `foo` in `foobar` but not in `foobaz`

### Lookbehind

- Positive: `(?<=X)Y` → match Y only if preceded by X
- Negative: `(?<!X)Y`

Example: match `USD` only when preceded by `$`:

- `(?<=\\$)\\d+(?:\\.\\d{2})?` matches `10.00` in `$10.00`

Flavor differences:

- **JavaScript**: supports lookbehind in modern runtimes, but not all older engines.
- **Python**: supports lookbehind, but it must be fixed-width.
- **RE2**: no lookbehind.

---

## Practical recipes

These aren’t “perfect validators” (often a bad idea), but useful patterns for common tasks.

### 1) Trim whitespace (find)

- Leading whitespace: `^\\s+`
- Trailing whitespace: `\\s+$`

### 2) Find duplicate words

- `\\b(\\w+)\\s+\\1\\b` (case-sensitive)
- Case-insensitive: add flag `i`

### 3) Extract domain from URL (simple)

```regex
https?://([^/]+)
```

Group 1 captures the host.

### 4) Validate a simple “slug”

Lowercase slug with dashes:

```regex
^[a-z0-9]+(?:-[a-z0-9]+)*$
```

### 5) Parse a key=value line

```regex
^\\s*([A-Za-z_][A-Za-z0-9_]*)\\s*=\\s*(.*?)\\s*$
```

- Group 1: key
- Group 2: value (lazy-ish via `.*?`)

### 6) Match an ISO-like date (basic)

```regex
^\\d{4}-\\d{2}-\\d{2}$
```

> This checks format, not calendar validity.

### 7) Find hex colors

```regex
#(?:[0-9A-Fa-f]{3}|[0-9A-Fa-f]{6})\\b
```

---

## Testing and debugging workflow

1. **Write a minimal test set**: include expected matches and non-matches.
2. **Start small**: match an anchor or a keyword first.
3. Add constraints one at a time.
4. Use a regex visualizer/tester:
   - regex101.com (PCRE)
   - regexr.com (JS)
   - Python: `re` with unit tests
5. When replacing, test with a “dry run” or preview.

### Debug checklist

- Did you forget anchors (`^`/`$`) for validation?
- Are you accidentally matching too much because of greedy `.*`?
- Are your escapes correct for your language (double escape)?
- Did you mean a literal dot `.` or “any char” dot?
- Are you operating in multiline or dotall mode unexpectedly?

---

## Performance and catastrophic backtracking

Some regex engines (notably backtracking engines like PCRE, Java, Python, JS) can become extremely slow on certain patterns and inputs.

### A classic problematic pattern

```regex
^(a+)+$
```

On a string like `aaaaaaaaaaaaaaaaaaaaX`, the engine may backtrack exponentially.

### Safer approaches

- Avoid nested quantifiers like `(.*)+`, `(a+)+`.
- Prefer more specific classes: use `[^\\n]*` instead of `.*` if you don’t want newlines.
- Use atomic groups / possessive quantifiers **where supported**:
  - Possessive: `a++`, `.*+`
  - Atomic group: `(?>...)`

> RE2 avoids catastrophic backtracking by design but lacks some features.

---

## Common pitfalls

1. **Using `.*` too early**
   - Problem: `start.*end` may swallow too much.
   - Fix: constrain it (`[^\\n]*`), or make it lazy (`.*?`), or anchor more precisely.

2. **Forgetting to escape**
   - `.` `?` `+` `(` `[` are special.
   - If you want literal `.` use `\\.`.

3. **Assuming regex validates everything**
   - Email/URL “perfect” validation is complex.
   - Use regex for a **reasonable format check**, and rely on application logic for full validation.

4. **Mismatched character classes for Unicode**
   - `\\w` may include more than `[A-Za-z0-9_]`.
   - If you need ASCII-only, specify it (e.g., `[A-Za-z0-9_]`).

5. **Boundary confusion**
   - `\\b` is “word boundary,” not “letter boundary.”

6. **Over-capturing**
   - Prefer `(?:...)` for non-capturing structure.

7. **Engine differences**
   - Lookbehind, atomic groups, named group syntax vary.

---

## Exercises (with solutions)

### Exercise set A — Basics

1. Match either `color` or `colour`.
2. Match `a` + any char + `z`.
3. Match a 5-digit ZIP code (US).
4. Match a 9-digit ZIP+4 like `12345-6789`.

**Solutions**

1. `colou?r`
2. `a.z`
3. `^\\d{5}$`
4. `^\\d{5}(?:-\\d{4})?$`

### Exercise set B — Grouping and extraction

Given: `Name: Ada Lovelace, Age: 36`

1. Capture first and last name.
2. Capture the age number.

**One possible solution**

- `Name:\\s*([A-Za-z]+)\\s+([A-Za-z]+),\\s*Age:\\s*(\\d+)`

Groups:

- 1: first name
- 2: last name
- 3: age

### Exercise set C — Avoiding overmatching

Text:

```
<item>one</item><item>two</item><item>three</item>
```

1. Write a regex to match each `<item>...</item>` block.
2. Why is the naive pattern `/<item>.*<\\/item>/` wrong?

**Solution idea**

1. `<item>.*?</item>` (lazy)
2. Because `.*` is greedy and will match from the first `<item>` to the last `</item>`.

> Note: Parsing nested HTML/XML with regex is fragile; use a parser for real documents.

---

## Cheat sheet

### Core tokens

- `.` any char (except newline unless dotall)
- `\\d` digit, `\\w` word, `\\s` whitespace
- `[abc]` one of a/b/c
- `[^abc]` not a/b/c
- `^` start, `$` end
- `\\b` word boundary

### Quantifiers

- `?` 0 or 1
- `*` 0+
- `+` 1+
- `{n}` exactly n
- `{n,m}` between n and m
- Append `?` for lazy (e.g., `*?`)

### Grouping

- `( ... )` capture
- `(?: ... )` non-capture
- `A|B` alternation

### Lookarounds

- `(?=...)` lookahead
- `(?!...)` negative lookahead
- `(?<=...)` lookbehind (not everywhere)
- `(?<!...)` negative lookbehind

---

## Next steps

- Practice by writing regexes against real data.
- Keep a personal snippet library of patterns you’ve tested.
- When patterns grow, consider writing a small parser instead—regex is one tool, not the tool for everything.
