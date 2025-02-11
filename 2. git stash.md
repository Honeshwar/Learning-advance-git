# Git Stash: Temporarily Save Changes Without Committing

```
It is use to save temporarily changes on our local machine with committing. so we can new commit other changes, 

use:
    - so no conflict appears.
    - safely or easily switch branch

Then, after we will move our save changes to our local branch
```
## What is Git Stash?
git stash is a command that allows you to temporarily save changes that you’re not ready to commit yet. This is particularly useful when you need to switch branches or pull updates from a remote repository but don’t want to lose your uncommitted work.

## Why Use Git Stash?
- Switch Branches Safely: You can stash your changes and switch branches without committing incomplete work.
- Avoid Conflicts: Stashing prevents conflicts when pulling updates from a remote repository.
- Keep Your Working Directory Clean: Stashing allows you to keep your working directory clean while you work on other tasks.
## How to Use Git Stash

To stash your current changes:
  ``` 
  git stash
  ```
This will save your changes and revert your working directory to the last commit.

To apply the most recent stash:
  ``` 
  git stash apply 
  ```
To apply and delete the most recent stash:
   ```
   git stash pop or git stash pop stash@{n} 
   ```
To list all stashes:
   ```
   git stash list
   ```
To apply a specific stash:
  ```
   git stash apply stash@{n} 
   ```
Replace n with the index of the stash you want to apply.


## Advanced Stash Commands
- Stash with a Message: You can add a message to your stash for better identification:
```
  git stash save "Work in progress on feature X" or git stash save -u "Work in progress on feature X"
```
- Stash Untracked Files: By default, git stash only stashes tracked files(``` files that in track by brach history ```). To include untracked files(``` files that is not until yet track by branch history (no existence of file in branch), because that file is not present in branch history it is new file, folder,... ```), use:
  ``` 
  git stash -u 
  ```
- Stash All Changes, Including Ignored Files: To stash everything, including ignored files, use:
  ``` 
  git stash -a
  ``` 
Example: Using Git Stash to Switch Branches
Suppose you’re working on a feature branch and need to switch to main to review a pull request, but you’re not ready to commit your changes. You can stash your changes and switch branches:
  ``` 
git stash
git checkout main
  ``` 
After reviewing the pull request, you can return to your feature branch and apply your stashed changes:

  ``` 
git checkout feature-branch
git stash pop
  ``` 
 

 ## commands
 ```
    git stash

    git stash apply 

    git stash pop or git stash pop stash@{n} 

    git stash list

    stash apply stash@{n} 

    git stash save "Work in progress on feature X" or git stash save -u "Work in progress on feature X"

    git stash -u 

    git stash -a
 
 

 ```