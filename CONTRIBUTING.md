# Guide de contribution

Merci de prendre le temps de contribuer !
Ce document explique comment participer à ce projet, étape par étape.

---

## Code de conduite

En participant à ce projet, tu acceptes de respecter notre [Code de Conduite](./CODE_OF_CONDUCT.md).

---

## Prérequis

- Git installé sur ta machine ([git-scm.com](https://git-scm.com))
- Un compte GitHub
- Un éditeur de texte (VS Code recommandé)

---

## Workflow de contribution

### 1. Fork le repo

Clique sur le bouton **Fork** en haut à droite de la page GitHub. 
Cela crée une copie du projet sur ton propre compte.

### 2. Clone ton fork

```bash
git clone https://github.com/<ton-pseudo>/git-crash-course.git
cd git-crash-course
```

### 3. Configure le remote upstream

```bash
git remote add upstream https://github.com/<owner>/git-crash-course.git
git remote -v  # vérifier les remotes
```

### 4. Crée une branche

Nomme ta branche de manière descriptive :

```bash
git checkout -b feat/ajouter-commande-stash
# ou
git checkout -b fix/typo-readme
# ou
git checkout -b docs/ameliorer-section-branches
```

**Convention de nommage des branches :**

| Préfixe | Usage |
|---|---|
| `feat/` | Nouvelle fonctionnalité ou contenu |
| `fix/` | Correction d'une erreur |
| `docs/` | Amélioration de la documentation |
| `chore/` | Maintenance, restructuration |

### 5. Fais tes modifications

Édite les fichiers concernés dans `docs/` ou `examples/`.

### 6. Vérifie tes changements

```bash
git status          # voir quels fichiers ont changé
git diff            # voir le détail des modifications
```

### 7. Commit

Suis la convention [Conventional Commits](https://www.conventionalcommits.org/fr) :

```bash
git add docs/commandes-base.md
git commit -m "feat: ajouter la commande git stash avec exemple"
```

**Format d'un bon message de commit :**
```
<type>: <description courte en impératif>

[Corps optionnel : pourquoi ce changement ?]

[Pied de page : références à des issues si besoin]
```

**Types acceptés :** `feat`, `fix`, `docs`, `chore`, `style`, `refactor`

### 8. Synchronise avec upstream

Avant de pousser, récupère les éventuels changements :

```bash
git fetch upstream
git rebase upstream/main
```

### 9. Push et Pull Request

```bash
git push origin feat/ajouter-commande-stash
```

Puis sur GitHub, clique **"Compare & pull request"**.

**Dans ta PR :**
- Titre clair (suit la convention de commit)
- Description : qu'est-ce qui change et pourquoi ?
- Screenshot si tu modifies la structure du projet

---

## Ce qu'on accepte

- ✅ Ajout de commandes Git avec explication et exemple
- ✅ Correction de fautes ou d'imprécisions
- ✅ Nouveaux templates `.gitignore`
- ✅ Traductions ou améliorations de la clarté
- ✅ Exemples concrets tirés de la pratique

## Ce qu'on n'accepte pas

- ❌ Contenu hors-sujet (non lié à Git)
- ❌ Copier-coller d'autres ressources sans attribution
- ❌ Commits avec des messages vagues (`fix`, `update`, `wip`)

---

## Revue de code

Toute PR est relue avant d'être mergée. Tu peux recevoir des commentaires — c'est normal et constructif !  
Réponds aux commentaires, pousse des corrections si nécessaire, et la PR sera mergée une fois approuvée.

---

Merci de contribuer à rendre ce projet meilleur pour tout le monde. 🚀
