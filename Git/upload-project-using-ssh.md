Read : set up ssh to your local machine

1) Go to your project folder
    - Open Git Bash and go to your project directory:
    - Example: cd my-project (Use your actual project path)

2) Check current connection type
    Run: git remote -v
    - You will see something like:
        origin  https://github.com/username/repo.git (fetch)
        origin  https://github.com/username/repo.git (push)
    - instead of this if it shows error like:
        - fatal: not a git repository (or any of the parent directories): .git
        -  then first you have to initialize git repository to it
            Run : git init (This will create a .git folder in your project directory)
        
3) Copy SSH URL from GitHub
    - Open your repository on GitHub in browser
    - Click the green Code button
    - Select SSH
    - Copy the URL that looks like: git@github.com:username/repo.git

4) Create the connection 
    - In Git Bash run: git remote add origin git@github.com:username/repo.git (Replace with your copied URL)
        - instead of 'origin' you can write anything you want 
    - Verify change: git remote -v 
    - Now it should show:
        origin  git@github.com:username/repo.git (fetch)
        origin  git@github.com:username/repo.git (push)
    - Now your repo uses SSH.
    - This time no username, no password, no token

5) Add all project files
    - Run: git add .
    - This will stage all your files for commit

6) Create first commit
    - Run: git commit -m "Initial commit"
    - This will create a commit with the message "Initial commit" 

7) Set main branch
    - Run: git branch -M main
    - This will rename your current branch to 'main'

8) Upload project
    - Run: git push -u origin main
    - This will push your code to GitHub for the first time
    - Wait a few seconds…
    - Refresh GitHub page -> your project will appear.

9) Future updates
    - For future changes, you can simply run:
        git add .
        git commit -m "Your commit message"
        git push
    - This will update your GitHub repository with the latest changes.