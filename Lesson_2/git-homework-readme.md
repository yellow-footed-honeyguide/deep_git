# Git History Repair Challenge

## The Mess

You got a project from a junior developer. The git history is a disaster. Your job - fix it using rebase.

## Problems to Fix

1. **Typos in commit messages** - multiple commits have spelling errors
2. **Wrong commit order** - feature commits mixed with bugfix commits  
3. **Garbage commits** - "WIP", "test", "asdfgh" commits everywhere
4. **Huge commits** - one commit changes 20 files
5. **Missing commits** - some changes not committed at all

## Your Mission

1. Clone the project
2. Use `git rebase -i` to clean this mess
3. Final history must be:
   - Logical commit order
   - Clean commit messages
   - One commit = one feature/fix
   - No WIP or test commits

## Requirements

- Use ONLY interactive rebase
- Don't lose any code changes
- Make history beautiful

## Deliverables

Push your fixed branch as `main-fixed` to show the result.

Good luck!