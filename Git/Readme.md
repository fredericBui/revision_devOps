# Fiche de Révision : Git

---

## 1. Introduction
Git est un système de gestion de version distribué permettant de suivre les modifications apportées à un projet et de collaborer efficacement.

---

## 2. Configuration Initiale
### a) Installation de Git
- **Linux** : `sudo apt install git`
- **Mac** : `brew install git`
- **Windows** : Télécharger depuis [git-scm.com](https://git-scm.com/)

### b) Configuration de l’utilisateur
```sh
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

---

## 3. Commandes Git Essentielles
### a) Initialiser un dépôt Git
```sh
git init
```

### b) Cloner un dépôt existant
```sh
git clone <URL-du-repo>
```

### c) Vérifier l’état du dépôt
```sh
git status
```

### d) Ajouter des fichiers au suivi
```sh
git add <fichier>
# Ou pour tout ajouter
git add .
```

### e) Valider les modifications
```sh
git commit -m "Message du commit"
```

### f) Afficher l’historique des commits
```sh
git log
```

### g) Annuler des modifications
- **Avant un commit** :
```sh
git checkout -- <fichier>
```
- **Après un commit** :
```sh
git revert <ID-du-commit>
```

### h) Travailler avec des branches
- **Créer une nouvelle branche** :
```sh
git branch <nom-de-la-branche>
```
- **Basculer sur une branche** :
```sh
git checkout <nom-de-la-branche>
```
- **Créer et changer de branche** :
```sh
git checkout -b <nom-de-la-branche>
```
- **Fusionner une branche** :
```sh
git merge <nom-de-la-branche>
```
- **Supprimer une branche** :
```sh
git branch -d <nom-de-la-branche>
```

### i) Travailler avec un dépôt distant
- **Ajouter un dépôt distant** :
```sh
git remote add origin <URL-du-repo>
```
- **Pousser les modifications** :
```sh
git push origin <branche>
```
- **Récupérer les modifications** :
```sh
git pull origin <branche>
```

---

## 4. Bonnes Pratiques
- **Utiliser des messages de commit clairs et descriptifs.**
- **Faire des commits fréquents pour un meilleur suivi des changements.**
- **Utiliser des branches pour séparer les développements.**
- **Effectuer des pull requests et des revues de code avant de fusionner.**
- **Ne pas committer de fichiers sensibles (ex : `.env`, `node_modules`).**

---

## 5. Ressources
- Documentation officielle Git : [https://git-scm.com/doc](https://git-scm.com/doc)
- GitHub Learning Lab : [https://lab.github.com/](https://lab.github.com/)
- Git Cheat Sheet : [https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

---

Cette fiche vous offre une vue rapide et efficace sur l’utilisation de Git ! 🚀

