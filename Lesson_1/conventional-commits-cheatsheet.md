# Conventional Commits Cheatsheet

## Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

## Types
- `feat` - new feature
- `fix` - bug fix
- `docs` - documentation only
- `style` - formatting, no code change
- `refactor` - code restructuring, no functional change
- `perf` - performance improvements
- `test` - adding tests
- `build` - build system or dependencies
- `ci` - CI configuration files
- `chore` - other changes (tooling, configs)
- `revert` - revert previous commit

## Common Scopes
- `api` - API endpoints, contracts
- `auth` - authentication, authorization
- `core` - core functionality
- `db` - database, migrations
- `deps` - dependencies
- `config` - configuration files
- `ui` - user interface
- `ux` - user experience
- `i18n` - internationalization
- `a11y` - accessibility
- `security` - security fixes
- `utils` - utilities, helpers
- `types` - type definitions
- `tests` - test infrastructure
- `docs` - documentation
- `build` - build scripts
- `ci` - continuous integration
- `docker` - Docker configuration
- `k8s` - Kubernetes configs

## Rules
- Subject line: max 50 characters
- Use imperative mood: "fix" not "fixed"
- No period at end of subject
- Body: wrap at 72 characters
- Body: explain WHY, not WHAT

## Breaking Changes
```
feat!: change API response format

BREAKING CHANGE: 'id' field renamed to 'userId'
```

## Examples
```
feat(auth): add OAuth2 integration
fix(api): handle null in user response
docs(readme): update installation steps
style(ui): format button components
refactor(core): extract validation logic
test(api): add user endpoint tests
build(deps): upgrade React to v18
chore(config): update eslint rules
```

## Footer References
- `Fixes #123` - closes issue
- `Refs #456` - references issue
- `BREAKING CHANGE:` - breaking change description
