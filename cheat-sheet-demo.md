# 🎤 CHEAT SHEET DÉMO LIVE — Cours Git 15 min
# À garder ouvert dans un second onglet terminal pendant la présentation

# ══════════════════════════════════════════════════════════════
# AVANT DE COMMENCER (setup à faire avant que la classe arrive)
# ══════════════════════════════════════════════════════════════

# 1. Cloner le repo de cours
git clone https://github.com/TON-PSEUDO/git-crash-course.git
cd git-crash-course

# 2. Vérifier que tout est propre
git status
git log --oneline

# 3. Agrandir la police du terminal (min. 18pt pour que la salle voie)
# 4. Ouvrir GitHub dans le navigateur sur la page du repo (onglet prêt)
# 5. Ouvrir VS Code sur le repo (si tu montres un éditeur)

# ══════════════════════════════════════════════════════════════
# SLIDE 3 — Repo, commit, historique  (~1,5 min)
# ══════════════════════════════════════════════════════════════

# 💬 Dit : "Regardez — je pars de zéro."
mkdir demo-git && cd demo-git
git init
# 💬 "Un dossier .git vient d'être créé — c'est le repo."

echo "# Mon super projet" > README.md
git status
# 💬 "Le fichier est 'untracked' — Git le voit mais ne le suit pas encore."

git add README.md
git status
# 💬 "Maintenant il est dans la staging area — prêt à être photographié."

git commit -m "feat: initialiser le projet"
git log --oneline
# 💬 "Premier commit. Vous voyez le hash SHA-1 — c'est l'empreinte unique."

# ══════════════════════════════════════════════════════════════
# SLIDE 4 — Les 3 zones  (~1,5 min)
# ══════════════════════════════════════════════════════════════

echo "Bonjour Git !" >> README.md
git status
# 💬 "Modified → Working Directory. Git a détecté le changement."

git diff
# 💬 "Le + en vert = ligne ajoutée. Le - en rouge = ligne supprimée."

git add README.md
git diff --staged
# 💬 "Maintenant c'est dans la Staging Area. On inspecte avant de commiter."

git commit -m "docs: ajouter message de bienvenue"
git log --oneline
# 💬 "2 commits. L'historique se construit."

# ══════════════════════════════════════════════════════════════
# SLIDE 5 — Branches  (~1 min)
# ══════════════════════════════════════════════════════════════

git checkout -b feature/login
# 💬 "Je crée une branche. main reste intact."

echo "# Page de connexion" > login.md
git add login.md
git commit -m "feat: ajouter page de connexion"

git log --oneline --graph --all
# 💬 "Voyez l'arbre — main et feature/login divergent."

# ══════════════════════════════════════════════════════════════
# SLIDE 6 — Merge & conflits  (~1 min)
# ══════════════════════════════════════════════════════════════

git checkout main
git merge feature/login
# 💬 "Fast-forward merge — aucun conflit car main n'a pas bougé."

git log --oneline --graph
# 💬 "Les commits de feature/login sont maintenant dans main."

# ── Montrer un conflit (optionnel, si temps) ──────────────────
git checkout -b conflict-demo
echo "Version A de main" > conflit.md
git add conflit.md && git commit -m "feat: version A"

git checkout main
echo "Version B de feature" > conflit.md
git add conflit.md && git commit -m "feat: version B"

git merge conflict-demo
# 💬 "CONFLICT ! Git ne sait pas choisir — à nous de décider."
cat conflit.md
# Résoudre manuellement, puis :
# git add conflit.md && git commit
git merge --abort   # si on veut juste montrer sans résoudre

# ══════════════════════════════════════════════════════════════
# SLIDE 8 — Pull Request (démo principale ~2 min)
# ══════════════════════════════════════════════════════════════
# 💬 "On passe maintenant sur le vrai repo du cours."

cd /path/to/git-crash-course

