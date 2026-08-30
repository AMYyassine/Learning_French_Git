# Commandes Git — Mémo

Ce fichier regroupe les commandes Git de base demandées.

---

## 1. `git status`

### Commande

```bash
git status
```

### Rôle

Affiche l'état actuel du dépôt Git.

Elle permet notamment de voir :

- les fichiers modifiés ;
- les fichiers non suivis (`untracked`) ;
- les fichiers ajoutés à la zone de staging ;
- la branche actuelle ;
- si la branche locale est en avance ou en retard sur la branche distante.

### Exemple

```bash
git status
```

À utiliser très souvent avant et après une opération Git.

---

# 2. `git config`

La commande `git config` permet de consulter ou modifier la configuration de Git.

## Voir la configuration

```bash
git config --list
```

---

## Configuration locale

```bash
git config --local
```

La configuration `--local` concerne uniquement le dépôt Git actuel.

Le fichier correspondant se trouve généralement dans :

```text
.git/config
```

Exemple :

```bash
git config --local user.name "Mon Nom"
```

---

## Configuration globale

```bash
git config --global
```

La configuration `--global` concerne tous les dépôts de l'utilisateur actuel.

Exemples :

```bash
git config --global user.name "Mon Nom"
git config --global user.email "monemail@example.com"
```

Vérification :

```bash
git config --global user.name
git config --global user.email
```

---

## Configuration système

```bash
git config --system
```

La configuration `--system` concerne tous les utilisateurs de la machine.

Elle nécessite généralement des droits administrateur.

Exemple :

```bash
git config --system core.autocrlf true
```

---

## Priorité des configurations

En cas de conflit :

```text
local > global > system
```

Donc une valeur définie avec `--local` remplace une valeur `--global`, qui elle-même remplace une valeur `--system`.

---

# 3. `git reset`

## Retirer un fichier de la zone de staging

Si un fichier a été ajouté avec :

```bash
git add nom_du_fichier.ext
```

on peut le retirer de la zone de staging avec :

```bash
git reset HEAD nom_du_fichier.ext
```

Exemple :

```bash
git reset HEAD main.py
```

Le fichier reste modifié sur le disque, mais il n'est plus dans la zone de staging.

---

## Plusieurs fichiers

```bash
git reset HEAD fichier1.py fichier2.py
```

---

## Tous les fichiers

```bash
git reset HEAD
```

Cela retire tous les fichiers de la zone de staging sans supprimer leurs modifications locales.

---

# 4. À propos de `.git/HEAD`

Dans un dépôt Git, le fichier :

```text
.git/HEAD
```

indique généralement la branche actuellement utilisée.

Par exemple :

```text
ref: refs/heads/main
```

Cependant, pour retirer un fichier du staging, on n'écrit généralement pas :

```bash
git reset ./git/HEAD nom_du_fichier.ext
```

La syntaxe correcte est :

```bash
git reset HEAD nom_du_fichier.ext
```

---

# Résumé rapide

```bash
# Voir l'état du dépôt
git status

# Voir toute la configuration
git config --list

# Configuration globale
git config --global user.name "Mon Nom"
git config --global user.email "monemail@example.com"

# Configuration système
git config --system ...

# Configuration du dépôt actuel
git config --local ...

# Retirer un fichier du staging
git reset HEAD nom_du_fichier.ext

# Retirer tous les fichiers du staging
git reset HEAD
```
