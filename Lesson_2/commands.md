# Lesson 2 Git Commands

⚙️ `git rebase main`
- Replays your branch's changes on top of the latest main.

⚙️ `git rebase -i HEAD~3` 
- Launches interactive editor to squash, edit, or reorder the last 3 commits

⚙️ `git rebase --continue` 
- Restarts rebase after you've fixed merge conflicts

⚙️ `git rebase --abort` 
- Nukes the entire rebase operation. Back to start, no harm done

⚙️ `git pull --rebase` 
- Fetches remote changes and rebases your commits on top. Cleaner than merge
