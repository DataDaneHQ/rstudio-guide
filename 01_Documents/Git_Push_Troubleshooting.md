<img src="../Resources/Git_Push_Troubleshooting_Banner.png" alt="Git Push Troubleshooting" width="100%">

<br>

## Overview

This guide explains how to fix the `failed to push some refs` error when pushing to GitHub from RStudio or the terminal.

> [!IMPORTANT]
> If you see the following error when running `git push origin main`:
>
> `error: failed to push some refs to 'https://github.com/USERNAME/REPONAME.git'`
>
> `hint: Updates were rejected because the remote contains work that you do not have locally`
>
> Follow the steps below to resolve it.

---

<br>

## Why Does This Happen?

The remote repository on GitHub contains changes that your local copy doesn't have yet — either someone else pushed an update, or you made changes on another machine. Git requires you to sync those changes before it will accept your push.

---

<br>

## Solution

### 1. Save Your Work Locally

Make sure all current changes are added and committed:
```bash
git add .
git commit -m "Save current work"
```
<br>

### 2. Pull the Latest Changes from GitHub

Download any updates from the remote repository:
```bash
git pull origin main
```
<br>

### 3. Resolve Conflicts (if any)

If Git reports conflicts after pulling:

1. Open each file listed as conflicted
2. Review the changes and decide what to keep
3. Save the file, then commit the resolution:
```bash
git add .
git commit -m "Resolve merge conflicts"
```
<br>

### 4. Push Your Changes

Once everything is merged and committed, push again:
```bash
git push origin main
```

---

<br>

## Still Getting Errors?

| Issue | Fix |
|---|---|
| Not sure which branch you're on | Run `git status` — your current branch is shown at the top |
| Branch shows as ahead/behind | Repeat the pull → resolve → push steps above |
| Conflicts you're not sure how to resolve | See GitHub's guide on [resolving merge conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line) |

---

<br>

*← [Linking GitHub to RStudio](Linking_GitHub_to_RStudio.md) · [README](../README.md)*