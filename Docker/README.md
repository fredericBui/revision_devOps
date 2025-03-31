# Fiche de Révision : Docker

---

## 1. Introduction 
Docker est une plateforme permettant de développer, expédier et exécuter des applications dans des conteneurs. Un conteneur est une unité logicielle standard qui regroupe le code et toutes ses dépendances afin d'assurer un fonctionnement rapide et fiable dans n'importe quel environnement.

---

## 2. Concepts Clés

### a) Image 
Une image Docker est un modèle immuable contenant tout le nécessaire pour exécuter une application (code, bibliothèques, variables d'environnement, etc.).

### b) Conteneur 
Un conteneur est une instance exécutable d'une image Docker. Il est isolé du système hôte.

### c) Dockerfile 
Un fichier texte contenant une suite d'instructions permettant de construire une image Docker.

### d) Registry 
Un référentiel d'images Docker, comme Docker Hub ou une registry privée.

### e) Volume 
Un volume permet de persister les données des conteneurs.

---

## 3. Commandes de Base

### a) Gestion des Images
- **Lister les images** : `docker images`
- **Construire une image** : `docker build -t nom_image .`
- **Supprimer une image** : `docker rmi id_image`

### b) Gestion des Conteneurs
- **Lister les conteneurs actifs** : `docker ps`
- **Lister tous les conteneurs** : `docker ps -a`
- **Exécuter un conteneur** : `docker run -d -p 8080:80 --name mon_conteneur nom_image`
- **Arrêter un conteneur** : `docker stop id_conteneur`
- **Supprimer un conteneur** : `docker rm id_conteneur`

### c) Gestion des Volumes
- **Lister les volumes** : `docker volume ls`
- **Créer un volume** : `docker volume create nom_volume`
- **Monter un volume** : `docker run -v nom_volume:/chemin/dans/conteneur nom_image`

---

## 4. Docker Compose

Docker Compose permet de définir et de gérer des applications multi-conteneurs.

### Fichier `docker-compose.yml` (Exemple) :
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: exemple
```

### Commandes utiles :
- **Démarrer les services** : `docker-compose up -d`
- **Arrêter les services** : `docker-compose down`
- **Afficher les logs** : `docker-compose logs`

---

## 5. Bonnes Pratiques
- Minimiser la taille des images en utilisant des images de base légères (`alpine`, `slim`).
- Utiliser `.dockerignore` pour exclure les fichiers inutiles.
- Garder les conteneurs et images propres (`docker system prune`).
- Sécuriser les accès aux registres et éviter de stocker des mots de passe en clair.

---

## 6. Ressources
- Documentation officielle : [https://docs.docker.com/](https://docs.docker.com/)
- Docker Hub : [https://hub.docker.com/](https://hub.docker.com/)

---

Avec cette fiche, vous avez une vue d'ensemble rapide et efficace sur Docker !

