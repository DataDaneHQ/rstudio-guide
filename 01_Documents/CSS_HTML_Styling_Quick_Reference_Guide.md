<img src="../00_Resources/css_guide_banner.png" alt="CSS HTML Styling Quick Reference Guide" width="100%">

<br>

## Overview

A practical reference guide for styling HTML reports in R Markdown and Quarto. Each section includes the CSS, usage syntax, and compatibility indicators so you know exactly what works where.

For guidance on linking a stylesheet to your report see the [R Markdown Quick Reference Guide](RMD_Quick_Reference_Guide.md#yaml-header).

> [!NOTE]
> This guide culminates in a complete `style.css` file — see [Complete style.css File](#complete-stylecss-file). Copy it directly into your project folder and reference it in your YAML header with `css: style.css`.

---

<br>

## Contents

<table align="center">
<tr>
<td width="550">

- [Compatibility Key](#compatibility-key)
- [Colour Palette](#colour-palette)
- [Body & Layout](#body--layout)
- [Typography](#typography)
- [Headings](#headings)
- [Hyperlinks](#hyperlinks)
- [Table of Contents](#table-of-contents)
- [Code Blocks](#code-blocks)

</td>
<td width="550">

- [Tables](#tables)
- [Callout Boxes](#callout-boxes)
- [Metric Cards](#metric-cards)
- [Toggle Button Styling](#toggle-button-styling)
- [Section Dividers](#section-dividers)
- [Utility Classes](#utility-classes)
- [Complete style.css File](#complete-stylecss-file)

</td>
</tr>
</table>

---

<br>

## Compatibility Key

Each section includes a compatibility indicator showing which platform the styles work on.

| Indicator | Meaning |
|---|---|
| *R Markdown* ✅ *Quarto* ✅ | Works on both platforms without changes |
| *R Markdown* ✅ *Quarto* ⬜ | R Markdown only — requires changes for Quarto |
| *R Markdown* ⬜ *Quarto* ✅ | Quarto only |

---

<br>

## Colour Palette

*R Markdown* ✅ *Quarto* ✅

These are the core colours used consistently across all styles in this guide. Update these values here and in the `style.css` file to retheme your reports globally.

| Hex | Use |
|---|---|
| `#040708` | Primary text, deep backgrounds |
| `#202c2d` | Dark section backgrounds |
| `#3d4846` | Secondary backgrounds, borders |
| `#727970` | Muted text, subtle borders |
| `#3ba5ae` | Primary accent, borders, highlights |
| `#33C7BA` | Secondary accent, hover states |

---
<br>

## Body & Layout

*R Markdown* ✅ *Quarto* ✅

Controls the overall page appearance — background, font, and content width.

```css
body {
    font-family: Arial, sans-serif;
    font-size: 12px;
    color: #000000;
    background-color: #ffffff;
    line-height: 1.6;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}
```

| Property | What it does |
|---|---|
| `font-family` | Sets the default font across the report |
| `font-size` | Base font size — all other sizes scale from this |
| `color` | Default text colour |
| `line-height` | Spacing between lines — `1.6` is comfortable for reading |
| `max-width` | Prevents content stretching too wide on large screens |
| `margin: 0 auto` | Centres the content on the page |

---

<br>

## Typography

*R Markdown* ✅ *Quarto* ✅

Controls the appearance of general body text — paragraphs, bold, and italic elements.

### Paragraphs

```css
p {
    margin: 0 0 12px 0;
    color: #000000;
}
```

`p` targets every paragraph of text in your report. 

| Property | What it does |
|---|---|
| `margin: 0 0 12px 0` | Adds 12px of space below each paragraph — the four values are top, right, bottom, left. This stops paragraphs sitting directly on top of each other |
| `color` | Sets the default paragraph text colour |

---

### Bold Text

```css
strong {
    color: #202c2d;
}
```

`strong` targets anything wrapped in `**double asterisks**` in your Markdown. Setting a colour here makes bold text slightly different from regular text — in this case a dark charcoal rather than pure black, which is subtler and easier on the eye.

---

### Italic Text

```css
em {
    color: #3d4846;
}
```

`em` targets anything wrapped in `*single asterisks*` in your Markdown. Same principle as bold — a slightly lighter shade creates a gentle visual distinction without being distracting.

---

### Why bother with these?

Without these styles your report inherits the browser's default typography — which is functional but generic. Defining `p`, `strong`, and `em` gives you consistent, intentional text styling that matches your colour palette throughout the entire report.

---
<br>

## Headings

*R Markdown* ✅ *Quarto* ✅

Consistent heading hierarchy using Montserrat and your colour palette.

```css
h1 {
    font-family: 'Montserrat', sans-serif;
    font-size: 24px;
    font-weight: 700;
    color: #3ba5ae;
    border-bottom: 2px solid #3ba5ae;
    padding-bottom: 8px;
    margin-top: 40px;
    margin-bottom: 16px;
    letter-spacing: 1px;
}

h2 {
    font-family: 'Montserrat', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: #202c2d;
    border-bottom: 1px solid #3d4846;
    padding-bottom: 6px;
    margin-top: 32px;
    margin-bottom: 12px;
}

h3 {
    font-family: 'Montserrat', sans-serif;
    font-size: 16px;
    font-weight: 600;
    color: #3d4846;
    margin-top: 24px;
    margin-bottom: 8px;
}

h4 {
    font-family: 'Montserrat', sans-serif;
    font-size: 14px;
    font-weight: 600;
    color: #727970;
    margin-top: 16px;
    margin-bottom: 6px;
}
```

| Property | What it does |
|---|---|
| `border-bottom` | Adds an underline to `h1` and `h2` for visual separation |
| `letter-spacing` | Slight spacing on `h1` for a polished look |
| `margin-top` | Controls spacing above each heading level |

> [!TIP]
> Add this to your `.Rmd` or Quarto document to load Montserrat from Google Fonts:
> ```html
> <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap" rel="stylesheet">
> ```

---
<br>

## Hyperlinks

*R Markdown* ✅ *Quarto* ✅

```css
a {
    color: #3ba5ae;
    text-decoration: none;
}

a:hover {
    color: #33C7BA;
    text-decoration: underline;
}
```

> [!TIP]
> `text-decoration: none` removes the default underline. It reappears on hover to confirm the link is clickable.

---
<br>

## Table of Contents

*R Markdown* ✅ *Quarto* ⬜

Styles the floating TOC sidebar generated by `toc_float: true` in your YAML. The `#TOC` selector is R Markdown specific — Quarto uses different selectors depending on the theme.

```css
#TOC {
    font-size: 13px;
    color: #3d4846;
    border-right: 2px solid #3ba5ae;
    padding-right: 12px;
}

#TOC a {
    color: #3d4846;
    text-decoration: none;
}

#TOC a:hover {
    color: #3ba5ae;
    text-decoration: none;
}

#TOC a.active {
    color: #3ba5ae;
    font-weight: 600;
}
```

---
<br>

## Code Blocks

*R Markdown* ✅ *Quarto* ✅

Styles inline code and code block backgrounds.

```css
/* Inline code */
code {
    background-color: #f4f4f4;
    color: #202c2d;
    padding: 2px 5px;
    border-radius: 3px;
    font-size: 13px;
}

/* Code blocks */
pre {
    background-color: #202c2d;
    color: #33C7BA;
    padding: 15px;
    border-radius: 5px;
    border-left: 3px solid #3ba5ae;
    font-size: 13px;
    overflow-x: auto;
}

pre code {
    background-color: transparent;
    color: inherit;
    padding: 0;
}
```

> [!TIP]
> `overflow-x: auto` adds a horizontal scrollbar to wide code blocks instead of breaking the layout.

---
<br>

## Tables

*R Markdown* ✅ *Quarto* ✅

Overrides default table styling for consistency across reports.

```css
table {
    border-collapse: collapse;
    width: 100%;
    font-size: 13px;
    margin: 20px 0;
}

th {
    background-color: #3ba5ae;
    color: white;
    font-weight: 600;
    padding: 10px 12px;
    text-align: left;
}

td {
    padding: 8px 12px;
    border-bottom: 1px solid #e0e0e0;
    color: #040708;
}

tr:hover {
    background-color: #f0f8f9;
}

tr:nth-child(even) {
    background-color: #f7f7f7;
}
```

| Property | What it does |
|---|---|
| `border-collapse` | Removes spacing between cell borders |
| `nth-child(even)` | Alternating row shading for readability |
| `tr:hover` | Subtle highlight on row hover |

---
<br>

## Callout Boxes

*R Markdown* ✅ *Quarto* ✅

Custom styled boxes for highlighting content in your reports. Define the class in `style.css` and apply it anywhere in your document with `<div class="box-name">`. You can create as many custom box styles as you need — name them anything and customise colours freely.

```css
/* Summary box — key takeaways and section summaries */
.summary-box {
    background-color: #e8f4f5;
    border-left: 3px solid #3ba5ae;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

/* Warning box — caveats and data quality issues */
.warning-box {
    background-color: #F7CCD6;
    border-left: 3px solid #E66684;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

/* Info box — supporting information and context */
.info-box {
    background-color: #d1ecf1;
    border-left: 3px solid #0c5460;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

/* Highlight box — important findings and executive callouts */
.highlight-box {
    background-color: #202c2d;
    border-left: 3px solid #33C7BA;
    color: white;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}
```

**Usage:**

```html
<div class="summary-box">
  Key takeaway or section summary here.
</div>

<div class="warning-box">
  Warning or caveat here.
</div>

<div class="info-box">
  Supporting information or context here.
</div>

<div class="highlight-box">
  Important result or finding here.
</div>
```

| Class | Use for |
|---|---|
| `.summary-box` | Key takeaways, section summaries |
| `.warning-box` | Warnings, caveats, data quality issues |
| `.info-box` | Supporting context, methodology notes |
| `.highlight-box` | Important findings, executive callouts |

---
<br>

## Metric Cards

*R Markdown* ✅ *Quarto* ✅

Metric cards display a prominent value with a descriptive label beneath it — ideal for KPIs, summary statistics, and executive overviews. Unlike BAN tables which use `kableExtra`, metric cards are pure HTML and CSS, giving you full control over layout, sizing, and positioning.

### CSS Definition

```css
/* Card container */
.metric-card {
    background-color: #ffffff;
    border: 1px solid #3ba5ae;
    border-top: 3px solid #3ba5ae;
    border-radius: 6px;
    padding: 16px 20px;
    text-align: center;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
    /* ✅ Set a fixed width or leave out to size automatically */
    width: 200px;
}

/* The large prominent value */
.metric-value {
    font-family: 'Montserrat', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: #3ba5ae;
    margin-bottom: 6px;
}

/* The descriptive label beneath the value */
.metric-label {
    font-size: 12px;
    color: #727970;
    line-height: 1.4;
}
```

### Layout Options

Use the `.metric-grid` wrapper to control how cards are arranged. Set `grid-template-columns` to define the number of columns.

```css
/* Grid wrapper — controls card layout */
.metric-grid {
    display: grid;
    gap: 16px;
    margin: 20px 0;
    justify-items: center;
    /* ✅ Adjust the number of columns below */
    grid-template-columns: repeat(3, 200px); /* 3 equal columns */
}
```

**Common column configurations:**

| Columns | CSS value |
|---|---|
| 2 equal columns | `repeat(2, 200px)` |
| 3 equal columns | `repeat(3, 200px)` |
| 4 equal columns | `repeat(4, 200px)` |
| Auto-fill to fit width | `repeat(auto-fill, minmax(180px, 1fr))` |

### Positioning

| Alignment | How to achieve it |
|---|---|
| Centre aligned | Add `justify-content: center` to `.metric-grid` |
| Left aligned | Add `justify-content: start` to `.metric-grid` |
| Full width evenly spaced | Add `justify-content: space-around` to `.metric-grid` |

### Usage

```html
<!-- ✅ Wrap all cards in a metric-grid div to control layout -->
<div class="metric-grid">

  <div class="metric-card">
    <div class="metric-value">94.2%</div>
    <div class="metric-label">Your metric label here</div>
  </div>

  <div class="metric-card">
    <div class="metric-value">1,284</div>
    <div class="metric-label">Your metric label here</div>
  </div>

  <div class="metric-card">
    <div class="metric-value">$42.6K</div>
    <div class="metric-label">Your metric label here</div>
  </div>

</div>
```

> [!TIP]
> To override the value colour for a specific card — for example to show a result in green or red — add an inline style to that card's `.metric-value` div:
> ```html
> <div class="metric-value" style="color: #2ca02c;">94.2%</div>
> ```

> [!NOTE]
> For R Markdown reports, replace placeholder values with inline R expressions:
> ```html
> <div class="metric-value">`r round(your_value, 1)`%</div>
> ```

---
<br>

## Toggle Button Styling

*R Markdown* ✅ *Quarto* ✅

The visual styling for toggle buttons. The JavaScript logic that controls show/hide behaviour lives in the [R Markdown Quick Reference Guide](RMD_Quick_Reference_Guide.md) — only appearance is controlled here.

```css
.toggleButton {
    background-color: #3ba5ae;
    color: white;
    border: 1px solid #202c2d;
    padding: 8px 16px;
    font-size: 14px;
    font-family: 'Montserrat', sans-serif;
    cursor: pointer;
    border-radius: 5px;
    letter-spacing: 0.5px;
    transition: background-color 0.2s ease;
}

.toggleButton:hover {
    background-color: #33C7BA;
    color: #040708;
}
```

| Property | What it does |
|---|---|
| `transition` | Smooth colour change on hover instead of an instant jump |
| `letter-spacing` | Slight spacing for a polished button label |
| `cursor: pointer` | Shows a hand cursor to confirm it's clickable |

---
<br>

## Section Dividers

*R Markdown* ✅ *Quarto* ✅

Styles the `---` horizontal rule used between sections.

```css
hr {
    border: none;
    border-top: 1px solid #3ba5ae;
    margin: 30px 0;
}
```

---
<br>

## Utility Classes

*R Markdown* ✅ *Quarto* ✅

Reusable helper classes for common layout and text needs.

```css
/* Centre-align content */
.centre {
    text-align: center;
}

/* Muted secondary text */
.text-muted {
    color: #727970;
    font-size: 12px;
}

/* Vertical breathing room */
.spacer {
    margin-top: 30px;
}

/* Flex row — display items side by side */
.flex-row {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 10px;
}
```

**Usage:**

```html
<p class="text-muted">Data source: ABS, 2024</p>

<div class="spacer"></div>

<div class="flex-row">
  <!-- Cards or BAN tables sit side by side here -->
</div>
```

---
<br>

## Complete style.css File

Copy this into a file named `style.css` and place it in the same folder as your `.Rmd` or Quarto file.

```css
/* ── Google Fonts ─────────────────────────────────────────────────────────── */
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap');

/* ── Colour Palette ───────────────────────────────────────────────────────── */
/*
    #040708  — Primary text, deep backgrounds
    #202c2d  — Dark section backgrounds
    #3d4846  — Secondary backgrounds, borders
    #727970  — Muted text, subtle borders
    #3ba5ae  — Primary accent
    #33C7BA  — Secondary accent, hover states
*/

/* ── Body & Layout ────────────────────────────────────────────────────────── */
body {
    font-family: Arial, sans-serif;
    font-size: 12px;
    color: #000000;
    background-color: #ffffff;
    line-height: 1.6;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* ── Typography ───────────────────────────────────────────────────────────── */
p {
    margin: 0 0 12px 0;
    color: #000000;
}

strong {
    color: #202c2d;
}

em {
    color: #3d4846;
}

/* ── Headings ─────────────────────────────────────────────────────────────── */
h1 {
    font-family: 'Montserrat', sans-serif;
    font-size: 24px;
    font-weight: 700;
    color: #3ba5ae;
    border-bottom: 2px solid #3ba5ae;
    padding-bottom: 8px;
    margin-top: 40px;
    margin-bottom: 16px;
    letter-spacing: 1px;
}

h2 {
    font-family: 'Montserrat', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: #202c2d;
    border-bottom: 1px solid #3d4846;
    padding-bottom: 6px;
    margin-top: 32px;
    margin-bottom: 12px;
}

h3 {
    font-family: 'Montserrat', sans-serif;
    font-size: 16px;
    font-weight: 600;
    color: #3d4846;
    margin-top: 24px;
    margin-bottom: 8px;
}

h4 {
    font-family: 'Montserrat', sans-serif;
    font-size: 14px;
    font-weight: 600;
    color: #727970;
    margin-top: 16px;
    margin-bottom: 6px;
}

/* ── Hyperlinks ───────────────────────────────────────────────────────────── */
a {
    color: #3ba5ae;
    text-decoration: none;
}

a:hover {
    color: #33C7BA;
    text-decoration: underline;
}

/* ── Table of Contents (R Markdown only) ─────────────────────────────────── */
#TOC {
    font-size: 13px;
    color: #3d4846;
    border-right: 2px solid #3ba5ae;
    padding-right: 12px;
}

#TOC a {
    color: #3d4846;
    text-decoration: none;
}

#TOC a:hover {
    color: #3ba5ae;
    text-decoration: none;
}

#TOC a.active {
    color: #3ba5ae;
    font-weight: 600;
}

/* ── Code ─────────────────────────────────────────────────────────────────── */
code {
    background-color: #f4f4f4;
    color: #202c2d;
    padding: 2px 5px;
    border-radius: 3px;
    font-size: 13px;
}

pre {
    background-color: #202c2d;
    color: #33C7BA;
    padding: 15px;
    border-radius: 5px;
    border-left: 3px solid #3ba5ae;
    font-size: 13px;
    overflow-x: auto;
}

pre code {
    background-color: transparent;
    color: inherit;
    padding: 0;
}

/* ── Tables ───────────────────────────────────────────────────────────────── */
table {
    border-collapse: collapse;
    width: 100%;
    font-size: 13px;
    margin: 20px 0;
}

th {
    background-color: #3ba5ae;
    color: white;
    font-weight: 600;
    padding: 10px 12px;
    text-align: left;
}

td {
    padding: 8px 12px;
    border-bottom: 1px solid #e0e0e0;
    color: #040708;
}

tr:hover {
    background-color: #f0f8f9;
}

tr:nth-child(even) {
    background-color: #f7f7f7;
}

/* ── Callout Boxes ────────────────────────────────────────────────────────── */
.summary-box {
    background-color: #e8f4f5;
    border-left: 3px solid #3ba5ae;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

.warning-box {
    background-color: #F7CCD6;
    border-left: 3px solid #E66684;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

.info-box {
    background-color: #d1ecf1;
    border-left: 3px solid #0c5460;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

.highlight-box {
    background-color: #202c2d;
    border-left: 3px solid #33C7BA;
    color: white;
    padding: 15px;
    margin: 20px 0;
    border-radius: 4px;
}

/* ── Metric Cards ─────────────────────────────────────────────────────────── */
.metric-card {
    background-color: #ffffff;
    border: 1px solid #3ba5ae;
    border-top: 3px solid #3ba5ae;
    border-radius: 6px;
    padding: 16px 20px;
    text-align: center;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
    width: 200px;
}

.metric-value {
    font-family: 'Montserrat', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: #3ba5ae;
    margin-bottom: 6px;
}

.metric-label {
    font-size: 12px;
    color: #727970;
    line-height: 1.4;
}

.metric-grid {
    display: grid;
    gap: 16px;
    margin: 20px 0;
    justify-items: center;
    justify-content: center;
    grid-template-columns: repeat(3, 200px);
}

/* ── Toggle Buttons ───────────────────────────────────────────────────────── */
.toggleButton {
    background-color: #3ba5ae;
    color: white;
    border: 1px solid #202c2d;
    padding: 8px 16px;
    font-size: 14px;
    font-family: 'Montserrat', sans-serif;
    cursor: pointer;
    border-radius: 5px;
    letter-spacing: 0.5px;
    transition: background-color 0.2s ease;
}

.toggleButton:hover {
    background-color: #33C7BA;
    color: #040708;
}

/* ── Section Dividers ─────────────────────────────────────────────────────── */
hr {
    border: none;
    border-top: 1px solid #3ba5ae;
    margin: 30px 0;
}

/* ── Utility Classes ──────────────────────────────────────────────────────── */
.centre {
    text-align: center;
}

.text-muted {
    color: #727970;
    font-size: 12px;
}

.spacer {
    margin-top: 30px;
}

.flex-row {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 10px;
}
```

---
<br>

*← [R Markdown Quick Reference](RMD_Quick_Reference_Guide.md) · [README](../README.md)*