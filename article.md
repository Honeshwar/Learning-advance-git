https://dev.to/hanzla-baig/5-advanced-git-techniques-every-developer-should-know-42hd

🌟 🔥 5 Advanced Git Techniques Every Developer Should Know 🚀
#
git
#
github
#
programming
5 Advanced Git Techniques Every Developer Should Know
Git is one of the most powerful tools in a developer's toolkit, but many developers only scratch the surface of its capabilities. While basic commands like git add, git commit, and git push are essential, mastering advanced Git techniques can significantly improve your workflow, help you manage complex projects, and save you from potential headaches when things go wrong. In this comprehensive guide, we’ll explore five advanced Git techniques that every developer should know. Buckle up, because this post is going to be long, detailed, and packed with high-level knowledge.

1. Interactive Rebase: Rewrite History Like a Pro
What is Interactive Rebase?
Interactive rebase (git rebase -i) is a powerful feature that allows you to rewrite your commit history. It’s particularly useful for cleaning up messy commits before pushing them to a shared repository or preparing your code for a pull request.

Why Use Interactive Rebase?
Clean Commit History: Interactive rebase helps you squash multiple small commits into a single meaningful commit, making your history easier to read.
Edit Commit Messages: You can modify commit messages to make them more descriptive or fix typos.
Reorder Commits: If you accidentally committed changes out of order, interactive rebase lets you rearrange them.
Drop Unnecessary Commits: You can remove commits that are no longer needed.
How to Use Interactive Rebase
To start an interactive rebase, use the following command:

git rebase -i HEAD~n
Here, n is the number of commits you want to interactively rebase. For example, if you want to rebase the last three commits:

git rebase -i HEAD~3
This will open an editor with something like this:

pick abc123 Commit message 1
pick def456 Commit message 2
pick ghi789 Commit message 3
You can now perform various actions by replacing the word pick with one of the following commands:

squash (or s): Combine this commit with the previous one.
edit (or e): Pause the rebase process to modify this commit.
reword (or r): Change the commit message.
drop (or d): Remove the commit entirely.
fixup (or f): Similar to squash, but discard the commit message.
After saving and closing the editor, Git will apply your changes. If you chose to edit or squash commits, Git will pause the rebase process, allowing you to make further modifications.

Example: Squashing Commits
Let’s say you have three commits that you want to combine into one:

abc123 Add feature X
def456 Fix bug in feature X
ghi789 Refactor feature X
Run the interactive rebase:

git rebase -i HEAD~3
In the editor, change the second and third lines to squash:

pick abc123 Add feature X
squash def456 Fix bug in feature X
squash ghi789 Refactor feature X
Save and close the editor. Git will then prompt you to create a new commit message for the combined commit. After editing the message, your history will now contain a single commit with all the changes.

Caveats of Interactive Rebase
Avoid Rebasing Shared Branches: Never rebase commits that have already been pushed to a shared branch. This can cause conflicts for other developers who have based their work on those commits.
Use with Caution: Rewriting history can be dangerous if not done carefully. Always ensure you understand the implications before proceeding.
2. Git Bisect: Find Bugs Faster
What is Git Bisect?
git bisect is a binary search tool that helps you quickly identify the commit that introduced a bug. Instead of manually checking each commit, git bisect automates the process by narrowing down the range of commits where the bug was introduced.

Why Use Git Bisect?
Efficient Debugging: Instead of testing every commit, git bisect reduces the number of tests you need to perform by half each time.
Pinpoint Problematic Commits: Once you’ve identified the problematic commit, you can focus your debugging efforts on that specific change.
Automate Testing: You can integrate automated tests with git bisect to speed up the process even further.
How to Use Git Bisect
Start the bisect process:
   git bisect start
Mark the current commit as "bad" (i.e., it contains the bug):
   git bisect bad
Mark a known good commit (i.e., a commit where the bug does not exist):
   git bisect good <commit-hash>
Replace <commit-hash> with the hash of the known good commit.

Git will automatically check out a commit halfway between the good and bad commits. Test the code at this commit to determine whether the bug exists.

If the bug exists, mark the commit as bad:

   git bisect bad
If the bug does not exist, mark the commit as good:

   git bisect good
Repeat steps 4 and 5 until Git identifies the exact commit that introduced the bug.

Once you’ve found the problematic commit, reset the bisect process:

   git bisect reset
Automating Git Bisect with Scripts
If you have automated tests, you can use them with git bisect to speed up the process. For example, if you have a test script called test.sh, you can run:

git bisect run ./test.sh
Git will automatically run the script on each commit and mark it as good or bad based on the script’s exit code.

Example: Finding a Bug with Git Bisect
Suppose you have a bug in your codebase, and you suspect it was introduced somewhere in the last 100 commits. Instead of manually testing each commit, you can use git bisect to narrow it down:

Start the bisect process:
   git bisect start
