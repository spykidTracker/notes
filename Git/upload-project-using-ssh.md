# Set Up SSH for Local Machine & Push Project

## 1) Go to Your Project Folder

Open Git Bash and go to your project directory.

Example:
```bash
cd my-project
```
(Use your actual project path)

---

## 2) Check Current Connection Type

Run:
```bash
git remote -v
```

You will see something like:
```
origin  https://github.com/username/repo.git (fetch)
origin  https://github.com/username/repo.git (push)
```

If you see this error instead:
```
fatal: not a git repository (or any of the parent directories): .git
```

Then initialize Git first:
```bash
git init
```

This creates a `.git` folder in your project directory.

---

## 3) Copy SSH URL from GitHub

1. Open your repository on GitHub in browser  
2. Click the green **Code** button  
3. Select **SSH**  
4. Copy the URL that looks like:

```
git@github.com:username/repo.git
```

---

## 4) Create the Connection

Run:
```bash
git remote add origin git@github.com:username/repo.git
```

You can replace **origin** with any name if you want.

Verify:
```bash
git remote -v
```

Now it should show:
```
origin  git@github.com:username/repo.git (fetch)
origin  git@github.com:username/repo.git (push)
```

Your repo now uses SSH.  
No username, no password, no token required.

---

## 5) Add All Project Files

```bash
git add .
```

This stages all files for commit.

---

## 6) Create First Commit

```bash
git commit -m "Initial commit"
```

---

## 7) Set Main Branch

```bash
git branch -M main
```

This renames your current branch to **main**.

---

## 8) Upload Project

```bash
git push -u origin main
```

Wait a few seconds, then refresh GitHub → your project will appear.

---

## 9) Future Updates

For future changes run:

```bash
git add .
git commit -m "Your commit message"
git push
```

This updates your GitHub repository with the latest changes.