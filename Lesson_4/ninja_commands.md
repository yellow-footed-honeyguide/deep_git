# 🥷 Git Ninja Essential Commands

## 1. `git reflog`
Shows a log of where your HEAD has been. Like a time machine for your repository!
```bash
git reflog
# Use this when: You accidentally deleted commits and need to find them
# Example: After git reset --hard, use reflog to see lost commit hashes
```

## 2. `git cherry-pick <commit-hash>`
Takes a specific commit from anywhere and applies it to your current branch.
```bash
git cherry-pick abc1234
# Use this when: You need to restore specific lost commits
# Example: Found a lost commit in reflog? Cherry-pick it back!
```

## 3. `git bisect start`
Starts a binary search through your commit history to find bugs.
```bash
git bisect start
git bisect bad                    # Current version is broken
git bisect good abc1234          # This old commit was working
# Use this when: You know something broke but don't know which commit did it
# Git will checkout commits for you to test until you find the bad one
```

## 4. `git add -p` (or `git add --patch`)
Lets you review and stage specific parts of file changes, not entire files.
```bash
git add -p filename.js
# Use this when: You made multiple changes but want separate commits
# Example: Fixed a bug AND added a feature? Split them into 2 commits!
```

## 5. `git reset --hard HEAD~n`
Moves your branch pointer back n commits and DELETES all changes.
```bash
git reset --hard HEAD~3          # Go back 3 commits and lose everything
# Use this when: You want to completely undo recent commits
# WARNING: This is destructive! But reflog can save you
```

## 6. `git gc --aggressive`
Garbage collection - cleans up unnecessary files and optimizes your repository.
```bash
git gc --aggressive
# Use this when: Your .git folder is huge and full of junk
# Example: After deleting many branches, run this to actually free up space
```

## 7. `git log -S "search string"`
Searches through all commits to find when a specific string was added or removed.
```bash
git log -S "TODO: This will break"
# Use this when: You need to find which commit introduced specific code
# Example: When did someone add that problematic function?
```

## 8. `git submodule update --init --recursive`
Initializes and updates all submodules to their correct commits.
```bash
git submodule update --init --recursive
# Use this when: You cloned a repo with submodules and they're empty
# Also use after: Someone else updated submodule references
```

## 9. `git branch -D branch-name`
Force deletes a branch, even if it has unmerged changes.
```bash
git branch -D feature/old-experiment
# Use this when: Cleaning up old branches that you don't need
# Regular -d won't delete unmerged branches, -D forces it
```

## 10. `git stash` / `git stash pop`
Temporarily saves your uncommitted changes and restores them later.
```bash
git stash                        # Save current changes
git bisect start                 # Do your bisect testing
git stash pop                    # Bring back your changes
# Use this when: You need clean working directory but don't want to lose changes
# Example: Perfect for bisect testing without losing your work
```

## 🎯 Pro Tips:

- **Always check `git status`** before and after these commands
- **Use `git reflog` as your safety net** - it remembers everything for 30 days
- **Practice in a test repo first** - these commands can be destructive
- **Combine commands** - like using stash during bisect, or cherry-pick after reflog

## 🚨 Emergency Recovery:

If you mess up, don't panic! Here's your rescue sequence:
```bash
git reflog                       # Find where you were before disaster
git reset --hard <good-hash>     # Go back to that safe point
# OR
git cherry-pick <lost-commit>    # Recover specific commits
```

Remember: Git never truly deletes anything immediately. You have 30 days to recover!