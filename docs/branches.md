# Branches Git

> Les branches sont la vraie superpuissance de Git. Elles permettent de travailler en parallèle sans risque.

---

## Concept

Une branche est un **pointeur léger** vers un commit. Créer une branche ne copie pas les fichiers — c'est juste un nouveau curseur dans l'historique.

```
main:    A → B → C
                  ↘
feature:           D → E
```

---

## Créer et naviguer

```bash
git branch                      # lister les branches locales
git branch -a                   # lister toutes les branches (locales + distantes)
git branch feat/login           # créer une branche
git checkout feat/login         # basculer sur une branche
git checkout -b feat/login      # créer ET basculer (raccourci)
git switch feat/login           # alternative moderne à checkout
git switch -c feat/login        # créer ET basculer (syntaxe moderne)
```

---

## Fusionner des branches

```bash
git merge feat/login            # fusionner feat/login dans la branche courante
git merge --no-ff feat/login    # forcer un commit de merge (conserve l'historique)
git merge --abort               # annuler un merge en cours
```

### Résoudre un conflit

Quand Git ne peut pas fusionner automatiquement, il marque les conflits :

```
<<<<<<< HEAD
code de la branche actuelle
=======
code de la branche à merger
>>>>>>> feat/login
```

1. Ouvrir le fichier en conflit
2. Choisir le bon code (ou combiner les deux)
3. Supprimer les marqueurs `<<<<<<<`, `=======`, `>>>>>>>`
4. `git add fichier_conflit.txt`
5. `git commit`

---

## Rebase — réécrire l'historique

```bash
git rebase main                 # rejouer ses commits sur la pointe de main
git rebase -i HEAD~3            # rebase interactif sur les 3 derniers commits
```

> ⚠️ Ne jamais rebaser des branches déjà poussées et partagées.

**Merge vs Rebase :**
| | Merge | Rebase |
|---|---|---|
| Historique | Préserve les divergences | Linéarise |
| Sécurité | Sûr même sur branches partagées | À éviter sur branches publiques |
| Lisibilité | Moins linéaire | Plus propre |

---

## Supprimer des branches

```bash
git branch -d feat/login        # supprimer une branche mergée
git branch -D feat/login        # forcer la suppression
git push origin --delete feat/login  # supprimer sur le remote
```

---

## Stratégies de branches courantes

### GitHub Flow (simple, recommandé pour débuter)
```
main ← toujours déployable
feat/xxx ← courte durée, PR vers main
```

### Git Flow (projets avec releases)
```
main ← production
develop ← intégration
feature/* ← nouvelles fonctionnalités
release/* ← préparation de version
hotfix/* ← corrections urgentes
```

---

## Ressources

- [learngitbranching.js.org](https://learngitbranching.js.org/) — visualiser les branches en interactif
- [git-scm.com/book ch.3](https://git-scm.com/book/fr/v2/Les-branches-avec-Git-Les-branches-en-bref)
