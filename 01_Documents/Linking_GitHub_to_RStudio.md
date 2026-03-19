<img src="../Resources/linking_your_repo_banner.png" alt="Linking Your GitHub Repo to RStudio" width="100%">

<br>

## Overview

This guide walks you through linking a GitHub repository to RStudio so you can work with it locally using version control. It covers three scenarios — cloning your own repo, forking someone else's, and downloading files without version control.

> [!IMPORTANT]
> If the repository is private, you must be added as a collaborator before you can clone it. If you receive an authentication error, contact the repository owner to request access.

---

<br>

## Cloning Your Own Repository

Use this workflow after creating a new repo on GitHub and you're ready to start working in RStudio.

### 1. Get Your Repository URL

1. Go to your repository page on GitHub
2. Click the green **Code** button
3. Ensure **HTTPS** is selected (not SSH)
4. Click the copy icon to copy the URL — it will look like:
   `https://github.com/YOUR-USERNAME/repo-name.git`

<img src="../Resources/screenshot_5.png" alt="GitHub Code button showing HTTPS URL and copy icon" width="700">

<br>

### 2. Link to RStudio

1. Open RStudio
2. Go to **File → New Project → Version Control → Git**
3. Paste your URL into the **Repository URL** field
4. Choose where to save the project on your computer (e.g. Documents)
5. Click **Create Project**
6. RStudio will download the repository and open it as a project automatically

> 📸 *Screenshot here — show the Version Control → Git dialog in RStudio with the URL field.*
<br>

### 3. Pull Updates

Once your project is set up, use Pull to keep your local copy in sync with GitHub.

1. Open the project in RStudio
2. Locate the **Git tab** in the top-right pane (next to Environment)
3. Click the blue **Pull** button (down arrow icon)

<img src="../Resources/Git_Pane_Image.png" alt="Git pane in RStudio showing Pull button" width="600">

---
<br>

## Forking Someone Else's Repository

Use this workflow when you want to work with a repo you don't own — forking creates your own copy under your GitHub account.

### 1. Fork the Repository

1. Go to the GitHub repository page you want to work with
2. Click the **Fork** button in the top-right corner
3. GitHub will create a copy under your account
4. You'll be redirected to your forked repository — the URL will show your username

> 📸 *Screenshot here — show the Fork button location on a GitHub repo page.*
<br>

### 2. Get Your Fork's URL

1. On your forked repository page, click the green **Code** button
2. Ensure **HTTPS** is selected (not SSH)
3. Click the copy icon to copy the URL — it will look like:
   `https://github.com/YOUR-USERNAME/repo-name.git`

<img src="../Resources/Fork_Repo.png" alt="Forked repository showing Code button and HTTPS URL" width="700">
<br>

### 3. Link to RStudio

Follow the same steps as cloning your own repo:

1. Open RStudio
2. Go to **File → New Project → Version Control → Git**
3. Paste your fork's URL into the **Repository URL** field
4. Choose where to save the project on your computer
5. Click **Create Project**

---
<br>

## Just Want to View the Files?

If you don't need version control and just want a local copy of the files, skip the steps above:

Click the green **Code** button on the repository page → **Download ZIP**

---
<br>

## Troubleshooting

| Issue | Fix |
|---|---|
| Git tab not visible in RStudio | Tools → Project Options → Git/SVN → set Version Control to **Git** |
| Authentication error when cloning | Confirm you've been added as a collaborator by the repo owner |
| Push or pull errors | See [Git Push Troubleshooting](01-Get_Push_Troubleshooting.md) |
| Incorrect IP address error | See [Incorrect IP Address](02-Incorrect_IP_Address.md) |

---
<br>

*← [Creating a GitHub Repository](Creating_A_Repo.md) · [README](../README.md)*