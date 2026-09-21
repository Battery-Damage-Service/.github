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

We follow the **Conventional Commits** standard. Every commit message must use one of the following formats:

```
<type>(<scope>): <description>
<type>: <description>
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

1. Always create your branch from the current `main` branch
2. Commit your changes following the commit message rules above
3. Open your PR against `main`
4. At least **1 approval** from another team member is required before merging
5. All **CI checks must pass** before a merge is allowed
6. The branch will be deleted automatically after merging

---

## 🌐 GitHub Web Workflow (for non-dev contributors)

Use this when you do not work locally and only use the GitHub website:

1. Open the target repository and navigate to the file you want to change
2. Click the pencil icon (**Edit this file**) and make your change
3. In **Commit changes**, choose **Create a new branch** and use a valid branch name (`feature/...`, `bugfix/...`, `hotfix/...`, `release/...`, or `chore/...`)
4. Use a commit message that follows the commit rules above, then commit the changes
5. Open a Pull Request to `main`, fill out the PR template, and request a review
6. Wait for CI checks + approval, then squash-merge and delete the branch

Simple safety rules:
- Never edit or paste secrets (passwords, tokens, connection strings) into GitHub
- Keep each PR focused on one small topic
- If a check fails, paste the error into AI and apply the fix in the same PR branch

---

## 🚫 What is Prohibited on `main`

- Direct pushes (`git push`) — changes must go through a PR
- Force pushes (`git push --force`)
- Deleting the branch

---

## 🔒 Branch Protection

`main` is protected in both `kundenportal-bds` and `kundenportal-bds-functions`. The rules themselves live per-repo under **Settings → Branches → Branch protection rules** (GitHub has no single switch that covers both repos at once), but both use the same configuration:

| Rule | Setting |
|---|---|
| Require a pull request before merging | ✅ — 1 approval, dismiss stale approvals on new commits |
| Require status checks to pass | ✅ — branch must be up to date; checks get added here as CI jobs land |
| Require conversation resolution before merging | ✅ |
| Applies to admins too | ✅ ("Do not allow bypassing the above settings") |
| Allow force pushes | ❌ blocked |
| Allow deletions | ❌ blocked |

### ✅ Enforcement status (verify after plan or policy changes)
Branch protection behavior can change based on repository visibility, owner type, and GitHub plan. After any billing-plan change or major policy update, verify enforcement directly in repository settings and with a small test PR to confirm that required reviews/checks are actually blocking merges as expected.

### If "require 1 approval" ever deadlocks
GitHub never counts your own review as an approval of your own PR. If only one person is available to review, a PR can get stuck at "0 of 1 required approvals" with no way to merge through the UI. A repo admin can temporarily lower the required approval count (or delete the rule) under Settings → Branches, then restore it once a second reviewer is available again.

---

## ❓ Questions

If you have any questions about the process or these rules, contact Andreas Klippenstein at andreas.klippenstein@batterydamageservice.de.