git checkout -b feat/ajouter-git-cherry-pick
echo "" >> docs/commandes-base.md
echo "## Cherry-pick" >> docs/commandes-base.md
echo "" >> docs/commandes-base.md
echo '```bash' >> docs/commandes-base.md
echo "git cherry-pick <hash>  # appliquer un commit spécifique d'une autre branche" >> docs/commandes-base.md
echo '```' >> docs/commandes-base.md

git add docs/commandes-base.md
git status
git diff --staged

git commit -m "feat: ajouter la commande git cherry-pick"
git log --oneline

git push origin feat/ajouter-git-cherry-pick
# 💬 "Push. GitHub va afficher le bouton 'Compare & pull request'."

# → BASCULER SUR LE NAVIGATEUR
# → Montrer : bouton vert "Compare & pull request"
# → Remplir le titre : "feat: ajouter la commande git cherry-pick"
# → Montrer l'onglet "Files changed" (diff visuel)
# → Montrer comment laisser un commentaire sur une ligne
# → Cliquer "Create pull request" (ne pas merger devant la classe)

# ══════════════════════════════════════════════════════════════
# SLIDE 9 — Stash, log, blame  (~1 min)
# ══════════════════════════════════════════════════════════════

echo "modification en cours..." >> README.md
git stash
# 💬 "J'avais des modifications non terminées — stash les met de côté."
git status
# 💬 "Repo propre. Je peux switcher de branche sans perdre mon travail."
git stash pop
# 💬 "Et je les récupère."

git log --oneline --graph --all
git blame README.md
# 💬 "Chaque ligne, son auteur, son commit, sa date."

# ══════════════════════════════════════════════════════════════
# SLIDE 10 — .gitignore & bonnes pratiques  (~1 min)
# ══════════════════════════════════════════════════════════════

cat .gitignore
# 💬 "Ces fichiers ne seront JAMAIS dans le repo."
# 💬 "La règle d'or : jamais de .env, jamais de mot de passe."

# Montrer le CONTRIBUTING.md pour la convention de commits
cat CONTRIBUTING.md | head -60

# ══════════════════════════════════════════════════════════════
# COMMANDES DE SECOURS (si quelque chose se passe mal)
# ══════════════════════════════════════════════════════════════

git status               # toujours commencer par là
git log --oneline        # voir où on en est
git checkout main        # revenir sur main si perdu
git merge --abort        # annuler un merge en cours
git stash                # mettre de côté si état sale
git restore .            # annuler toutes les modifications non stagées

# ══════════════════════════════════════════════════════════════
# NOTES ORATEUR — une ligne par slide
# ══════════════════════════════════════════════════════════════

# S1  Accroche   → Question à la salle, pause 3 sec, laisser les mains lever
# S2  Contexte   → Anecdote : "Linus Torvalds a écrit Git en 10 jours, plus vite que certains projets de fin d'année"
# S3  Commit     → Insister : "Le hash c'est comme un numéro de reçu — si quelqu'un modifie un fichier, le hash change"
# S4  3 zones    → Analogie cuisine : "Working = frigo, Staging = assiette, Repo = table des invités"
# S5  Branches   → "Imaginez que vous écrivez un roman — vous testez une fin alternative sans détruire l'original"
# S6  Merge      → "Le conflit n'est PAS une erreur, c'est Git qui vous demande de prendre une décision humaine"
# S7  GitHub     → "GitHub c'est comme Google Drive, mais pour le code, avec un historique parfait de tout"
# S8  PR         → DÉMO LIVE — prendre son temps, zoom sur le bouton vert
# S9  Avancé     → "git blame semble agressif comme nom, mais c'est juste 'qui a écrit ça et pourquoi'"
# S10 .gitignore → "Un stagiaire chez Samsung a commité des clés AWS sur GitHub. 6 000 $ de frais en 1 nuit."
# S11 Récap      → "Ces 5 commandes = 90% de votre usage quotidien pendant les 6 prochains mois"
