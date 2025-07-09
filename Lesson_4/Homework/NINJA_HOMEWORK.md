# Git Ninja Challenge

You've inherited a broken repository! Your mission is to fix it using advanced Git techniques.


# String Processor Homework

## Objective
Fix a broken Git repository containing a Python string processing library. You'll need to:

1. Recover lost commits
2. Find and fix a bug using git bisect
3. Clean up the repository

## Tasks

### 1. Recover Lost Commits
The repository had several important commits lost after a `git reset --hard`. 
Use Git's reflog to identify and restore these commits.

### 2. Find and Fix the Bug (not fix this bug while first task!)
The `is_palindrome()` function has a bug - it doesn't handle case sensitivity properly.
For manual or automatic bisect command you can use this script (bisect_test.py) in order to verify this is bad or good commit
```python
import sys

try:
    from calculator import divide
    try:
        from string_processor import is_palindrome
        assert is_palindrome("Anna") == True
        print("GOOD")
        exit(0)
    except AssertionError:
        print("BAD: Fails case-insensitive check")
        exit(1)
    except:
        print("BAD: Other error")
        exit(1)
except ImportError:
    print("GOOD: Function not exists")
    sys.exit(0)
```
Use git bisect to:

- Find the commit that introduced the bug

- Fix the function to properly handle case-insensitive comparison

-  Write your findings in bisect-results.txt

### 3. Clean Up
Remove experimental branches (feature/old-impl, feature/broken-unicode)

Run garbage collection to optimize the repository

Create a cleanup report showing space saved

Verification

After completing all tasks(example):

```bash
python3 -c "
from string_processor import is_palindrome
assert is_palindrome('Anna') == True, 'Test failed!'
print('All tests pass!')
"
```
Deliverables: Restored repository with all features working

bisect-results.txt with:
- Bad commit hash
- Commit message
- Description of the bug
- cleanup-report.txt with cleanup statistics

