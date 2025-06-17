# Git Commit Best Practices

## 1. Feature Branch + Squash
Work freely in your feature branch. Make as many commits as you need - even 200 tiny ones. Before merging to main, squash them into one meaningful commit.

**Example:**
```bash
# In feature branch - many WIP commits
- WIP: add button
- fix typo
- adjust color
- oops, forgot file
- finally works!

# After squash
- feat(ui): add submit button with validation
```

## 2. Logical Commits
Each commit represents one complete thought or change. Not a "save point" but a logical step forward.

**Good:**
- `feat(auth): add login form validation`
- `fix(api): handle empty response correctly`
- `docs: update API authentication guide`

**Bad:**
- `save work`
- `end of day`
- `more changes`
- `stuff`

## 3. Build Rule
Code MUST compile after every single commit. Never break the build.

**Before committing:**
```bash
# Run build locally first!
npm run build  # or your build command
# Only commit if it succeeds
```

**Why:** Anyone should be able to checkout ANY commit and have working code.

## 4. Test Rule  
All tests MUST pass after every commit. No exceptions.

**Before committing:**
```bash
# Run tests locally first!
npm test  # or your test command
# Only commit if all tests pass
```

**Why:** Every commit in history should be a valid, working state of the project.

## Summary
Think of each commit as a "working snapshot" of your project. Someone should be able to:
- Checkout any commit
- Build successfully  
- Run all tests successfully
- Understand what changed and why

This keeps your git history clean, useful, and professional.
