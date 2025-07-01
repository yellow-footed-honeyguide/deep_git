## Many Decent Project Uses These:

🐚 pre-commit.sample – Runs checks before you commit (linting, tests, formatting).
Main feature: Stops garbage code from being committed.

🐚 commit-msg.sample – Validates commit messages (enforces rules like Conventional Commits).
Main feature: No more shitty "fix bug" commit messages.

🐚 pre-push.sample – Runs checks before pushing to remote (full test suite, security scans).
Main feature: Prevents CI from roasting you.

## Useful, But Not Always Set Up:

🐚 prepare-commit-msg.sample – Auto-fills commit messages (adds issue numbers, templates).
Main feature: Saves you from typing boilerplate.

🐚 post-update.sample – Triggers actions after repo updates (auto-deploy, notifications).
Main feature: Automates boring post-push tasks.

🐚 pre-rebase.sample – Checks if rebase is safe (prevents history disasters).
Main feature: Saves you from git reflog hell.

## Rarely Used (Mostly for Advanced/Server-Side Stuff)
🐚 pre-receive.sample – Server-side hook, validates pushes (blocks bad commits).
Main feature: The final boss of code quality.

🐚 fsmonitor-watchman.sample – Speeds up Git by tracking file changes faster.
Main feature: Makes Git less slow on huge repos.

🐚 update.sample – Runs when refs are updated (fine-grained branch control).
Main feature: Like pre-receive, but per-branch.

## The Rest (Who Even Uses These?)
pre-applypatch, push-to-checkout.sample, sendemail-validate.sample → Niche cases, legacy stuff.
