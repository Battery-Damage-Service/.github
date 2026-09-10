# Contributing to BDS Kundenportal

Willkommen! Dieses Dokument beschreibt die verbindlichen Regeln für die Arbeit an diesem Repository.

---

## 🌿 Branch Naming

Branches **müssen** folgendem Schema entsprechen. Branches mit ungültigen Namen werden beim PR automatisch durch die CI-Pipeline blockiert.

| Präfix | Wann benutzen |
|---|---|
| `feature/` | Neues Feature entwickeln |
| `bugfix/` | Einen Bug beheben |
| `hotfix/` | Kritischer Fix, direkt auf main |
| `release/` | Release vorbereiten |
| `chore/` | Wartung, Dependencies updaten, Refactoring |

### ✅ Erlaubte Branch-Namen
```
feature/kundenportal-login
feature/dashboard-filter
bugfix/fix-pagination
bugfix/session-expiry
hotfix/critical-auth-fix
release/v1.0.0
chore/update-dependencies
```

### ❌ Nicht erlaubte Branch-Namen
```
johns-branch
test123
mein-fix
WIP-irgendwas
FEATURE/Login
```

### 🔧 Branch umbenennen (falls falsch erstellt)
```bash
# Lokal umbenennen
git branch -m alter-name feature/mein-feature

# Alten Branch auf GitHub löschen + neuen pushen
git push origin --delete alter-name
git push origin feature/mein-feature

# Upstream neu setzen
git branch --set-upstream-to=origin/feature/mein-feature feature/mein-feature
```

---

## 📝 Commit Messages

Wir folgen dem **Conventional Commits** Standard. Jede Commit Message muss dem folgenden Format entsprechen:

```
<type>(<scope>): <beschreibung>
```

### Erlaubte Typen

| Typ | Wann benutzen |
|---|---|
| `feat` | Neues Feature |
| `fix` | Bug behoben |
| `chore` | Wartung, Dependencies |
| `docs` | Nur Dokumentation geändert |
| `refactor` | Code umgebaut, kein neues Feature |
| `test` | Tests hinzugefügt oder geändert |

### ✅ Erlaubte Commit Messages
```
feat(auth): add JWT login
feat(dashboard): add request filter by status
fix(pagination): correct page count calculation
chore: update dependencies
docs: add API documentation
refactor(dashboard): simplify chart rendering
```

### ❌ Nicht erlaubte Commit Messages
```
Fixed the bug
WIP
asdfgh
Update
fix: Fixed the Bug.     ← Großbuchstabe + Punkt am Ende
FEAT: new thing         ← Großschreibung
```

---

## 🔁 Pull Request Prozess

1. Branch vom aktuellen `develop` erstellen (nicht von `main`)
2. Änderungen committen – Commit Message Regeln beachten!
3. PR gegen `develop` öffnen – **niemals direkt gegen `main`**
4. Mind. **1 Approval** eines anderen Teammitglieds erforderlich
5. Alle **CI-Checks müssen grün** sein bevor gemergt werden darf
6. Der Branch wird nach dem Merge automatisch gelöscht

---

## 🚫 Was direkt auf `main` verboten ist

- Direkte Pushes (`git push`) – nur über PR
- Force Pushes (`git push --force`)
- Branch löschen

---

## ❓ Fragen

Bei Fragen zum Prozess oder zu den Regeln: Andreas Klippenstein (andreas.klippenstein@batterydamageservice.de)
