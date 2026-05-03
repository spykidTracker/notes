# Setup Git SSH & Connect GitHub

## Open Git Bash
- Click Start
- Search Git Bash
- Open it

## Create SSH Key

Run:
```bash
ssh-keygen -t ed25519 -C "your_github_email@example.com"
```

Use the same email as your GitHub account.

## Choose Key Location

You will see:
Enter file in which to save the key (C:\Users\LENOVO/.ssh/id_ed25519):

Press ENTER.  
Do NOT type anything.  
This will automatically create the `.ssh` folder.

## Passphrase

You will be asked:
Enter passphrase (empty for no passphrase):

Press ENTER  
Then press ENTER again to confirm.

## SSH Key Created

You should see:
Your identification has been saved in C:\Users\LENOVO\.ssh\id_ed25519  
Your public key has been saved in C:\Users\LENOVO\.ssh\id_ed25519.pub  

This means the key was created successfully.

## Verify SSH Files

Run:
```bash
ls ~/.ssh
```
You should see:
id_ed25519  
id_ed25519.pub

## Copy Public Key

Run:
```bash
cat ~/.ssh/id_ed25519.pub
```

You will see a long line starting with:
ssh-ed25519 AAAAC3...

Copy the entire line.

## Add SSH Key to GitHub

1. Open GitHub in browser  
2. Click profile picture → Settings  
3. Go to SSH and GPG keys  
4. Click New SSH key  
5. Title → My Laptop (or any name)  
6. Paste the copied key  
7. Click Add SSH Key

## Test SSH Connection

Run:
```bash
ssh -T git@github.com
```

Type yes and press Enter.

You should see:
Hi username! You've successfully authenticated

## Next Step

After completing this setup, convert your existing GitHub repository from HTTPS to SSH so you can push code without entering your password.