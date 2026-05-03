# Setup Git SSH & Connect GitHub (Complete Guide)

This guide explains **what**, **why**, and **how** of using SSH with GitHub.  
It is written so both beginners and experienced developers can understand the full process.

---

# Why Use SSH Instead of HTTPS?

When you push code using HTTPS, GitHub asks for:
- Username
- Personal Access Token (password alternative)

This becomes annoying because you must enter credentials every time.

SSH solves this by creating a **trusted connection** between:
- Your computer
- GitHub

After setup:
- No password
- No token
- One-time authentication only

---

# What is an SSH Key?

SSH uses **public-key cryptography**.

You create 2 keys:
- **Private key** → stays on your computer (SECRET)
- **Public key** → uploaded to GitHub (SAFE)

GitHub checks:
"If public key matches the private key → allow access"

Think of it like:
- Public key = Lock
- Private key = Key

---

# Step 1 — Open Git Bash

Open Git Bash:
- Click Start
- Search **Git Bash**
- Open it

Git Bash provides a Linux-like terminal required for SSH commands.

---

# Step 2 — Create SSH Key

Run:
```bash
ssh-keygen -t ed25519 -C "your_github_email@example.com"
```

Explanation:
- `ssh-keygen` → tool to generate SSH keys
- `-t ed25519` → modern secure encryption algorithm
- `-C` → adds label (your GitHub email)

Always use the **same email as your GitHub account**.

---

# Step 3 — Choose Key Location

You will see:
```
Enter file in which to save the key (C:\Users\LENOVO/.ssh/id_ed25519):
```

Press **ENTER**.

Why?
- This uses the **default secure location**
- Git automatically knows this location
- `.ssh` folder will be created automatically

---

# Step 4 — Passphrase (Optional but Recommended)

You will see:
```
Enter passphrase (empty for no passphrase):
```

Press ENTER to skip OR set a passphrase.

What is passphrase?
- Extra password protecting your private key
- Even if someone steals your key, they cannot use it

Beginners usually skip.  
Professionals usually set it.

---

# Step 5 — SSH Keys Created

You should see:
```
Your identification has been saved in C:\Users\LENOVO\.ssh\id_ed25519
Your public key has been saved in C:\Users\LENOVO\.ssh\id_ed25519.pub
```

Files created:
- `id_ed25519` → PRIVATE KEY (never share)
- `id_ed25519.pub` → PUBLIC KEY (share with GitHub)

---

# Step 6 — Verify SSH Files Exist

Run:
```bash
ls ~/.ssh
```

You should see:
```
id_ed25519
id_ed25519.pub
```

This confirms keys exist.

---

# Step 7 — Copy Public Key

Run:
```bash
cat ~/.ssh/id_ed25519.pub
```

You will see a long line starting with:
```
ssh-ed25519 AAAAC3NzaC1...
```

Copy the **entire line**.

Important:
- Copy everything
- Do not add spaces or new lines

---

# Step 8 — Add SSH Key to GitHub

1. Open GitHub in browser
2. Click profile picture → **Settings**
3. Go to **SSH and GPG keys**
4. Click **New SSH key**
5. Title → e.g. *My Laptop*
6. Paste the copied key
7. Click **Add SSH Key**

Now GitHub knows your computer.

---

# Step 9 — Test SSH Connection

Run:
```bash
ssh -T git@github.com
```

First time message:
```
Are you sure you want to continue connecting (yes/no)?
```

Type:
```
yes
```

Success message:
```
Hi username! You've successfully authenticated
```

This confirms:
Your computer ↔ GitHub connection is working.

---

# What Happens Behind the Scenes?

When you push code:
1. GitHub checks your public key
2. Your computer proves it has private key
3. GitHub grants access
4. Push succeeds without password

---

# Next Step

Now convert your repositories from **HTTPS → SSH** so you can push code securely without entering credentials.