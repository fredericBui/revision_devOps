# Fiche de Révision : SonarQube et ses Agents

---

## 1. Introduction
SonarQube est une plateforme open-source d'analyse de code permettant d'améliorer la qualité logicielle en détectant les bugs, vulnérabilités et mauvaises pratiques. Il s'intègre facilement dans des pipelines CI/CD comme Jenkins, GitLab CI, et GitHub Actions.

SonarQube fonctionne avec des **agents d'analyse** qui collectent des métriques à partir du code source et envoient les résultats au serveur SonarQube pour analyse et reporting.

---

## 2. Concepts Clés

### a) SonarQube Server
Le serveur central SonarQube qui :
- Stocke et analyse les résultats des scans de code.
- Fournit une interface web pour visualiser les rapports.
- Permet d'appliquer des règles de qualité et de sécurité.

### b) SonarQube Scanner (Agent d'Analyse)
Un outil utilisé pour analyser le code et envoyer les résultats au serveur SonarQube.

Il existe plusieurs types de scanners selon l'environnement :
- **SonarScanner CLI** : Utilisé en ligne de commande.
- **Scanner Maven** : Intégré dans les projets Maven.
- **Scanner Gradle** : Pour les projets Gradle.
- **Scanner pour Jenkins** : Intégré à Jenkins via un plugin.

### c) Quality Gates (Portes de Qualité)
Un ensemble de règles définissant si un projet respecte les standards de qualité avant d’être validé.

### d) Quality Profiles
Des ensembles de règles de qualité spécifiques aux langages de programmation utilisés pour analyser le code.

---

## 3. Installation et Configuration

### a) Installation de SonarQube Server
- **Via Docker** :
```sh
docker run -d --name sonarqube \
  -p 9000:9000 \
  -e SONARQUBE_JDBC_URL=jdbc:postgresql://db:5432/sonarqube \
  -e SONARQUBE_JDBC_USERNAME=sonar \
  -e SONARQUBE_JDBC_PASSWORD=sonar \
  sonarqube:lts-community
```

- **Sur Ubuntu** :
```sh
sudo apt update && sudo apt install sonarqube -y
sudo systemctl start sonarqube
sudo systemctl enable sonarqube
```

### b) Installation d’un SonarScanner (Agent d’Analyse)
#### 1. Scanner CLI
- **Installation** :
```sh
wget -O sonarscanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-latest.zip
unzip sonarscanner.zip -d /opt/sonar-scanner
export PATH=$PATH:/opt/sonar-scanner/bin
```
- **Exécution d’une analyse** :
```sh
sonar-scanner \
  -Dsonar.projectKey=mon-projet \
  -Dsonar.sources=src \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=mon_token
```

#### 2. Scanner Maven
Ajout dans `pom.xml` :
```xml
<plugin>
  <groupId>org.sonarsource.scanner.maven</groupId>
  <artifactId>sonar-maven-plugin</artifactId>
  <version>3.9.1.2184</version>
</plugin>
```
- **Exécution de l’analyse** :
```sh
mvn clean verify sonar:sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=mon_token
```

---

## 4. Intégration avec Jenkins

### a) Installation du Plugin SonarQube
1. Aller dans **Gérer Jenkins > Gérer les plugins**.
2. Rechercher **SonarQube Scanner** et l’installer.
3. Configurer SonarQube dans **Gérer Jenkins > Configurer le système**.

### b) Exemple de Pipeline avec SonarQube

#### Fichier `Jenkinsfile`
```groovy
pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
```

---

## 5. Bonnes Pratiques
- Configurer des **Quality Gates** pour imposer des critères de qualité.
- Exécuter des analyses SonarQube à chaque **commit**.
- Utiliser des **Tokens d’authentification** au lieu de mots de passe.
- Nettoyer régulièrement les anciens projets pour éviter l’encombrement du serveur.

---

## 6. Ressources
- Documentation officielle : [https://docs.sonarqube.org/](https://docs.sonarqube.org/)
- Plugins SonarQube : [https://docs.sonarqube.org/latest/extend/plugins/](https://docs.sonarqube.org/latest/extend/plugins/)

---

Cette fiche vous offre une vue d'ensemble rapide et efficace sur SonarQube et ses agents ! 🚀

