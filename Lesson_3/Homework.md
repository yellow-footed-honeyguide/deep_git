# Homework: Git Hooks & GitHub Actions 🚀

## Assignment Overview
Create a Python/JS/C++ project with Git hooks and GitHub Actions that automatically checks code quality.

> Attention! Submit your project as a zip file!

## Requirements

### 1. Example of Project Structure
Create a project called `student_code_checker` with:
```
student_code_checker/
├── .github/
│   └── workflows/
│       └── main.yml
├── src/
│   └── string_utils.py    # Your main code
├── tests/
│   └── test_string_utils.py    # Your tests
├── requirements.txt
├── README.md
└── .gitignore
```

### 2. Main Code (`src/string_utils.py`)
Create at least 4 string manipulation functions:
- `reverse_string(s)` - reverses a string
- `capitalize_words(s)` - capitalizes first letter of each word
- `count_vowels(s)` - counts vowels in a string
- `is_palindrome(s)` - checks if string is palindrome

### 3. Tests (`tests/test_string_utils.py`)
Write tests for ALL functions using pytest. Each function needs at least 3 test cases.

### 4. Git Hooks (MUST WORK!)
Create these hooks in `.git/hooks/`:

#### a) `pre-commit`
- Check Python syntax with `python -m py_compile`
- Check if tests exist for new functions
- Block commit if syntax errors found

#### b) `commit-msg`
- Enforce format: `type: description`
- Types allowed: `feat`, `fix`, `test`, `docs`, `chore`
- Minimum description length: 10 characters

#### c) `pre-push`
- Run ALL tests with pytest
- Block push if any test fails

### 5. GitHub Actions (`main.yml`)
Create workflow that:
- Runs on push and pull_request
- Tests on Python 3.8, 3.9, 3.10
- Runs on Ubuntu and Windows
- Checks code with flake8
- Runs all tests
- Shows test coverage

### 6. Branch Protection
Configure on GitHub:
- Protect `main` branch
- Require PR before merging
- Require status checks to pass

## Deliverables

1. **GitHub repository link** with all code
2. **Screenshots** showing:
   - Failed pre-commit hook
   - Failed commit-msg hook
   - Failed pre-push hook
   - Failed GitHub Actions
   - Successful GitHub Actions
   - Branch protection settings

## Grading Criteria

| Component | Points | What I'll Test |
|-----------|--------|----------------|
| Git Hooks | 40% | • Create file with syntax error → commit should fail<br>• Try bad commit message → should fail<br>• Break a test → push should fail |
| GitHub Actions | 30% | • Push broken code → Actions should fail<br>• Fix code → Actions should pass<br>• Check multi-platform runs |
| Code Quality | 20% | • All functions work correctly<br>• Tests cover edge cases<br>• Code follows PEP8 |
| Documentation | 10% | • Clear README<br>• Comments in code<br>• Setup instructions |

## Testing Your Work

Before submitting, test yourself:
```bash
# Test 1: Bad syntax
echo "def bad(" > bad.py
git add bad.py
git commit -m "test"  # Should FAIL!

# Test 2: Bad message
git add .
git commit -m "x"  # Should FAIL!

# Test 3: Broken test
# Break one test intentionally
git add .
git commit -m "test: check hook"
git push  # Should FAIL!
```

