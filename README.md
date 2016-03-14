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

Stashing - backing up the current stage 
```git

// List all the stashes
git stash list 

$ git stash list
stash@{0}: WIP on master: 686b55d Add test2.
stash@{1}: WIP on gerbils: b2bdead Add test1.
stash@{2}: WIP on gerbils: b2bdead Add test.


// Add to stash
git stash
// or
git stash save

// Get latest stash
git stash apply
// or
git stash apply stash@{1}

// If there is a conflict on applying a stash, you have to reset your current changes or commit them.

// Drop lastest stash
git stash drop
// or 
git stash drop stash@{0}

// Remove the last stash from the stash stack
git stash pop

// Stash only not staged for commit area
git stash save --keep-index
// Now you can commit your latest changes added to staging area

// Include untracked files in the stash
git stash save --include-untracked

git stash show
// or
git stash show stash@{0}

git stash show --patch

// You can save the stash with a message
git stash save "Add gerbils page, start index."

// Create new branch out of a stash
git stash branch test2 stash@{0}
git commit -am "Test 2"

// Clear the whole stash stack
git stash clear

```


Tree filter
If you want to remove a file in history
```git
git filter-branch --tree-filter <command> ...
// specify any shell command

git filter-branch --tree-filter 'rm -f passwords.txt'

// With --all you will remove the file from all branches, all commits
git filter-branch --tree-filter 'rm -f passwords.txt' -- --all

// If filter-branch leave some commits empty, you can remove them by
git filter-branch -f --prune-empty -- --all
```

Cherry-pick
```git
// We can get directly a commit from any branch in the tree with cherry-pick hash
git cherry-pick 53212e5
// Now you have the commit from different branch as latest commit in your branch.
// You can give a different name of that commit:
 git cherry-pick --edit 5321

// You can get two commits and put them in the staging area, but no commit
git cherry-pick --no-commit 53212e5 55ae374

// Or get the commit without the name 
git cherry-pick -x 5321

// The commit you get maybe is somebody elses, you can add your name
git cherry-pick --signoff 5321
```


Submodules
```git
// Git repo inside a git repo
// Add css to your project
git submodule add git@github.com:css.git
git commit -m "Add CSS submodule."
git push

// you can see .gitmodules for all your modules
.gitmodules

// When you update the module you have to commit and push in the module
// Than got the the parent project and add {module} | commit | push too


// When you have a project with submodules you can clone it, but you should init & update the submodules with
git submodule init
git submodule update

// When you work on a submodule occasionally other developers can pull your changes by simply
git pull 
git submodule update

// When you have to make changes in a submodule first you have to associate the submodule with a brach by
git branch test2 b6bb78f 
git checkout master
git merge b6bb78f
git push
cd .. // to the parent project
git add css
git commit -m "The new update in css submodule."
git push


```