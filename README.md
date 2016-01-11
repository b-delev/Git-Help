# Git-Help

## Short manual for working with git


## Multiple git accounts with ssh

```bash
ssh-keygen -t rsa -C "your-email-address"
```

Add your public key ~/.ssh/id_rsa.pub to your github/gitlab/git... account.
You can add as many accounts as you want with different emails or use one publik key in many git accounts.

List git configuration

```bash
git config --list
```

Config default git text editor 

```bash
git config --global core.editor vim
```

Config name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email-address"
```