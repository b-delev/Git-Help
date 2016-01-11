# Git-Help

## Short manual for working with git


Multiple git accounts with ssh

```git
ssh-keygen -t rsa -C "your-email-address"
```

Add your public key ~/.ssh/id_rsa.pub to your github/gitlab/git... account.
You can add as many accounts as you want with different emails or use one public key in many git accounts.

List git configuration

```git
git config --list
```

Config default git text editor 

```git
git config --global core.editor vim
```

Config name and email

```git
git config --global user.name "Your Name"
git config --global user.email "your-email-address"
```

Get project from existing repo ( Clone )

```git
git clone git@github.com:b-delev/Git-Help.git
```
Create new local repo
```git

// !!! If the server is github you have to create the repo from the web interface
git init
git add .
git commit -m "First commit"
git remote add origin https://github.com/user/repo.git
```



Working with remote
```git
git remote

// verify remote repo
git remote -v

//add remote repo
git remote
git remote add origin https://github.com/user/repo.git
git remote -v
git push

// inspect a remote
git remote show origin

// rename a remote
git remote rename test delev

// delete remote repo
git remote rm name-of-the-repo
```

