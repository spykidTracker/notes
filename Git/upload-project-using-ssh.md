# Set Up SSH for Local Machine & Push Project (Complete Guide)

This guide explains how to connect your **local project** to **GitHub using SSH** and upload your project for the first time.

This is the **most important Git workflow** every developer uses daily.

---

# Before Starting (Important Concept)

Git works in 3 places:

| Area | Meaning |
|---|---|
| Working Directory | Your project files |
| Local Repository | Git history on your computer |
| Remote Repository | GitHub repository |

Goal of this guide:
Connect Local Repository → Remote Repository using **SSH**.

---

# Step 1 — Go to Your Project Folder

Open **Git Bash** and move to your project directory.

Example:
```bash
cd my-project
```

If your project is somewhere else, use full path:

Example:
```bash
cd D:/Projects/my-project
```

You must be inside your project folder before running Git commands.

---

# Step 2 — Check Current Connection Type

Run:
```bash
git remote -v
```

### Case 1 — If you see HTTPS URLs

```
origin  https://github.com/username/repo.git (fetch)
origin  https://github.com/username/repo.git (push)
```

This means your repo is using **HTTPS**.

We will replace it with **SSH**.

---

### Case 2 — If you see error

```
fatal: not a git repository (or any of the parent directories): .git
```

This means your project is **not initialized with Git yet**.

Fix it by running:
```bash
git init
```

What this does:
- Creates hidden `.git` folder
- Turns your project into a Git repository
- Enables version control

Without this step, Git cannot track files.

---

# Step 3 — Copy SSH URL from GitHub

Go to your repository on GitHub.

Steps:
1. Open repository in browser
2. Click green **Code** button
3. Select **SSH**
4. Copy URL like:

```
git@github.com:username/repo.git
```

This is the secure SSH connection URL.

---

# Step 4 — Create Remote Connection

Run:
```bash
git remote add origin git@github.com:username/repo.git
```

### What does this command mean?

| Part | Meaning |
|---|---|
| remote | External repository |
| add | Create connection |
| origin | Nickname of GitHub repo |
| URL | GitHub repository address |

Think of **origin** as shortcut name for GitHub.

You can name it anything, but **origin is industry standard**.

---

# Verify Remote Connection

Run:
```bash
git remote -v
```

You should see:
```
origin  git@github.com:username/repo.git (fetch)
origin  git@github.com:username/repo.git (push)
```

Your local repo is now connected to GitHub using SSH 🎉

---

# Step 5 — Add All Project Files

Run:
```bash
git add .
```

### What happens here?

Git moves files from:
Working Directory → Staging Area

You are telling Git:
"Prepare these files for the next snapshot (commit)"

---

# Step 6 — Create First Commit

Run:
```bash
git commit -m "Initial commit"
```

### What is a commit?

A commit is:
- A snapshot of your project
- Saved version of your code
- A checkpoint in history

---

# Step 7 — Set Main Branch

Run:
```bash
git branch -M main
```

### Why this step?

Older Git versions use branch name **master**.  
Modern Git uses **main**.

This command renames current branch → main.

---

# Step 8 — Upload Project to GitHub (First Push)

Run:
```bash
git push -u origin main
```

### What happens here?

Your code moves:
Local Repository → GitHub Repository

`-u` sets **origin/main as default upstream**.

Meaning:
Next time you can simply run:
```bash
git push
```

---

# Step 9 — Future Updates Workflow

After first push, daily workflow becomes simple:

```bash
git add .
git commit -m "Your commit message"
git push
```

This updates GitHub with latest changes.

---

# What Just Happened (Big Picture)

You have successfully:
- Initialized Git repository
- Connected GitHub via SSH
- Created first commit
- Uploaded project to cloud
- Set up daily workflow

You are now using Git like a real developer 🚀