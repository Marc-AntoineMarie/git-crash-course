# Collaboration avec Git & GitHub

> Git est local. GitHub est la couche sociale. Ensemble, ils permettent à des milliers de personnes de travailler sur le même code.

---

## Remotes — travailler avec un serveur

```bash
git remote -v                           # voir les remotes configurés
git remote add origin <url>             # ajouter un remote appelé "origin"
git remote add upstream <url>           # ajouter l'original (pour les forks)
git remote remove origin                # supprimer un remote
```

---

## Push & Pull

```bash
git push origin main                    # envoyer la branche main sur GitHub
git push -u origin feat/login           # push + définir le remote par défaut
git push --force-with-lease             # push forcé (plus sûr que --force)

git pull origin main                    # récupérer ET merger
git fetch origin                        # récupérer SANS merger (inspecter d'abord)
git pull --rebase origin main           # récupérer + rebaser ses commits dessus
```

> **Bonne pratique :** `git fetch` + `git log origin/main` avant de `git pull` pour voir ce qui arrive.

---

## Fork & Pull Request — le workflow open-source

```
Repo original (upstream)
        ↓  fork
Ton fork sur GitHub (origin)
        ↓  clone
Ta machine locale
```

### Étapes complètes

```bash
# 1. Cloner ton fork
git clone https://github.com/toi/git-crash-course.git
cd git-crash-course

# 2. Ajouter l'upstream
git remote add upstream https://github.com/owner/git-crash-course.git

# 3. Créer une branche
git checkout -b feat/ajouter-git-stash

# 4. Coder, puis commiter
git add docs/commandes-base.md
git commit -m "feat: ajouter section git stash"

# 5. Synchroniser avec l'upstream avant de pousser
git fetch upstream
git rebase upstream/main

# 6. Pousser sur son fork
git push origin feat/ajouter-git-stash

# 7. Ouvrir la Pull Request sur GitHub (bouton vert)
```

---

## Pull Request — bonnes pratiques

Une bonne PR :
- A un **titre clair** (`feat: ajouter commande git stash`)
- A une **description** : pourquoi ce changement ? qu'est-ce qui change ?
- Est **petite et ciblée** — une PR = une fonctionnalité
- Passe les **checks automatiques** (CI, linting)
- N'a **pas de conflits** avec la branche cible

---

## Code Review — lire et commenter une PR

- Commenter une ligne spécifique avec une suggestion
- Approuver avec "Approve" ou demander des changements avec "Request changes"
- Ne jamais merger sa propre PR sans review (sauf projet solo)

---

## Synchroniser son fork avec l'upstream

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

## Tags — marquer une version

```bash
git tag v1.0.0                          # créer un tag léger
git tag -a v1.0.0 -m "Version 1.0.0"   # tag annoté (recommandé)
git push origin v1.0.0                  # pousser le tag
git push origin --tags                  # pousser tous les tags
```

---

## Ressources

- [docs.github.com — Pull Requests](https://docs.github.com/fr/pull-requests)
- [conventionalcommits.org/fr](https://www.conventionalcommits.org/fr)
- [git-scm.com/book ch.5](https://git-scm.com/book/fr/v2/Git-distribué-Contribution-à-un-projet)
