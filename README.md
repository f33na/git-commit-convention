# 📋 Git Commit Convention

> A lightweight, practical standard for commit messages and semantic versioning — works for solo developers and teams alike.

[![Standard Version](https://img.shields.io/badge/standard-v1.0.0-blue)](./GIT_CONVENTION.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## Why this standard?

Most commit conventions (like Conventional Commits) are designed for large teams with CI/CD pipelines and automated changelogs. This standard is different:

- ✅ Works for **solo developers** on small projects
- ✅ Works for **teams** with a task tracker and branches
- ✅ Stays **readable** in `git log` without extra tooling
- ✅ Maps directly to **Semantic Versioning (SemVer)**

---

## Commit Format

```
[TASK-ID/TAG] Short description of the change
```

### Two modes

**Full format** — when you have a task and a dedicated branch:

```
[AUTH-42/FEATURE] Add OAuth2 authorization via Google
[PAY-7/FIX] Fix amount rounding on currency conversion
[API-15/MAJOR] Change response structure of /users endpoint
```

**Short format** — solo project, no tracker, committing to `main`/`dev`:

```
[INIT] Initialize project
[FEATURE] Add dark theme
[FIX] Remove memory leak in WebSocket handler
[RELEASE] v1.3.0
```

> The branch name always matches `TASK-ID`.

---

## Change Tags

| Tag        | Description                          | SemVer impact           |
| ---------- | ------------------------------------ | ----------------------- |
| `INIT`     | Project or module initialization     | —                       |
| `FEATURE`  | New functionality                    | **MINOR** ↑             |
| `FIX`      | Bug fix                              | **PATCH** ↑             |
| `HOTFIX`   | Urgent production fix                | **PATCH** ↑             |
| `MAJOR`    | Breaking change, API incompatibility | **MAJOR** ↑             |
| `REFACTOR` | Refactoring without behavior change  | **PATCH** ↑             |
| `PERF`     | Performance improvement              | **PATCH** / **MINOR** ↑ |
| `STYLE`    | Formatting, linting, indentation     | —                       |
| `DOCS`     | Documentation                        | —                       |
| `TEST`     | Adding or updating tests             | —                       |
| `CHORE`    | Dependencies, configs, CI/CD         | —                       |
| `REVERT`   | Reverting a previous commit          | **PATCH** ↑             |
| `RELEASE`  | Release commit, version bump         | —                       |

---

## Semantic Versioning

Version format: **`MAJOR.MINOR.PATCH`**

Look at all commits since the last `RELEASE` tag and apply the first matching rule:

```
Any MAJOR?              →  MAJOR++,  MINOR = 0, PATCH = 0
Any FEATURE or PERF*?  →  MINOR++,  PATCH = 0
Any FIX / HOTFIX / …?  →  PATCH++
Only STYLE/DOCS/CHORE  →  no change
```

> `*` `PERF` bumps `MINOR` only when the improvement is significant to the end user.

---

## Release Flow

```bash
# 1. Finish all work, then mark the release
git commit --allow-empty -m "[RELEASE] v1.3.0"

# 2. Create an annotated tag
git tag -a v1.3.0 -m "Release v1.3.0"

# 3. Push with tags
git push origin main --tags
```

---

## Writing Good Descriptions

- Max **72 characters**
- Use **imperative mood**: _Add_, _Fix_, _Remove_, _Update_
- No period at the end
- Add a body after a blank line when context is needed:

```
[AUTH-42/FEATURE] Add OAuth2 authorization via Google

Implemented authorization via Google OAuth2.
Added environment variables GOOGLE_CLIENT_ID and GOOGLE_CLIENT_SECRET.
Affected modules: auth, config, middleware.
```

---

## Quick Reference Card

```
Has a branch / task?
  YES →  [TASK-ID/TAG] Description
  NO  →  [TAG] Description

Does the TAG affect the version?
  MAJOR    →  x+1.0.0
  FEATURE  →  x.y+1.0
  FIX      →  x.y.z+1
  others   →  no change
```

---

## Full Documentation

- Main [GIT_CONVENTION.md](./GIT_CONVENTION.md)
- 🇬🇧 [GIT_CONVENTION_EN.md](./i18n/GIT_CONVENTION_EN.md)
- 🇷🇺 [GIT_CONVENTION_RU.md](./i18n/GIT_CONVENTION_RU.md)

---

## Contributing

Found an issue or have a suggestion? Open an [issue](../../issues) or submit a [pull request](../../pulls).  
Please follow this very convention when contributing 😉

---

## License

[MIT](LICENSE)
