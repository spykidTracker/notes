Install Git: https://git-scm.com/install/

Check installation in terminal / CMD: 
    git --version

Configure Git
    git config --global user.name "Your Name"
    git config --global user.email "your_email@gmail.com"

Check saved config:
    git config --list

Create GitHub Account & Repository
    1. Click New Repository
    2. Give repo name
    3. Keep Public (or Private)
    4. Click Create Repository

Create Local Project Folder
Now initialize Git in this folder
    git init

Connect Local Git to GitHub Repository
    git remote add origin https://github.com/username/myproject.git

Check connection:
    git remote -v

Add Files to Git
    Create any file (example index.html)
    Check file status:
        git status

    Add files to staging
        git add .

Commit Files
    git commit -m "First commit"

Push Code to GitHub
    git branch -M main
    git push -u origin main

Done!
Refresh GitHub → your code is there.

After This — Daily Workflow
    Whenever you change code:

    git add .
    git commit -m "describe changes"
    git push

Quick Summary (Memory Trick)
git init
git add .
git commit -m "message"
git remote add origin URL
git push -u origin main