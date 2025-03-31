# Fiche de Révision : Jenkins et ses Agents

---

## 1. Introduction
Jenkins est un serveur d'intégration et de déploiement continu open-source permettant d'automatiser le cycle de développement logiciel. Il permet d'exécuter des tâches via des pipelines et peut être étendu grâce à des plugins.

Jenkins repose sur un modèle maître-agent, où un serveur central (maître) orchestre l'exécution des tâches sur des machines distantes (agents).

---

## 2. Concepts Clés

### a) Jenkins Master (Serveur Principal)
Le serveur Jenkins central qui gère :
- L'interface utilisateur.
- La gestion des builds et des configurations.
- La distribution des tâches aux agents.

### b) Jenkins Agent
Une machine (physique ou virtuelle) qui exécute les tâches demandées par le maître. 

Les agents permettent de :
- Répartir la charge de travail.
- Exécuter des builds sur différentes plateformes.
- Isoler les environnements d'exécution.

### c) Pipeline Jenkins
Un pipeline est un script définissant une série d'étapes à exécuter dans un processus de CI/CD.

Deux types de pipelines :
- **Déclaratif** : syntaxe simplifiée basée sur `Jenkinsfile`.
- **Scripté** : syntaxe plus flexible en Groovy.

### d) Nœuds et Étiquettes
Les agents peuvent être regroupés sous des étiquettes pour mieux gérer l'affectation des builds.

---

## 3. Commandes et Configuration

### a) Installation de Jenkins
- **Via Docker** :
```sh
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
```
- **Sur Ubuntu** :
```sh
sudo apt update && sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### b) Gestion des Agents

#### 1. Démarrage d’un agent via Docker
Dans Jenkins :
1. Aller dans **Gérer Jenkins > Gérer les nœuds**.
2. Ajouter un nouvel agent et configurer les paramètres (nom, étiquette, mode d'exécution).
3. Lancer l'agent avec Docker :
```sh
docker run -d --name jenkins-agent \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/inbound-agent \
  -url <JENKINS_URL> \
  <SECRET> <AGENT_NAME>
```

### c) Exemple de Pipeline

#### Fichier `Jenkinsfile`
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Compilation du code...'
            }
        }
        stage('Test') {
            steps {
                echo 'Exécution des tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Déploiement en production...'
            }
        }
    }
}
```

---

## 4. Bonnes Pratiques
- Sécuriser Jenkins en activant l’authentification et en limitant les accès aux agents.
- Utiliser des **pipelines déclaratifs** pour plus de lisibilité.
- Stocker les **Jenkinsfiles** dans le dépôt Git pour assurer le suivi des changements.
- Utiliser des **agents spécialisés** selon les besoins (Docker, Windows, Linux).
- Nettoyer régulièrement les anciens builds et artefacts pour éviter l’encombrement du serveur.

---

## 5. Ressources
- Documentation officielle : [https://www.jenkins.io/doc/](https://www.jenkins.io/doc/)
- Jenkins Plugins : [https://plugins.jenkins.io/](https://plugins.jenkins.io/)

---

Cette fiche vous offre une vue d'ensemble rapide et efficace sur Jenkins et ses agents ! 🚀

