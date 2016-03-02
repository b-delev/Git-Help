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

Commit history
```git
git log

// Changes over time in a file
git log -p <file>

// Who changed what and when in file
git blame <file>
```

Branches
```git
// List all branches
git branch -av

// Switch to branch
git checkout <branch-name>

// Create new branch
git branch <branch-name>

// Delete local branch
git branch -d <branch-name>

// Mark current commit with a tag
git tag <tag-name>
```


Branches

```git
// Merge from branch into your current branch
git branch  - check on what branch is in the moment
git merge <branch>

git rebase <branch>
git rebase  --abort
git rebase  --continue

git mergetool
```

Discard current changes
```git
git stash
```


Working with remote
```git
git remote

// Verify remote repo
git remote -v

// Add remote repo
git remote
git remote add origin https://github.com/user/repo.git
git remote -v
git push

// Download remote, but don't integrate into HEAD
git fetch <remote>

// Download changes and integrate into HEAD
git pull <remote> <branch>

// Upload local changes to remote
git push <remote> <branch>

// Delete remote branch
git branch -dr <remote/branch>

// Inspect a remote
git remote show origin

// Rename a remote
git remote rename test delev

// Delete remote repo
git remote rm name-of-the-repo
```

Undo one commit on remote master branch
```git
git reset HEAD^
git push -u origin master --force
```

Generate a patch
```git
git format-patch -1 commit_id -o ../DirectoryLocation
```
