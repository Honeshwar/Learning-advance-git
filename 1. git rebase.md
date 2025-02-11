
# How to use git rebase

```
it is use to combine multiple commit into single commit, edit commit message, delete any commit...

it rebase or re-order branch structure history
```

## What is Interactive Rebase?
Interactive rebase (git rebase -i) is a powerful feature that allows you to rewrite your commit history. It’s particularly useful for cleaning up messy commits before pushing them to a shared repository or preparing your code for a pull request.

## Why Use Interactive Rebase?
- Clean Commit History: Interactive rebase helps you squash multiple small commits into a single meaningful commit, making your history easier to read.
- Edit Commit Messages: You can modify commit messages to make them more descriptive or fix typos.
- Reorder Commits: If you accidentally committed changes out of order, interactive rebase lets you rearrange them.
- Drop Unnecessary Commits: You can remove commits that are no longer needed.


## How to Use Interactive Rebase
```
To start an interactive rebase, use the following command:
here -i flag open a vim terminal(interactive terminal)

git rebase -i HEAD~n
Here, n is the number of commits you want to interactively rebase. For example, if you want to rebase the last three commits:

git rebase -i HEAD~3
This will open an editor with something like this:

pick abc123 Commit message 1
pick def456 Commit message 2
pick ghi789 Commit message 3

```
You can now perform various actions by replacing the word pick with one of the following commands:

- squash (or s): Combine this commit with the previous one.
- edit (or e): Pause the rebase process to modify this commit.
- reword (or r): Change the commit message.
- drop (or d): Remove the commit entirely.
- fixup (or f): Similar to squash, but discard the commit message.

```
UseFull:
    - Squash
    - reword
    - drop (dangerous entire changes commit will gone away)
```

After saving and closing the editor, Git will apply your changes. If you chose to edit or squash commits, Git will pause the rebase process, allowing you to make further modifications.

## Don't of Interactive Rebase
- Avoid Rebasing Shared Branches: Never rebase commits that have already been pushed to a shared branch. This can cause conflicts for other developers who have based their work on those commits.
- Use with Caution: Rewriting history can be dangerous if not done carefully. Always ensure you understand the implications before proceeding.


## Some important command for git rebase
- git rebase --abort
- git rebase --skip, --continue,.. 
