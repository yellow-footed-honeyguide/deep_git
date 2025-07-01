## LOCAL HOOKS (INSTANT FEEDBACK - CATCHES DUMB MISTAKES)

**pre-commit** (1-5 seconds)
- Syntax errors ("you forgot a bracket!")
- Code formatting ("spaces vs tabs war")
- Console.logs left behind
- Merge conflict markers
- Large files ("no 100MB videos in repo!")
- Secrets/passwords in code

**commit-msg** (instant)
- "asdfasdf" commit messages
- Missing ticket numbers
- Wrong format (no "feat:", "fix:" prefix)

**pre-push** (5-30 seconds)
- Failing unit tests
- Linting errors
- Type checking (TypeScript/Flow)
- Basic security scan

## CI/CD PIPELINE (SERVER POWER - CATCHES INTEGRATION PROBLEMS)

**Stage 1: Quick Checks** (2-5 minutes)
- Compile/Build ("does it even build?")
- Unit tests ("does your code work in isolation?")
- Code coverage ("did you test your shit?")
- Dependencies check ("is that npm package malicious?")

**Stage 2: Integration** (5-15 minutes)
- Integration tests ("does it work with database?")
- API contract tests ("did you break other teams?")
- Database migrations ("will this destroy production data?")
- Cross-service communication

**Stage 3: Quality Gates** (10-30 minutes)
- Performance regression ("did you make it slower?")
- Security scanning ("any vulnerabilities?")
- Load testing ("will it handle Black Friday?")
- Browser compatibility ("does it work in Safari?")

**Stage 4: Deployment** (5-20 minutes)
- Deploy to staging
- Smoke tests ("basic features still work?")
- Health checks
- Rollback preparation

**Stage 5: Production** (continuous)
- Canary deployment ("test on 1% of users")
- Monitoring alerts
- Error rates
- Performance metrics

## THE PHILOSOPHY

```
Developer's Machine -> Git Server -> CI Server -> Staging -> Production
FAST & CHEAP      ->            -> SLOW & THOROUGH    -> REAL WORLD
```

**Each stage filters out different shit:**
- Hooks = stupid mistakes
- CI = integration failures  
- Staging = environment issues
- Production = real user problems

**The further the bug travels, the more expensive it becomes:**
- Caught by hook = 0 cost
- Caught by CI = 30 min wasted
- Caught in staging = 1 day wasted
- Caught in production = $$$$ lost + angry users