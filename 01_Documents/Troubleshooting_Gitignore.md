<img src="../00_Resources/gitignore_banner.png" alt="Gitignore Tips" width="100%">

<br>

## Overview

A `.gitignore` file tells Git which files and folders to leave untracked — meaning they exist on your computer but are never committed to GitHub. This is useful for keeping sensitive data, large files, and clutter out of your repository.

> [!NOTE]
> When you initialise a new repo on GitHub with the **R** template selected, a standard `.gitignore` is created automatically. You can then customise it for your project.

---

<br>

## Where Does .gitignore Live?

The `.gitignore` file sits in the **root of your repository** — the same level as your `.Rproj` file. It applies to everything in the repo from that level down.

---

<br>

## Standard R Entries

The following are added automatically when you select the **R** template during repo creation:
```bash
.Rproj.user
.Rhistory
.RData
.Ruserdata
```

### Recommended Additions

These aren't included by default but are worth adding for most R projects:
```bash
# R Markdown output folders generated when knitting documents
*_cache/
*_files/

# R package build artefacts (relevant if developing R packages)
*.tar.gz
*.rdb
*.rdx
```

---

<br>

## Ignoring Specific Files and Folders
```bash
# Ignore a specific file in the same folder as .gitignore
file.html

# Ignore a specific file in a subfolder
folder_name/file.html

# Ignore an entire folder
folder_name/

# Ignore an entire folder but keep specific files
folder_name/*
!folder_name/keep_this.txt
!folder_name/keep_that.R

# Ignore a file type everywhere in the repo
*.csv
*.xlsx
```

---

<br>

## Including Files from an Ignored Folder

Use `!` to un-ignore specific files inside an otherwise ignored folder:
```bash
# Ignore the folder contents but not the folder itself
folder_name/*

# But include these specific files
!folder_name/file1.txt
!folder_name/file2.R
!folder_name/subfolder/important.csv
```

> [!IMPORTANT]
> Use `folder_name/*` rather than `folder_name/` when you need exceptions. Ignoring the folder itself with `folder_name/` blocks all exceptions — Git won't look inside an ignored folder at all.

---

<br>

## Already Tracking a File by Mistake?

Adding a file to `.gitignore` won't stop Git tracking it if it was already committed. You need to remove it from tracking first:
```bash
git rm --cached filename.csv
```

For an entire folder:
```bash
git rm --cached -r folder_name/
```

Then commit the change:
```bash
git add .
git commit -m "Remove tracked files now covered by gitignore"
```

> [!WARNING]
> `git rm --cached` removes the file from Git tracking only — it does **not** delete it from your computer.

---

<br>

## Quick Reference

| Pattern | What it does |
|---|---|
| `file.html` | Ignores a specific file |
| `folder_name/` | Ignores an entire folder |
| `folder_name/*` | Ignores folder contents but keeps structure |
| `!folder_name/file.txt` | Un-ignores a specific file |
| `*.csv` | Ignores all files of that type |
| `git rm --cached file` | Stops tracking an already committed file |

---

<br>

## Further Reading

- [GitHub's gitignore documentation](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
- [gitignore.io](https://www.toptal.com/developers/gitignore) — generate `.gitignore` templates for any language or tool

---

<br>

*← [Incorrect IP Address](02-Incorrect_IP_Address.md) · [README](../README.md)*