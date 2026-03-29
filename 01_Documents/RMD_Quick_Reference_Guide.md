<img src="../00_Resources/rmd_guide_banner.png" alt="R Markdown Quick Reference Guide" width="100%">

<br>

## Overview

A practical reference guide for building HTML reports in R Markdown. Covers the elements used most commonly in real analysis work — from YAML setup and data loading through to tables, BANs, and toggle buttons.

For basic formatting (headers, bold, italic, lists, etc.) refer to the [Markdown Quick Reference Guide](Quick_Reference_Guide.md).

> [!NOTE]
> This is a living document — new sections will be added over time as the guide expands.

---

<br>

## Contents

<table align="center">
<tr>
<td width="550">

- [Creating an HTML R Markdown File](#creating-an-html-r-markdown-file)
- [YAML Header](#yaml-header)
- [Title Banner](#title-banner)
- [Load Libraries & Set Global Options](#load-libraries--set-global-options)
- [Load Data](#load-data)
- [Comments](#comments)

</td>
<td width="550">

- [Tabsets](#tabsets)
- [Toggle Buttons](#toggle-buttons)
- [BAN Tables](#ban-tables)
- [Summary Tables](#summary-tables)

</td>
</tr>
</table>

---

<br>

## Creating an HTML R Markdown File

1. Open RStudio
2. Go to **File → New File → R Markdown**
3. Enter a title (this can be removed later — see [Title Banner](#title-banner))
4. Select **HTML** as the output format
5. Click **OK**
6. Save the file with an `.Rmd` extension

> [!TIP]
> Delete the boilerplate content below the YAML header before starting — RStudio fills new `.Rmd` files with example code you won't need.

---

<br>

## YAML Header

The YAML header sits at the very top of your `.Rmd` file between `---` markers. It controls document output, styling, and table of contents behaviour.
````yaml
---
output: 
  html_document:
    css: style.css
    toc: true
    toc_depth: 4
    toc_float: true
encoding: UTF-8
---
````

**Key settings:**

| Setting | What it does |
|---|---|
| `css: style.css` | Links a custom CSS file for styling — place `style.css` in the same folder as your `.Rmd` |
| `toc: true` | Adds a table of contents |
| `toc_depth: 4` | Includes headers down to `####` level in the TOC |
| `toc_float: true` | Keeps the TOC visible as a floating sidebar while scrolling |
| `encoding: UTF-8` | Ensures special characters render correctly |

> [!NOTE]
> - The YAML header does not include `title:` or `author:` fields — these are replaced by a custom title banner. See [Title Banner](#title-banner) below.  
> - For guidance on writing and customising your `style.css` file, see the [CSS Styling Guide](02_CSS_Styling_Guide.md).

---

<br>

## Title Banner

Instead of the standard YAML title and author fields, use a custom HTML banner that combines a background image, main title, and subtitle. Place this directly below the YAML header.
````html
<!-- ✅ Main Banner Image | Replace 'data:image/png;base64,YOUR_BASE64_STRING_HERE' with your image path-->
<div style="width: 100%;
            background-image: url('data:image/png;base64,YOUR_BASE64_STRING_HERE'); 
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            padding: 80px 10px;
            color: white;
            font-family: Arial, sans-serif;
            text-align: left;">
<!-- ✅ Change the text below to adjust the main title -->
  <div style="font-size: 32px; font-weight: bold; margin: 0;">Enter Main Title Here</div>
<!-- ✅ Change the text below to adjust the subtitle -->
  <p style="margin: 0; color: white !important;">Enter Sub-title Here</p>
</div>
````

> [!TIP]
> - Update the three lines marked ✅ for each new report. Everything else can stay as is.  
> - Convert your banner image to base64 at [base64-image.de](https://www.base64-image.de) — drag and drop your image, copy the base64 string, and replace `data:image/png;base64,YOUR_BASE64_STRING_HERE` with the result. This embeds the image directly in the report so it displays correctly regardless of file paths.

---

<br>

## Load Libraries & Set Global Options

Place this as the first code chunk in your document. Add or remove libraries based on your report's requirements — the example below reflects a typical setup for data analysis and HTML report generation. Global options apply to every chunk in the report.
````r
{r setup, include=FALSE}
# ──────────────────────────────────────────────────────────────────────────────
# 1️⃣ Load Libraries
# ──────────────────────────────────────────────────────────────────────────────
library(arrow)        # Read and write Feather files
library(dplyr)        # Data manipulation and transformation
library(DT)           # Interactive browsable tables
library(here)         # Path management
library(htmltools)    # Build HTML elements for outputs
library(kableExtra)   # Enhance and style knitr tables
library(knitr)        # Render tables and support report generation
library(lubridate)    # Date and time manipulation
library(purrr)        # Functional programming tools (map, walk, etc.)
library(plotly)       # Interactive web-based data visualisation
library(scales)       # Format numbers, percentages, and axis labels
library(tidyverse)    # Core packages for data manipulation and visualisation


# ──────────────────────────────────────────────────────────────────────────────
# 2️⃣ Global Code Chunk Options
# ──────────────────────────────────────────────────────────────────────────────
knitr::opts_chunk$set(
  echo       = FALSE,   # Hide code from output
  warning    = FALSE,   # Suppress warnings
  message    = FALSE,   # Suppress messages
  fig.width  = 10,      # Default figure width
  fig.height = 5        # Default figure height
)
````

**`include=FALSE`** — runs the chunk but keeps it completely out of the rendered output. Use this for setup chunks you never want visible.

---

<br>

## Load Data

Place this immediately after the setup chunk. Supports Feather, CSV, and Excel formats.
````r
{r load_data, include=FALSE}
# Import Feather file
data <- read_feather(here("file_path", "file_name.feather"))

# Import CSV file
data <- read_csv(here("file_path", "file_name.csv"))

# Import Excel file
data <- read_excel(here("file_path", "file_name.xlsx"), sheet = "Sheet1")
# Remove sheet = argument if not required
````

> [!TIP]
> Use `here()` for all file paths — it builds paths relative to your project root, which means your report will work on any machine without needing to update hardcoded paths.

---

<br>

## Comments

Use HTML comment syntax to add notes in your `.Rmd` file that won't appear in the rendered output. Useful for leaving instructions, reminders, or section markers.
````html
<!-- Your comment here -->
````

---

<br>

## Tabsets

Tabsets split content into clickable tabs under a heading. Add `{.tabset}` to any header to make its sub-headings into tabs.
````markdown
## My Section {.tabset}

### Tab One
Content for tab one.

### Tab Two
Content for tab two.

### Tab Three
Content for tab three.
````

> [!TIP]
> Tabsets are ideal for breaking up long sections — comparisons between groups, before/after views, or splitting data by category.

---

<br>

## Toggle Buttons

Toggle buttons show and hide content on click — useful for keeping reports clean while still making detail available on demand.

### Step 1 — Add the Script

Place this once in your document, directly below the title banner. It can be removed entirely if toggle buttons aren't needed.
````html
<!-- Toggle Button Script | Leave as is or remove if buttons not required -->
<script>
document.addEventListener("DOMContentLoaded", function() {
  document.querySelectorAll(".toggleButton").forEach(function(button) {
    let originalText = button.innerText;
    button.addEventListener("click", function() {
      var targetId = this.getAttribute("data-target");
      var content = document.getElementById(targetId);
      if (content) {
        content.style.display = (content.style.display === "none") ? "block" : "none";
        this.innerText = content.style.display === "none" ? originalText : "Hide " + originalText.substring(5);
      }
    });
  });
});
</script>

<!-- Toggle Button Styling | Adjust colours as needed -->
<style>
  .toggleButton {
    background-color: #a4bdcf;   /* Button colour */
    color: black;                /* Text colour */
    border: 1px solid #7890a0;   /* Border colour */
    padding: 8px 12px;           /* Inner spacing */
    font-size: 14px;             /* Text size */
    cursor: pointer;             /* Pointer cursor on hover */
    border-radius: 5px;          /* Rounded corners */
  }
  .toggleButton:hover {
    background-color: #90a9bc;   /* Hover colour */
  }
</style>
````

### Step 2 — Add a Button

For each toggle button, create a matching button and content block. The `data-target` and `id` values must match.
````html
<!-- Toggle Button -->
<div style="display: flex; justify-content: center; margin-bottom: 1em;">
  <button class="toggleButton" data-target="section_one" style="margin-right: 40px;">
    Show Button Contents <!-- ✅ Change button label here -->
  </button>
</div>

<!-- Content Block -->
<div id="section_one" class="codeContent" style="display:none;">
```{r button_content}
# ✅ Add content here
```
</div>
````

> [!IMPORTANT]
> Every button needs a unique `data-target` and matching `id`. If two buttons share the same value, clicking one will toggle both.

---

<br>

## BAN Tables

BAN (Big Ass Number) tables display key metrics as large, prominent figures — ideal for report summaries and executive overviews.

### Step 1 — Define the Function

Place this once in your document. The `header_color` argument accepts any hex colour.
````r
{r ban_function, include=FALSE}
# ──────────────────────────────────────────────────────────────────────────────
# Reusable function to create consistent BAN-style tables
# ──────────────────────────────────────────────────────────────────────────────
create_ban <- function(df, header_color = "#7BA0BE") {
  df %>%
    kbl(format = "html", align = "c", escape = FALSE, 
        format.args = list(big.mark = ",")) %>%
    kable_styling(
      full_width = FALSE,
      bootstrap_options = c("condensed", "bordered", "hover"),
      position = "center"
    ) %>%
    row_spec(0, bold = TRUE, font_size = 12, 
             background = header_color, color = "white") %>%
    row_spec(1, bold = TRUE, font_size = 18) %>%
    column_spec(1, width = "200px", 
                extra_css = "white-space: normal; text-align: center;")
}
````

### Step 2 — Calculate Your Values
````r
{r calculate_bans, include=FALSE}
# ✅ Replace with your own calculated values
metric_one <- nrow(your_dataframe)
metric_two <- sum(your_dataframe$your_column)
````

### Step 3 — Render the BANs
````r
{r render_bans, results='asis'}
cat('<div style="display: flex; justify-content: space-around; flex-wrap: wrap;">')
cat('<div style="margin: 3px;">', 
    as.character(create_ban(data.frame(
      "✅ Your Metric Label" = metric_one, check.names = FALSE))), 
    '</div>')
cat('<div style="margin: 3px;">', 
    as.character(create_ban(data.frame(
      "✅ Your Second Metric Label" = metric_two, check.names = FALSE))), 
    '</div>')
cat('</div>')
````

> [!TIP]
> Add as many BAN `<div>` blocks as needed. They wrap automatically on smaller screens thanks to `flex-wrap: wrap`.

---

<br>

## Summary Tables

A reusable function for styled, consistently formatted summary tables using `kableExtra`. Adjust column names, widths, and alignment to suit your data.

### Step 1 — Define the Function
````r
{r summary_table_function, include=FALSE}
create_summary_table <- function(df, header_color = "#7BA0BE") {
  df %>%
    kbl(
      format    = "html",
      align     = c("l", "l", "c", "c", "c", "c"),  # ✅ One value per column
      escape    = FALSE,
      col.names = c("Column One", "Column Two", "Column Three",
                    "Column Four", "Column Five", "Column Six") # ✅ Update column names
    ) %>%
    kable_styling(
      full_width        = TRUE,
      bootstrap_options = c("condensed", "bordered", "hover", "striped"),
      position          = "center",
      font_size         = 12
    ) %>%
    row_spec(0, bold = TRUE, background = header_color, color = "white") %>%
    column_spec(1, width = "300px") %>%  # ✅ Adjust column widths as needed
    column_spec(2, width = "120px") %>%
    column_spec(3, width = "80px") %>%
    column_spec(4, width = "80px") %>%
    column_spec(5, width = "80px") %>%
    column_spec(6, width = "120px")
}
````

### Step 2 — Render the Table
````r
{r render_table}
create_summary_table(your_dataframe) # ✅ Replace with your dataframe name
````

> [!TIP]
> **`row_spec()` common options**
> 
> `row_spec(row, ...)` — `0` targets the header row, `1` targets the first data row, etc.
> 
> | Argument | Example | What it does |
> |---|---|---|
> | `bold` | `bold = TRUE` | Makes text bold |
> | `italic` | `italic = TRUE` | Makes text italic |
> | `color` | `color = "white"` | Sets text colour |
> | `background` | `background = "#7BA0BE"` | Sets background colour |
> | `font_size` | `font_size = 14` | Sets font size in pts |
> | `align` | `align = "c"` | Overrides alignment for the row |
> | `extra_css` | `extra_css = "border-top: 2px solid black;"` | Applies custom CSS |

> [!TIP]
> **`column_spec()` common options**
>
> `column_spec(column, ...)` — column number is positional, starting at `1`.
>
> | Argument | Example | What it does |
> |---|---|---|
> | `width` | `width = "150px"` | Sets fixed column width |
> | `bold` | `bold = TRUE` | Makes all values in column bold |
> | `italic` | `italic = TRUE` | Makes all values in column italic |
> | `color` | `color = "grey"` | Sets text colour for the column |
> | `background` | `background = "#f5f5f5"` | Sets background colour for the column |
> | `border_left` | `border_left = TRUE` | Adds a left border to the column |
> | `border_right` | `border_right = TRUE` | Adds a right border to the column |
> | `extra_css` | `extra_css = "white-space: nowrap;"` | Applies custom CSS |

**Key arguments:**

| Argument | What it does |
|---|---|
| `align` | Sets column alignment — `"l"` left, `"c"` centre, `"r"` right |
| `col.names` | Overrides column names in the rendered output |
| `header_color` | Hex colour for the header row — defaults to `#7BA0BE` |
| `full_width = TRUE` | Table stretches to full page width |
| `striped` | Alternating row shading for readability |
---

<br>

*[README](../README.md)*