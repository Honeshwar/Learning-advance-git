# 15 Git Command-Line Tricks Every Developer Should Know
#
github
#
git
#
developer
#
development
Git is an essential tool for developers, enabling version control and collaboration on codebases. Mastering Git can significantly enhance your productivity and efficiency. Here are 15 Git command-line tricks that every developer should know, presented in a way that's easy to understand and enjoyable to read. Let's dive in!

1. Stashing Changes
Ever been in the middle of something and suddenly need to switch branches? git stash is your friend! It temporarily saves your changes so you can work on something else.

git stash
To apply the stashed changes later:

git stash apply
2. Interactive Rebase
Want to clean up your commit history before merging? Interactive rebase lets you squash, reorder, or edit commits.

git rebase -i HEAD~n
Replace n with the number of commits you want to go back.

3. Cherry-Picking Commits
Need to apply a specific commit from one branch to another? Cherry-pick to the rescue!

git cherry-pick <commit-hash>
4. Reverting Commits
Made a mistake? No problem! Revert a commit to undo its changes.

git revert <commit-hash>
5. Amending Commits
Forgot to add something to your last commit? Amend it!

git commit --amend
6. Viewing Commit History
Want a pretty view of your commit history? Use:

git log --oneline --graph --decorate --all
7. Finding Large Files
Identify large files in your repository with:

git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"
8. Alias Shortcuts
Tired of typing long commands? Create aliases!

git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
9. Autocomplete
Enable Git autocomplete for your shell to save time.

For Bash:

source ~/.git-completion.bash
For Zsh:

source ~/.git-completion.zsh
10. Ignoring Files
Use .gitignore to exclude files from version control. Generate a template with:

curl https://www.toptal.com/developers/gitignore/api/<OPERATING-SYSTEM>,<IDE>,<PROGRAMMING-LANGUAGE> > .gitignore
11. Viewing Changes
See what's changed in your working directory with:

git diff
Or compare branches:

git diff branch1..branch2
12. Stashing Specific Files
Stash only specific files:

git stash push -m "your message" path/to/file
13. Bisecting Bugs
Use git bisect to find the commit that introduced a bug.

git bisect start
git bisect bad
git bisect good <commit-hash>
14. Reflog
Accidentally lost a commit? Use the reflog to recover it.

git reflog
15. Submodules
Manage dependencies with Git submodules.

git submodule add <repository-url> path/to/submodule
Conclusion
Mastering these Git tricks can make your development workflow smoother and more efficient. Whether you're stashing changes, rebasing commits, or using aliases, each trick adds a layer of control and convenience. Happy coding, and may your Git adventures be bug-free and productive! 🎉💻

This blog aims to make learning Git fun and engaging. If you found these tips helpful, share them with your fellow developers and let's all become Git masters together!

Follow me on GitHub for more tips and tricks: https://github.com/SOVANNARO