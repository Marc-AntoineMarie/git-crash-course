# git-crash-course

> Un wiki collaboratif en Markdown — cheatsheet Git de la communauté.
> Créé pour le cours "Introduction à Git" · Contributions bienvenues !

![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![PRs](https://img.shields.io/badge/PRs-welcome-orange.svg)

---

## Table des matières

- [git-crash-course](#git-crash-course)
  - [Table des matières](#table-des-matières)
  - [À propos](#à-propos)
  - [Structure du projet](#structure-du-projet)
  - [Comment contribuer](#comment-contribuer)
  - [Commandes de base](#commandes-de-base)
  - [Ressources](#ressources)

---

## À propos

Ce repo est un support pédagogique pour apprendre Git en pratiquant.  
Chaque étudiant peut contribuer en ajoutant une commande, en corrigeant une typo, ou en améliorant la doc — exactement comme dans un vrai projet open-source.

**Ce projet illustre :**
- la gestion de branches (`git branch`, `git checkout`)
- le workflow Pull Request
- la revue de code collaborative
- les bonnes pratiques de commit

---

## Structure du projet

```
git-crash-course/
├── README.md                        ← vous êtes ici
├── CONTRIBUTING.md                  ← comment contribuer
├── CODE_OF_CONDUCT.md               ← règles de bonne conduite
├── CHANGELOG.md                     ← historique des versions
├── .gitignore                       ← fichiers exclus du suivi
├── docs/
│   ├── commandes-base.md            ← init, add, commit, status...
│   ├── branches.md                  ← branch, checkout, merge...
│   └── collaboration.md             ← remote, push, pull, PR...
└── examples/
    └── gitignore-templates/
        ├── python.gitignore
        ├── node.gitignore
        └── macos.gitignore
```

---

## Comment contribuer

1. **Fork** ce repo sur GitHub
2. **Clone** ton fork localement
3. Crée une **branche** : `git checkout -b feat/ma-contribution`
4. Fais tes modifications
5. **Commit** : `git commit -m "feat: ajouter commande git stash"`
6. **Push** : `git push origin feat/ma-contribution`
7. Ouvre une **Pull Request** sur GitHub

→ Voir [CONTRIBUTING.md](./CONTRIBUTING.md) pour les détails.

---

## Commandes de base

```bash
git init                    # initialiser un nouveau repo
git  <url>             # cloner un repo existant
git status             clone     # voir l'état des fichiers
git add <fichier>           # stager un fichier
git add .                   # stager tous les changements
git commit -m "message"     # créer un commit
git log --oneline --graph   # visualiser l'historique
git push origin main        # envoyer sur GitHub
git pull origin main        # récupérer les changements
```

---

## Ressources

| Ressource | Description |
|---|---|
| [Pro Git (gratuit)](https://git-scm.com/book/fr) | Le livre de référence, en français |
| [learngitbranching.js.org](https://learngitbranching.js.org/) | Visualiser les branches interactivement |
| [git-scm.com/docs](https://git-scm.com/docs) | Documentation officielle |
| [ohshitgit.com](https://ohshitgit.com/fr) | Réparer les erreurs courantes |
| [conventionalcommits.org](https://www.conventionalcommits.org/fr) | Convention de nommage des commits |

---

> **Maintenu par** : [Marc-Antoine] · Cours Git 2026
> **Licence** : MIT