Mark the current commit as bad:
   git bisect bad
Mark a known good commit (e.g., the commit from two weeks ago):
   git bisect good abc123
Git will check out a commit halfway between the good and bad commits. Run your tests and mark the commit as good or bad accordingly.

Continue this process until Git identifies the exact commit that introduced the bug.

3. Git Stash: Temporarily Save Changes Without Committing
What is Git Stash?
git stash is a command that allows you to temporarily save changes that you’re not ready to commit yet. This is particularly useful when you need to switch branches or pull updates from a remote repository but don’t want to lose your uncommitted work.

Why Use Git Stash?
Switch Branches Safely: You can stash your changes and switch branches without committing incomplete work.
Avoid Conflicts: Stashing prevents conflicts when pulling updates from a remote repository.
Keep Your Working Directory Clean: Stashing allows you to keep your working directory clean while you work on other tasks.
How to Use Git Stash
To stash your current changes:
   git stash
This will save your changes and revert your working directory to the last commit.

To apply the most recent stash:
   git stash apply
To apply and delete the most recent stash:
   git stash pop
To list all stashes:
   git stash list
To apply a specific stash:
   git stash apply stash@{n}
Replace n with the index of the stash you want to apply.

Advanced Stash Commands
Stash with a Message: You can add a message to your stash for better identification:
  git stash save "Work in progress on feature X"
Stash Untracked Files: By default, git stash only stashes tracked files. To include untracked files, use:
  git stash -u
Stash All Changes, Including Ignored Files: To stash everything, including ignored files, use:
  git stash -a
Example: Using Git Stash to Switch Branches
Suppose you’re working on a feature branch and need to switch to main to review a pull request, but you’re not ready to commit your changes. You can stash your changes and switch branches:

git stash
git checkout main
After reviewing the pull request, you can return to your feature branch and apply your stashed changes:

git checkout feature-branch
git stash pop
4. Git Worktrees: Work on Multiple Branches Simultaneously
What is Git Worktree?
git worktree allows you to have multiple working directories attached to the same repository. This is particularly useful when you need to work on multiple branches simultaneously without switching back and forth.

Why Use Git Worktree?
Avoid Constant Branch Switching: With git worktree, you can have separate directories for different branches, eliminating the need to constantly switch branches.
Isolate Work: Each worktree is isolated, so you can work on different features or bug fixes without interfering with each other.
Test Changes in Parallel: You can test changes in one branch while continuing to work on another.
How to Use Git Worktree
Create a new worktree:
   git worktree add ../new-directory branch-name
This will create a new directory called new-directory and check out branch-name into it.

List all worktrees:
   git worktree list
Remove a worktree:
   git worktree remove ../new-directory
Example: Using Git Worktree to Work on Multiple Features
Suppose you’re working on a feature branch called feature-x and need to review a pull request on feature-y. Instead of switching branches, you can create a new worktree for feature-y:

git worktree add ../feature-y feature-y
Now you can work on feature-x in your original directory and review feature-y in the new directory.

5. Git Hooks: Automate Repetitive Tasks
What are Git Hooks?
Git hooks are scripts that run automatically at certain points in the Git workflow, such as before or after a commit, push, or merge. They allow you to automate repetitive tasks, enforce coding standards, and prevent mistakes.

Why Use Git Hooks?
Enforce Coding Standards: You can use pre-commit hooks to run linters or formatters before committing code.
Prevent Bad Commits: Pre-push hooks can prevent you from pushing code that doesn’t meet certain criteria (e.g., failing tests).
Automate Deployment: Post-receive hooks can automate deployment processes when code is pushed to a remote repository.
Common Git Hooks
pre-commit: Runs before a commit is created. Useful for running linters or tests.
pre-push: Runs before a push is executed. Useful for preventing bad pushes.
post-receive: Runs on the remote repository after a push is received. Useful for triggering deployments.
How to Use Git Hooks
Git hooks are located in the .git/hooks directory of your repository. To create a hook, simply add a script with the appropriate name (e.g., pre-commit) to this directory.

Example: Enforcing Code Formatting with a Pre-Commit Hook
Create a pre-commit file in .git/hooks:
   touch .git/hooks/pre-commit
   chmod +x .git/hooks/pre-commit
Add the following script to the pre-commit file:
   #!/bin/sh
   # Run a code formatter (e.g., Prettier) before committing
   npx prettier --write .
   git add .
Now, every time you commit, the code will be automatically formatted.
Conclusion
Mastering these advanced Git techniques—interactive rebase, Git bisect, Git stash, Git worktrees, and Git hooks—can take your development workflow to the next level. Whether you’re cleaning up your commit history, debugging efficiently, or automating repetitive tasks, these tools will help you become a more productive and confident developer.

Remember, Git is a powerful tool, but with great power comes great responsibility. Always use these techniques carefully, especially when rewriting h