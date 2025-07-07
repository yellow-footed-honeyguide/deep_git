# Git Ninja Challenge

You've inherited a broken repository! Your mission is to fix it using advanced Git techniques.

## Your Tasks:

### 1. Recovery Mission (use reflog)
- Some important commits were lost! 
- Use `git reflog` to find them
- You should find commits for: power function, documentation, and a bug fix
- Restore these commits to a new branch called `recovered`

### 2. Bug Hunt (use bisect)
- There's a divide-by-zero bug somewhere in history
- Use `git bisect` to find which commit introduced it
- Start with `git bisect start`
- Mark current state as bad: `git bisect bad`
- Mark the first commit as good: `git bisect good <first-commit-hash>`
- Test with: `node -e "require('./calculator').divide(10, 0)"`
- Document your findings in `bisect-results.txt`

### 3. Clean Up Messy Commit (use add -p)
- The last commit on main is a mess! It has multiple unrelated changes
- Reset it: `git reset HEAD~1`
- Use `git add -p` to create separate, logical commits:
  - One for new math functions (sqrt, percentage)
  - One for logging functionality
  - One for configuration files (.gitignore, config.json)
  - One for updated tests
- Each commit should have a clear, descriptive message

### 4. Repository Cleanup
- Remove all feature/ and bugfix/ branches
- Run `git gc --aggressive`
- Document the before/after size of .git folder in `cleanup-report.txt`

### 5. Submodule Update
- The utils submodule needs updating
- Go into utils/ and add a new file: `math-helpers.js`
- Commit the change inside the submodule
- Update the parent repository to track the new submodule commit

## Deliverables:
1. Create `recovery-log.txt` with the hashes and messages of recovered commits
2. Create `bisect-results.txt` with the problematic commit details  
3. Your commit history should be clean and logical
4. Create `cleanup-report.txt` with size comparison
5. The submodule should be properly updated

## Submit:
- Zip your entire repository (including .git folder!)
- Name it: `git-ninja-[yourname].zip`

Good luck, ninja! 🥷
