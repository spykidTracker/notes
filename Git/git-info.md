# Install Git & Push First Project to GitHub

## Install Git
Download and install Git:
https://git-scm.com/install/

---

## Check Installation

Open Terminal / CMD and run:

```bash
git --version
```

---

## Configure Git

Set your username and email:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@gmail.com"
```

Check saved config:

```bash
git config --list
```

---

## Create GitHub Account & Repository

1. Click **New Repository**
2. Give repository name
3. Keep **Public** (or Private)
4. Click **Create Repository**

---

## Create Local Project Folder

Initialize Git in your project folder:

```bash
git init
```

---

## Connect Local Git to GitHub Repository

```bash
git remote add origin https://github.com/username/myproject.git
```

Check connection:

```bash
git remote -v
```

---

## Add Files to Git

Create any file (example: `index.html`)

Check file status:

```bash
git status
```

Add files to staging:

```bash
git add .
```

---

## Commit Files

```bash
git commit -m "First commit"
```

---

## Push Code to GitHub

```bash
git branch -M main
git push -u origin main
```

Done!  
Refresh GitHub → your code is there.

---

## Daily Workflow

Whenever you change code:

```bash
git add .
git commit -m "describe changes"
git push
```

---

## Quick Summary (Memory Trick)

```bash
git init
git add .
git commit -m "message"
git remote add origin URL
git push -u origin main
```