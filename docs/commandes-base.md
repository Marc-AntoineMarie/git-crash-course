# Commandes Git — Bases

> Les commandes essentielles pour démarrer avec Git au quotidien.

---

## Initialisation

```bash
git init                    # initialiser un repo dans le dossier courant
git clone <url>             # cloner un repo distant en local
git clone <url> mon-dossier # cloner dans un dossier spécifique
```

---

## Configuration (à faire une fois)

```bash
git config --global user.name "Ton Nom"
git config --global user.email "toi@example.com"
git config --global core.editor "code --wait"  # VS Code comme éditeur
git config --list                               # voir toute la config
```

---

## Inspecter l'état du repo

```bash
git status              # voir les fichiers modifiés / stagés / non suivis
git diff                # voir les modifications non stagées
git diff --staged       # voir les modifications stagées (prêtes à commiter)
git log                 # historique complet
git log --oneline       # historique condensé (1 ligne par commit)
git log --oneline --graph --all  # arbre de branches visuel
```

---

## Stager et commiter

```bash
git add fichier.txt     # stager un fichier spécifique
git add .               # stager tous les changements du dossier courant
git add -p              # stager interactivement (morceau par morceau)

git commit -m "feat: ajouter la page d'accueil"
git commit --amend      # modifier le dernier commit (message ou contenu)
```

---

## Mettre des changements de côté

```bash
git stash               # mettre les modifications en attente
git stash pop           # récupérer les modifications mises en attente
git stash list          # voir toutes les stashs
git stash drop          # supprimer la dernière stash
```

---

## Annuler des changements

```bash
git restore fichier.txt         # annuler les modifications non stagées
git restore --staged fichier.txt # déstaguer un fichier
git revert <hash>               # créer un commit qui annule un commit passé
git reset --soft HEAD~1         # défaire le dernier commit (garde les modifs)
```

> ⚠️ Éviter `git reset --hard` sur des commits déjà poussés — cela réécrit l'historique public.

---

## Inspecter l'historique

```bash
git show <hash>                 # voir le détail d'un commit
git blame fichier.txt           # voir qui a modifié chaque ligne
git log --author="Prénom"       # filtrer par auteur
git log --since="2 weeks ago"   # filtrer par date
```

---

## Ressources complémentaires

- [git-scm.com/docs](https://git-scm.com/docs) — documentation officielle
- [ohshitgit.com/fr](https://ohshitgit.com/fr) — corriger les erreurs courantes
