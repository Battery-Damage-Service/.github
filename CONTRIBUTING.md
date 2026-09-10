# Contributing to BDS Kundenportal

Welcome! This document defines the mandatory rules for working in this repository. Please read it carefully before creating branches, committing changes, or opening pull requests.

---

## 🌿 Branch Naming

Branches **must** follow the naming schema below. Branches with invalid names will automatically be blocked by the CI pipeline when opening a pull request.

| Prefix | When to use |
|---|---|
| `feature/` | Developing a new feature |
| `bugfix/` | Fixing a bug |
| `hotfix/` | Critical fix applied directly toward main |
| `release/` | Preparing a release |
| `chore/` | Maintenance, dependency updates, refactoring |

### ✅ Valid Branch Names
```
feature/customer-portal-login
feature/dashboard-filter
bugfix/fix-pagination
bugfix/session-expiry
hotfix/critical-auth-fix
release/v1.0.0
chore/update-dependencies
```

### ❌ Invalid Branch Names
```
johns-branch
test123
my-fix
WIP-something
FEATURE/Login
```

### 🔧 How to Rename a Branch (if created incorrectly)
```bash
# Rename locally
git branch -m old-name feature/my-feature

# Delete old branch on GitHub and push the new one
git push origin --delete old-name
git push origin feature/my-feature

# Set the new upstream
git branch --set-upstream-to=origin/feature/my-feature feature/my-feature
```

---

## 📝 Commit Messages

We follow the **Conventional Commits** standard. Every commit message must match the following format:

```
<type>(<scope>): <description>
```

### Allowed Types

| Type | When to use |
|---|---|
| `feat` | A new feature |
| `fix` | A bug fix |
| `chore` | Maintenance or dependency updates |
| `docs` | Documentation changes only |
| `refactor` | Code restructuring without new features or bug fixes |
| `test` | Adding or updating tests |

### ✅ Valid Commit Messages
```
feat(auth): add JWT login
feat(dashboard): add request filter by status
fix(pagination): correct page count calculation
chore: update dependencies
docs: add API documentation
refactor(dashboard): simplify chart rendering
```

### ❌ Invalid Commit Messages
```
Fixed the bug
WIP
asdfgh
Update
fix: Fixed the Bug.     ← capital letter + period at the end
FEAT: new thing         ← uppercase type
```

---

## 🔁 Pull Request Process

1. Always create your branch from the current `develop` branch — never from `main`
2. Commit your changes following the commit message rules above
3. Open your PR against `develop` — **never directly against `main`**
4. At least **1 approval** from another team member is required before merging
5. All **CI checks must pass** before a merge is allowed
6. The branch will be deleted automatically after merging

---

## 🚫 What is Prohibited on `main`

- Direct pushes (`git push`) — changes must go through a PR
- Force pushes (`git push --force`)
- Deleting the branch

---

## ❓ Questions

If you have any questions about the process or these rules, contact Andreas Klippenstein at andreas.klippenstein@batterydamageservice.de.
