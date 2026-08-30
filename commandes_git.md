# Git — Mémo rapide

## 1. Vérifier l'état du dépôt

### `git status`
Affiche les fichiers modifiés, staged, non suivis et la branche actuelle.

```bash
git status
```

---

# 2. Configuration Git

### `git config --list`
Affiche toute la configuration Git.

```bash
git config --list
```

### `git config --global`
Configuration pour l'utilisateur actuel.

```bash
git config --global user.name "Alice"
git config --global user.email "alice@example.com"
```

### `git config --system`
Configuration pour tous les utilisateurs de la machine.

```bash
git config --system core.autocrlf true
```

### `git config --local`
Configuration uniquement pour le dépôt actuel.

```bash
git config --local user.name "Alice"
```

Priorité :

```text
local > global > system
```

---

# 3. Staging et reset

### `git reset HEAD <fichier>`
Retire un fichier de la staging area sans supprimer ses modifications.

```bash
git reset HEAD main.py
```

### `git reset HEAD`
Retire tous les fichiers de la staging area.

```bash
git reset HEAD
```

---

# 4. Commits

### `git commit -m "message"`
Commit les changements déjà staged.

```bash
git commit -m "Add login page"
```

### `git commit -a -m "message"`
Commit directement toutes les modifications des fichiers déjà suivis.

```bash
git commit -a -m "Fix bugs"
```

### `git commit --allow-empty -m "message"`
Crée un commit vide.

```bash
git commit --allow-empty -m "Start project"
```

### `git commit --no-edit`
Utilise le message du commit précédent sans ouvrir l'éditeur.

```bash
git commit --no-edit
```

### `git commit --amend --no-edit`
Ajoute les changements staged au dernier commit sans changer son message.

```bash
git commit --amend --no-edit
```

---

# 5. Historique

### `git log`
Affiche l'historique détaillé des commits.

```bash
git log
```

### `git log --oneline`
Affiche un historique compact.

```bash
git log --oneline
```

### `git log --author="Alice"`
Affiche les commits d'un auteur.

```bash
git log --author="Alice"
```

### `git log --since="2 weeks ago"`
Affiche les commits récents.

```bash
git log --since="2 weeks ago"
```

### `git log --graph`
Affiche l'historique sous forme de graphe.

```bash
git log --graph --oneline
```

---

# 6. Tags

### `git tag <tagname>`
Crée un tag léger.

```bash
git tag v1.0
```

### `git tag -a <tagname> -m "message"`
Crée un tag annoté.

```bash
git tag -a v1.0 -m "First release"
```

### `git tag <tagname> <commit-hash>`
Ajoute un tag à un commit précis.

```bash
git tag v1.0 a1b2c3d
```

### `git tag`
Liste tous les tags.

```bash
git tag
```

### `git show <tagname>`
Affiche les informations d'un tag.

```bash
git show v1.0
```

### `git push origin <tagname>`
Envoie un tag vers le dépôt distant.

```bash
git push origin v1.0
```

### `git tag -d <tagname>`
Supprime un tag local.

```bash
git tag -d v1.0
```

### `git push origin --delete tag <tagname>`
Supprime un tag distant.

```bash
git push origin --delete tag v1.0
```

### Déplacer un tag

```bash
git tag -f v1.0 <new-commit-hash>
git push --force origin v1.0
```

---

# 7. Stash

### `git stash`
Met temporairement de côté les modifications des fichiers suivis.

```bash
git stash
```

### `git stash push -m "message"`
Crée un stash avec un message.

```bash
git stash push -m "WIP: homepage redesign"
```

### `git stash -u`
Stash aussi les fichiers non suivis.

```bash
git stash -u
```

### `git stash list`
Liste tous les stash.

```bash
git stash list
```

### `git stash show`
Affiche un résumé du dernier stash.

```bash
git stash show
```

### `git stash apply`
Réapplique le dernier stash sans le supprimer.

```bash
git stash apply
```

### `git stash apply stash@{n}`
Réapplique un stash précis.

```bash
git stash apply stash@{1}
```

### `git stash pop`
Réapplique puis supprime le dernier stash.

```bash
git stash pop
```

### `git stash drop`
Supprime le dernier stash.

```bash
git stash drop
```

### `git stash clear`
Supprime tous les stash.

```bash
git stash clear
```

### `git stash branch <branchname>`
Crée une branche à partir d'un stash.

```bash
git stash branch feature-login
```

Par défaut, Git stash sauvegarde les fichiers suivis staged et unstaged.

