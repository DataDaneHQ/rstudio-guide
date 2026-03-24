![Guide_Title_Banner](00_Resources/readme_title_banner.png)

<br>

A practical, beginner-friendly guide to version control in RStudio — covering everything from creating your first repository to writing polished R Markdown reports.

Built originally as internal team documentation, this guide is designed to get analysts and data scientists productive with Git and GitHub as quickly as possible.

---

<br>

## What's Covered

| Section | Description |
|---|---|
| [Creating a GitHub Repository](01_Documents/Creating_a_Repo.md) | Set up and configure a new repo from scratch |
| [Linking GitHub to RStudio](01_Documents/Linking_GitHub_to_RStudio.md) | Connect a repo to an RStudio Project for version control |
| [Markdown Quick Reference](01_Documents/Markdown_Quick_Reference_Guide.md) | Essential Markdown syntax for documentation |
| [R Markdown Template](02_Scripts/report_template.Rmd) | A ready-to-use `.Rmd` template for reports |
| [Troubleshooting](#troubleshooting) | Common errors and how to fix them |

---

<br>

## Getting Started

If you're new to Git and RStudio, start here:

1. [Create a GitHub repository](01_Documents/Creating_a_Repo.md)
2. [Link it to an RStudio Project](01_Documents/Linking_GitHub_to_RStudio.md)
3. Make your first commit, push, and pull

The guide assumes basic familiarity with R and RStudio but no prior Git experience.

---

<br>

## Troubleshooting

| Issue | Guide |
|---|---|
| Git push errors | [01 — Git Push Troubleshooting](01_Documents/Troubleshooting_Git_Push.md) |
| Incorrect IP address error | [02 — Incorrect IP Address](01_Documents/Troubleshooting_Incorrect_IP_Address.md) |
| `.gitignore` tips | [03 — Gitignore Tips](01_Documents/03-Gitignore_Tips.md) |
| Accessing linked documents | [04 — Accessing Documents](01_Documents/04-Accessing_Documents.md) |
| Git tab not visible in RStudio | Tools → Project Options → Git/SVN → set Version Control to **Git** |

---

<br>

## Repository Structure
```
GitHub-RStudio-Starter-Guide/
├── Documents/
│   ├── Creating_A_Repo.md
│   ├── Accessing_A_Repo.md
│   ├── Quick_Reference_Guide.md
│   ├── 01-Get_Push_Troubleshooting.md
│   ├── 02-Incorrect_IP_Address.md
│   ├── 03-Gitignore_Tips.md
│   └── 04-Accessing_Documents.md
├── Scripts/
│   └── report_template.Rmd
├── Resources/
│   └── readme_title_banner.png
└── README.md
```

---

<br>

*Created by [DataDaneHQ](https://github.com/DataDaneHQ)*