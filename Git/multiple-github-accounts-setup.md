# Complete Beginner-Friendly Guide  
# Using Multiple GitHub Accounts on One PC with SSH

---

# Table of Contents

1. Introduction
2. What Problem Does This Solve?
3. Understanding Git, GitHub, SSH, and Authentication
4. How Git Normally Works
5. Why Problems Happen with Multiple Accounts
6. Understanding Global vs Local Git Config
7. Understanding SSH Keys
8. Understanding Public and Private Keys
9. Complete Setup Process
10. Creating SSH Keys
11. Adding Keys to GitHub
12. Creating SSH Config File
13. Testing SSH Connections
14. Using Correct Repository URLs
15. Setting Git User Per Project
16. Common Mistakes
17. Troubleshooting
18. Recommended Workflow
19. Final Folder Structure
20. Conclusion

---

# 1. Introduction

Many developers use multiple GitHub accounts on the same computer.

Example:

- One account for practice
- One account for real projects
- One account for office/company work

If not configured properly:

- wrong account may push code
- wrong author name may appear
- authentication problems occur
- Git becomes confusing

This guide explains everything from scratch.

---

# 2. What Problem Does This Solve?

Suppose you have:

| Account Type | GitHub Username |
|---|---|
| Practice Account | Sora1 |
| Real Projects Account | Sora2 |

Now imagine:

- you create a real project
- but Git pushes it using practice account
- or commits show wrong author

This happens because Git and SSH are not configured separately.

---

# 3. Understanding Git, GitHub, SSH, and Authentication

Before setup, understand these terms.

---

# What is Git?

Git is a version control system.

It tracks:
- file changes
- project history
- commits

Git works locally on your PC.

---

# What is GitHub?

GitHub is an online platform that stores Git repositories.

It allows:
- backup
- collaboration
- remote repositories

---

# What is SSH?

SSH stands for:

```txt
Secure Shell
```

SSH allows secure communication between:
- your computer
- GitHub server

Without typing username/password every time.

---

# What is Authentication?

Authentication means:

```txt
"How GitHub verifies who you are"
```

GitHub can authenticate using:
- password/token
- SSH key

Professional developers usually use SSH.

---

# 4. How Git Normally Works

When you commit:

```bash
git commit -m "message"
```

Git checks:

```bash
git config user.name
git config user.email
```

This decides:

```txt
Author: Your Name
```

BUT this does NOT decide which GitHub account is used.

---

# 5. Why Problems Happen with Multiple Accounts

Suppose:

- your PC has only one SSH key
- that key belongs to practice account

Now even if you work on real project:

```bash
git push
```

GitHub may:
- reject push
- authenticate wrong account
- create confusion

---

# 6. Understanding Global vs Local Git Config

This is VERY important.

---

# Global Config

Command:

```bash
git config --global
```

Applies to:
- ALL repositories on your computer

Example:

```bash
git config --global user.name "Pradip"
```

Now every project uses this author name.

---

# Local Config

Command:

```bash
git config
```

(no `--global`)

Applies ONLY to current repository.

Example:

```bash
git config user.name "Sora1"
```

Only this project uses that name.

---

# Recommendation

For multiple accounts:

✅ avoid global username/email  
✅ use local config per project

---

# 7. Understanding SSH Keys

SSH uses TWO keys:

| Key Type | Purpose |
|---|---|
| Private Key | stays on your PC |
| Public Key | uploaded to GitHub |

---

# Analogy

Think like this:

| Real World | SSH |
|---|---|
| House Lock | Public Key |
| House Key | Private Key |

GitHub has lock.

Your PC has key.

If key matches lock:
✅ access granted

---

# 8. Understanding Public and Private Keys

When you create SSH key:

Git generates:

```txt
id_ed25519
id_ed25519.pub
```

---

# Private Key

Example:

```txt
id_ed25519
```

IMPORTANT:
- NEVER share
- stays secret

---

# Public Key

Example:

```txt
id_ed25519.pub
```

This is uploaded to GitHub.

Safe to share.

---

# 9. Complete Setup Process

We will:

1. Remove old setup
2. Create separate SSH keys
3. Configure SSH
4. Add keys to GitHub
5. Configure repositories properly

---

# 10. Remove Old Git Global Config (Optional)

Check global config:

```bash
git config --global --list
```

Remove old username/email:

```bash
git config --global --unset user.name
git config --global --unset user.email
```

---

# 11. Create `.ssh` Folder

Go to:

```txt
C:\Users\YOUR_USERNAME
```

Create folder:

```txt
.ssh
```

Final path:

```txt
C:\Users\YOUR_USERNAME\.ssh
```

---

# 12. Generate SSH Key for Practice Account

Open Git Bash.

Run:

```bash
ssh-keygen -t ed25519 -C "practice@gmail.com" -f ~/.ssh/id_ed25519_practice
```

---

# What This Command Means

| Part | Meaning |
|---|---|
| ssh-keygen | generate SSH key |
| -t ed25519 | modern encryption type |
| -C | comment/email |
| -f | filename |