Les fichiers untracked ne sont pas inclus sauf avec :

```bash
git stash -u
```

---

# 8. Différences

### `git diff`
Affiche les modifications non staged.

```bash
git diff
```

### `git diff --staged`
Affiche les modifications staged.

```bash
git diff --staged
```

### `git diff <commit1> <commit2>`
Compare deux commits.

```bash
git diff a1b2c3d e4f5g6h
```

---

# 9. Branches

### `git branch`
Liste les branches.

```bash
git branch
```

### `git branch <nom>`
Crée une nouvelle branche.

```bash
git branch hello-world-images
```

### `git checkout <branche>`
Change de branche.

```bash
git checkout hello-world-images
```

### `git switch <branche>`
Change de branche avec la syntaxe moderne.

```bash
git switch hello-world-images
```

### `git checkout -b <branche>`
Crée une branche et bascule dessus.

```bash
git checkout -b emergency-fix
```

### `git branch -d <branche>`
Supprime une branche déjà fusionnée.

```bash
git branch -d hello-world-images
```

### `git branch -D <branche>`
Force la suppression d'une branche non fusionnée.

```bash
git branch -D hello-world-images
```

### `git branch -m <ancien> <nouveau>`
Renomme une branche.

```bash
git branch -m old-name new-name
```

---

# 10. Merge

### `git merge <branche>`
Fusionne une branche dans la branche actuelle.

```bash
git merge feature-login
```

### `git merge --no-ff <branche>`
Force la création d'un merge commit.

```bash
git merge --no-ff feature-login
```

### `git merge --squash <branche>`
Regroupe les changements de la branche sans créer directement plusieurs commits.

```bash
git merge --squash feature-login
```

Puis :

```bash
git commit -m "Merge feature-login"
```

### `git merge --abort`
Annule un merge en cours.

```bash
git merge --abort
```

---

# 11. Dépôts distants

### `git clone <url>`
Clone un dépôt distant.

```bash
git clone https://github.com/user/repo.git
```

### `git fetch origin`
Télécharge les nouveautés du dépôt distant sans les fusionner.

```bash
git fetch origin
```

### `git pull`
Télécharge et fusionne les nouveautés distantes.

```bash
git pull
```

### `git push`
Envoie les commits locaux vers le dépôt distant.

```bash
git push
```

### `git push origin main`
Envoie la branche `main` vers `origin`.

```bash
git push origin main
```

---

# 12. `.gitignore`

Le fichier `.gitignore` indique les fichiers que Git ne doit pas suivre.

Exemple :

```gitignore
.env
__pycache__/
*.log
data/
```

---

# 13. Aide Git

### `git help <command>`
Affiche le manuel d'une commande.

```bash
git help commit
```

### `git <command> --help`
Même fonction.

```bash
git commit --help
```

### `git <command> -h`
Affiche une aide courte.

```bash
git commit -h
```

### `git help --all`
Liste toutes les commandes Git.

```bash
git help --all
```

### `git help -g`
Liste les guides Git.

```bash
git help -g
```

---

# 14. Workflow Git

```text
[Working Directory]
        |
     git add
        v
[Staging Area]
        |
   git commit
        v
[Local Repository]
        |
    git push
        v
[Remote Repository]
```

Pour récupérer les changements distants :

```text
Remote Repository
        |
   git fetch / git pull
        v
Local Repository
```

---

# 15. Termes importants

| Terme | Signification |
|---|---|
| Branch | Ligne de développement indépendante |
| Checkout | Changer de branche ou récupérer une version |
| Clone | Copier un dépôt distant en local |
| Commit | Enregistrer une version du projet |
| Conflict | Conflit entre deux modifications incompatibles |
| Fetch | Télécharger les nouveautés distantes sans fusion |
| Fork | Copie d'un dépôt dans un autre compte GitHub |
| HEAD | Référence vers le commit ou la branche actuelle |
| Index / Staging Area | Zone entre les fichiers de travail et le commit |
| Merge | Fusionner deux branches |
| Origin | Nom par défaut du dépôt distant principal |
| Pull | Fetch + intégration des changements |
| Push | Envoyer les commits locaux vers le remote |
| Rebase | Repositionner une série de commits sur une autre base |
| Remote | Dépôt distant |
| Repository | Projet suivi par Git |
| Stash | Stockage temporaire de modifications |
| Tag | Nom associé à un commit, souvent pour une version |
| Upstream | Dépôt ou branche distante de référence |
| Working Directory | Fichiers actuellement présents sur le disque |
