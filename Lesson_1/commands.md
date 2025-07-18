# Lesson 1 Git Commands

⚙️ `git cat-file -p 75675257f7f4180abd2d01fbc6e6d71dfb238f41`
-  Show content of git object in pretty format

⚙️ `git add -p`
- Pick & stage changes piece by piece

⚙️ `git diff --cached`
- Show what’s staged (ready to commit)

⚙️ `git reset --soft HEAD~1`   
- Uncommit → changes remain staged (undoes commit but keeps changes staged)

⚙️ `git reset --mixed HEAD~1`   
- Undoes commit, keeps changes unstaged

⚙️ `git reset HEAD~1`           
- Same as above (--mixed is default)

⚙️ `git reset --hard HEAD~1`    
- COMPLETELY discards commit and all changes (WARNING: Destructive! All changes are LOST)

⚙️ `git checkout 84e9069`
- Temporary view → requires stashing changes (detached HEAD state)

⚙️ `git switch 84e9069`
- Modern alternative (detached HEAD state, but safer)