---

# What Happens Next?

Git creates:

```txt
id_ed25519_practice
id_ed25519_practice.pub
```

inside:

```txt
C:\Users\YOUR_USERNAME\.ssh
```

---

# Passphrase Question

It asks:

```txt
Enter passphrase
```

You can:
- press Enter (simpler)
- or add password (more secure)

---

# 13. Generate SSH Key for Real Projects

Run:

```bash
ssh-keygen -t ed25519 -C "real@gmail.com" -f ~/.ssh/id_ed25519_project
```

Now you have TWO separate SSH keys.

---

# 14. Start SSH Agent

SSH agent manages keys in memory.

Run:

```bash
eval "$(ssh-agent -s)"
```

---

# Add Practice Key

```bash
ssh-add ~/.ssh/id_ed25519_practice
```

---

# Add Real Project Key

```bash
ssh-add ~/.ssh/id_ed25519_project
```

---

# 15. Create SSH Config File

Go to:

```txt
C:\Users\YOUR_USERNAME\.ssh
```

Create file:

```txt
config
```

NO extension.

NOT:
```txt
config.txt
```

---

# Add This Content

```config
# Practice Account
Host github-practice
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_practice

# Real Projects Account
Host github-project
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_project
```

---

# Understanding This Config

---

# Host

Example:

```txt
Host github-practice
```

This is custom shortcut name.

Later Git uses:

```bash
git@github-practice
```

instead of:

```bash
git@github.com
```

---

# IdentityFile

Specifies WHICH SSH key should be used.

This is the MOST IMPORTANT line.

---

# 16. Add Public Keys to GitHub

---

# Practice Account

Run:

```bash
cat ~/.ssh/id_ed25519_practice.pub
```

Copy output.

Go to GitHub:

- Settings
- SSH and GPG Keys
- New SSH Key
- Paste key

---

# Real Account

Run:

```bash
cat ~/.ssh/id_ed25519_project.pub
```

Add it to second account.

---

# 17. Test SSH Connections

---

# Practice Account

```bash
ssh -T git@github-practice
```

---

# Real Account

```bash
ssh -T git@github-project
```

---

# Expected Output

```txt
Hi USERNAME! You've successfully authenticated...
```

---

# 18. Clone Repository Properly

This is VERY important.

---

# Practice Repository

```bash
git clone git@github-practice:Sora1/repository.git
```

---

# Real Repository

```bash
git clone git@github-project:Sora2/repository.git
```

---

# 19. Set Local Git Author Per Repository

Go inside repository.

---

# Practice Repo

```bash
git config user.name "Sora1"
git config user.email "practice@gmail.com"
```

---

# Real Repo

```bash
git config user.name "Sora2"
git config user.email "real@gmail.com"
```

---

# Why This Is Needed?

SSH controls:
✅ authentication

Git config controls:
✅ commit author

These are DIFFERENT things.

---

# 20. Verify Settings

Check local config:

```bash
git config --list
```

---

# 21. Common Mistakes

---

# Mistake 1 — Using Global Username

Problem:
- all projects show same author

Fix:
- use local config

---

# Mistake 2 — Wrong Remote URL

Wrong:

```bash
git@github.com:user/repo.git
```

Correct:

```bash
git@github-project:user/repo.git
```

---

# Mistake 3 — Config File Extension

Wrong:

```txt
config.txt
```

Correct:

```txt
config
```

---

# Mistake 4 — Sharing Private Key

Never share:

```txt
id_ed25519
```

Only share:

```txt
id_ed25519.pub
```

---

# 22. Troubleshooting

---

# Error: Permission denied (publickey)

Possible reasons:
- SSH key not added
- wrong config
- wrong remote URL

---

# Check Loaded Keys

```bash
ssh-add -l
```

---

# Re-add Keys

```bash
ssh-add ~/.ssh/id_ed25519_practice
ssh-add ~/.ssh/id_ed25519_project
```

---

# Error: Repository not found

Usually:
- wrong GitHub account
- wrong repository URL

---

# Check Remote URL

```bash
git remote -v
```

---

# 23. Recommended Workflow

---

# Practice Projects

Use:
- practice SSH key
- practice GitHub account
- practice local git config

---

# Real Projects

Use:
- project SSH key
- real GitHub account
- real local git config

---

# 24. Recommended Django `.gitignore`

```gitignore
venv/
__pycache__/
*.pyc
.env
db.sqlite3
.vscode/
media/
```

---

# 25. Final Folder Structure

```txt
.ssh/
│
├── config
├── id_ed25519_practice
├── id_ed25519_practice.pub
├── id_ed25519_project
├── id_ed25519_project.pub
└── known_hosts
```

---

# 26. Conclusion

You now understand:

✅ Git vs GitHub  
✅ SSH authentication  
✅ Public vs private keys  
✅ Multiple GitHub account setup  
✅ Global vs local git config  
✅ Professional workflow  
✅ Correct repository management

This setup is used by professional developers worldwide.
