# Git Collaboration Labs

Projet pédagogique progressif consacré à Git local, à la synchronisation avec GitHub et à la collaboration. Les manipulations sont conçues pour **Windows**, **Visual Studio Code** et **Git Bash**.

## Objectif du projet

À la fin des quatre laboratoires, l'apprenant devra être capable de :

- distinguer Git, qui gère localement les versions d'un projet, de GitHub, qui héberge et facilite la collaboration autour d'un dépôt distant ;
- créer, inspecter et documenter un dépôt Git ;
- sélectionner des modifications, créer des commits logiques et lire l'historique ;
- synchroniser correctement une branche locale avec un dépôt distant ;
- créer des branches, les fusionner et résoudre un conflit textuel ;
- collaborer au moyen d'issues, de branches, de pull requests et de revues de code ;
- diagnostiquer un push refusé sans employer automatiquement une commande risquée ;
- protéger les secrets, les données et les fichiers qui ne doivent pas être versionnés.

## Prérequis

- Windows 10 ou 11 ;
- Git installé ;
- Visual Studio Code installé ;
- un terminal Git Bash ;
- un compte GitHub à partir du Lab 2 ;
- aucune connaissance avancée en programmation.

Vérifier l'installation dans Git Bash :

```bash
git --version
```

Un numéro de version doit apparaître, par exemple `git version 2.x.x.windows.x`.

## Structure générale

```text
git-collaboration-labs/
├── README.md
├── .gitignore                         # créé pendant la progression
└── labs/
    ├── 01_fondamentaux_git.md
    ├── 02_depot_distant_et_synchronisation.md
    ├── 03_branches_et_conflits.md
    └── 04_collaboration_github.md
```

Les fichiers sont ajoutés progressivement. Chaque nouveau laboratoire reprend l'état obtenu dans le précédent afin de former une histoire cohérente autour de `mini-projet-data`.

## Les quatre laboratoires

| Laboratoire | Rôle | Compétence principale |
|---|---|---|
| 1 — Fondamentaux de Git en local | Construire l'historique du projet fictif `mini-projet-data` | Passer correctement de la modification au commit |
| 2 — Dépôt distant et synchronisation | Relier le dépôt à GitHub et traiter un push refusé | Comprendre `main`, `origin/main`, `fetch`, `pull` et `push` |
| 3 — Branches, fusions et conflits | Développer en parallèle et résoudre un conflit reproductible | Utiliser des branches sans confondre divergence et conflit textuel |
| 4 — Collaboration professionnelle sur GitHub | Simuler le travail d'Alice et Bob autour d'une pull request | Appliquer un flux de collaboration complet avec revue de code |

## Progression recommandée

1. Lire les objectifs et les concepts du laboratoire courant.
2. Exécuter les commandes une par une dans Git Bash.
3. Vérifier le dossier courant avant toute opération.
4. Comparer la sortie obtenue avec le résultat attendu.
5. Effectuer l'exercice sans recopier mécaniquement la manipulation guidée.
6. Transmettre les sorties demandées pour validation.
7. Passer au laboratoire suivant uniquement lorsque les vérifications sont satisfaisantes.

## Précautions avant une commande Git

Avant une opération importante, vérifier autant que possible :

```bash
pwd
git status
git branch --show-current
git remote -v
```

- `pwd` évite de modifier le mauvais projet.
- `git status` décrit l'état des fichiers et de la zone de préparation.
- `git branch --show-current` indique la branche active.
- `git remote -v` montre les dépôts distants configurés ; il devient surtout utile à partir du Lab 2.

Avant chaque commit :

- examiner les fichiers modifiés et non suivis ;
- vérifier qu'aucun mot de passe, jeton, fichier `.env` ou jeu de données confidentiel ne sera enregistré ;
- lire `git diff` et `git diff --staged` ;
- préparer seulement les fichiers appartenant à la même modification logique ;
- choisir un message court qui explique le changement.

Les commandes suivantes ne doivent jamais être exécutées mécaniquement :

```bash
git reset --hard
git clean -fd
git push --force
```

Elles peuvent supprimer des modifications ou réécrire un historique partagé. Une solution plus sûre doit être étudiée en premier.

## État de la progression

- [x] Structure et règles générales définies
- [x] Lab 1 — Fondamentaux de Git en local préparé
- [ ] Lab 1 — Exercice exécuté et validé
- [x] Lab 2 — Dépôt distant et synchronisation préparé
- [ ] Lab 2 — Exercice exécuté et validé
- [ ] Lab 3 — Branches, fusions et conflits
- [ ] Lab 4 — Collaboration professionnelle sur GitHub
