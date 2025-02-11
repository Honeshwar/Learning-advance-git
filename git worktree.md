 # Git Worktrees: Work on Multiple Branches Simultaneously
## What is Git Worktree?
git worktree allows you to have multiple working directories attached to the same repository. This is particularly useful when you need to work on multiple branches simultaneously without switching back and forth.

## Why Use Git Worktree?
- Avoid Constant Branch Switching: With git worktree, you can have separate directories for different branches, eliminating the need to constantly switch branches.
- Isolate Work: Each worktree is isolated, so you can work on different features or bug fixes without interfering with each other.
- Test Changes in Parallel: You can test changes in one branch while continuing to work on another.
## How to Use Git Worktree
Create a new worktree:
 ```
   git worktree add ../new-directory branch-name
   ```
This will create a new directory called new-directory and check out branch-name into it.

List all worktrees:
 ```
   git worktree list
 ```
Remove a worktree:
 ```
   git worktree remove ../new-directory
 ```
Example: Using Git Worktree to Work on Multiple Features
Suppose you’re working on a feature branch called feature-x and need to review a pull request on feature-y. Instead of switching branches, you can create a new worktree for feature-y:

 ```
git worktree add ../feature-y feature-y
 ```
Now you can work on feature-x in your original directory and review feature-y in the new directory.