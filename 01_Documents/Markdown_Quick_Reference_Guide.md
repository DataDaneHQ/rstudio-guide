<img src="../00_Resources/markdown_guide_banner.png" alt="Markdown Quick Reference Guide" width="100%">

<br>

## Overview

A beginner-friendly reference guide to creating and formatting Markdown (`.md`) files. Markdown is a simple way to format text using plain characters — easy to read, easy to write, and supported by GitHub, RStudio, and most modern documentation platforms.

<br>

### Contents

<table align="center">
<tr>
<td width="460">

- [Creating a Markdown File](#creating-a-markdown-file)
- [Headers](#headers)
- [Text Formatting](#text-formatting)
- [Line Breaks](#line-breaks)
- [Lists](#lists)
- [Links](#links)
- [Images](#images)
- [Code](#code)
- [Blockquotes](#blockquotes)

</td>
<td width="460">

- [Horizontal Rules](#horizontal-rules)
- [Tables](#tables)
- [Task Lists](#task-lists)
- [Table of Contents](#table-of-contents)
- [GitHub-Specific Features](#github-specific-features)
- [Best Practices](#best-practices)
- [Common Mistakes](#common-mistakes)
- [Quick Reference Table](#quick-reference-table)
- [Useful Resources](#useful-resources)

</td>
</tr>
</table>

---

<br>

## Creating a Markdown File

### In RStudio

1. Go to **File → New File → Text File**
2. Write your content using Markdown syntax
3. Go to **File → Save As** and name it with a `.md` extension (e.g. `notes.md`)

### In Any Text Editor

1. Open Notepad, TextEdit, or any plain text editor
2. Write your content
3. Save with a `.md` extension

---

<br>

## Headers

Use `#` symbols for headers. More `#` symbols = smaller header.
````markdown
# Header 1 (Largest)
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6 (Smallest)
````

> [!TIP]
> Don't skip header levels — move from H1 to H2 to H3 in order. Skipping levels (e.g. H1 → H3) breaks document structure and accessibility.

---

<br>

## Text Formatting
````markdown
**Bold text**
*Italic text*
***Bold and italic***
~~Strikethrough~~
<mark>Highlight</mark>
````

**Result:**

| Syntax | Output |
|---|---|
| `**Bold**` | **Bold** |
| `*Italic*` | *Italic* |
| `***Bold and italic***` | ***Bold and italic*** |
| `~~Strikethrough~~` | ~~Strikethrough~~ |
| `<mark>Highlight</mark>` | <mark>Highlight</mark> |

---

<br>

## Line Breaks

**Single line break** — End a line with two spaces, then press Enter:
````markdown
This is line one.  
This is line two.
````

**Forced line break** — Use `<br>` for explicit spacing:
````markdown
This is line one.

<br>

This is line two.
````

> [!NOTE]
> Pressing Enter once won't create a visible line break — text will flow together. You need either two trailing spaces or `<br>`.

---

<br>

## Lists

**Unordered (bullet) lists** — Use `*`, `-`, or `+`:
````markdown
* Item 1
* Item 2
  * Sub-item 2a (indent with 2 spaces)
  * Sub-item 2b
* Item 3
````

**Result:**
* Item 1
* Item 2
  * Sub-item 2a
  * Sub-item 2b
* Item 3

<br>

**Ordered (numbered) lists:**
````markdown
1. First item
2. Second item
3. Third item
   1. Sub-item 3a
   2. Sub-item 3b
````

**Result:**
1. First item
2. Second item
3. Third item
   1. Sub-item 3a
   2. Sub-item 3b

> [!TIP]
> Be consistent — pick one bullet style (`*` or `-`) and stick with it throughout your document.

---

<br>

## Links
````markdown
[Link text](https://www.example.com)
[Link with hover text](https://www.example.com "This appears on hover")
````

**Result:**
[Link text](https://www.example.com)

---

<br>

## Images

**Standard Markdown:**
````markdown
![Alt text description](path/to/image.png)
````

**HTML — use this when you need to control image size:**
````html
<img src="path/to/image.png" alt="Description" width="700">
````

> [!TIP]
> Always write descriptive alt text — it improves accessibility and appears if the image fails to load. For GitHub docs, 600–750px width works well for screenshots.

---

<br>

## Code

**Inline code** — wrap with single backticks:
````markdown
This is `inline code` within a sentence.
````

**Result:** This is `inline code` within a sentence.

<br>

**Code blocks** — wrap with triple backticks and specify the language:
````markdown
```r
# R code example
x <- c(1, 2, 3)
mean(x)
```
````

**Result:**
````r
# R code example
x <- c(1, 2, 3)
mean(x)
````

**Supported languages:** `r`, `python`, `javascript`, `html`, `css`, `bash`, `sql` and many more.

---

<br>

## Blockquotes

Use `>` for blockquotes:
````markdown
> This is a blockquote.
> It can span multiple lines.
>
> It can also have multiple paragraphs.
````

**Result:**
> This is a blockquote.
> It can span multiple lines.
>
> It can also have multiple paragraphs.

---

<br>

## Horizontal Rules

Create a dividing line with three or more dashes:
````markdown
---
````

---

<br>

## Tables
````markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Data     | Data     |
| Row 2    | Data     | Data     |
````

**Result:**

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Data     | Data     |
| Row 2    | Data     | Data     |

<br>

**Column alignment:**
````markdown
| Left aligned | Centre aligned | Right aligned |
|:-------------|:--------------:|--------------:|
| Text         | Text           | Text          |
````

| Syntax | Alignment |
|---|---|
| `:---` | Left |
| `:---:` | Centre |
| `---:` | Right |

---

<br>

## Task Lists
````markdown
- [x] Completed task
- [ ] Incomplete task
- [ ] Another incomplete task
````

**Result:**
- [x] Completed task
- [ ] Incomplete task
- [ ] Another incomplete task

---

<br>

## Table of Contents

Markdown automatically creates anchor links for all headers. Use these to build a clickable table of contents.

**Rules for anchor names:**

| Header | Anchor |
|---|---|
| `## My Header` | `#my-header` |
| `## Code Blocks` | `#code-blocks` |
| `## What's This?` | `#whats-this` |
| `## Step 1: Setup` | `#step-1-setup` |

- Convert to lowercase
- Replace spaces with hyphens
- Remove special characters and punctuation

**Example:**
````markdown
## Contents
- [Creating a Markdown File](#creating-a-markdown-file)
- [Headers](#headers)
- [Tables](#tables)
````

> [!TIP]
> When in doubt about an anchor name, click the header on GitHub and check the URL — that's the exact anchor. Use a table of contents for documents with 7 or more sections.

---

<br>

## GitHub-Specific Features

These features are supported on GitHub but may not render in RStudio's preview pane.

### Alerts (Callout Boxes)
````markdown
> [!NOTE]
> Useful information the reader should know.

> [!TIP]
> Helpful advice for doing things better.

> [!IMPORTANT]
> Key information required for success.

> [!WARNING]
> Urgent information — potential issues ahead.

> [!CAUTION]
> Advises about risks or negative outcomes.
````

**Result:**

> [!NOTE]
> Useful information the reader should know.

> [!TIP]
> Helpful advice for doing things better.

> [!IMPORTANT]
> Key information required for success.

> [!WARNING]
> Urgent information — potential issues ahead.

> [!CAUTION]
> Advises about risks or negative outcomes.

---

<br>

### Emoji

GitHub supports emoji shortcodes:
````markdown
:smile: :rocket: :thumbsup: :warning:
````

**Result:** 😄 🚀 👍 ⚠️

[Full emoji list](https://github.com/ikatyang/emoji-cheat-sheet)

---

<br>

## Best Practices

1. **Use blank lines between elements** — add spacing between headers, paragraphs, and lists for better readability
2. **Be consistent** — pick one bullet style (`*` or `-`) and stick with it throughout
3. **Preview as you go** — RStudio has a preview button; GitHub renders on save
4. **Keep it simple** — Markdown is designed to be readable as plain text too
5. **Use headers logically** — don't skip levels (H1 → H2 → H3, not H1 → H3)
6. **Write descriptive alt text** — every image should have meaningful alt text
7. **Specify code languages** — always declare the language in code blocks for syntax highlighting

---

<br>

## Common Mistakes

❌ **No space after `#`**
````markdown
#This won't render as a header
````
✅ **Correct:**
````markdown
# This renders correctly
````

---

<br>

❌ **Missing blank lines between elements**
````markdown
# Header
Text immediately after looks cramped.
````
✅ **Correct:**
````markdown
# Header

Text with proper spacing below.
````

---

<br>

❌ **Wrong indentation for sub-lists**
````markdown
* Item
    * Sub-item (4 spaces — too many)
````
✅ **Correct:**
````markdown
* Item
  * Sub-item (2 spaces)
````

---

<br>

❌ **Skipping header levels**
````markdown
# Header 1
### Header 3 (skipped H2)
````
✅ **Correct:**
````markdown
# Header 1
## Header 2
### Header 3
````

---

<br>

## Quick Reference Table

| Element | Syntax |
|---|---|
| Header | `# H1` `## H2` `### H3` |
| Bold | `**bold**` |
| Italic | `*italic*` |
| Bold and italic | `***bold and italic***` |
| Strikethrough | `~~strikethrough~~` |
| Link | `[text](url)` |
| Image | `![alt](path)` |
| Inline code | `` `code` `` |
| Code block | ` ```language ` |
| Blockquote | `> quote` |
| Unordered list | `* item` or `- item` |
| Ordered list | `1. item` |
| Horizontal rule | `---` |
| Task list | `- [ ] task` |
| Line break | `<br>` |
| Table | `\| col \| col \|` |

---

<br>

## Useful Resources

- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Markdown Documentation](https://docs.github.com/en/get-started/writing-on-github)
- [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
- [Emoji Cheat Sheet](https://github.com/ikatyang/emoji-cheat-sheet)

---

<br>

*[README](../README.md)*