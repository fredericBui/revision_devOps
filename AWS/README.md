# Fiche de Révision : AWS, Terraform et Services Gratuits

---

## 1. Introduction
Amazon Web Services (AWS) est une plateforme de services cloud fournie par Amazon. Elle propose une large gamme de services, allant de l’hébergement d’applications aux bases de données, en passant par le stockage et l’intelligence artificielle.

AWS permet aux entreprises de déployer des infrastructures scalables, sécurisées et économiques, avec une tarification basée sur la consommation. Il existe également un **niveau gratuit (AWS Free Tier)** qui permet d’utiliser certains services gratuitement, avec des limites.

Terraform est un outil d’Infrastructure as Code (IaC) permettant d’automatiser la gestion des ressources AWS à l’aide de fichiers de configuration.

---

## 2. Services Clés (Inclus dans AWS Free Tier)

### a) Compute (Calcul)
- **EC2 (Elastic Compute Cloud)** : 750 heures/mois d’instance t2.micro ou t3.micro (Linux ou Windows) pendant 12 mois.
- **Lambda** : 1 million d’exécutions gratuites par mois.
- **ECS (Elastic Container Service)** : Gratuit pour l’orchestration, mais nécessite des instances EC2.
- **EKS (Elastic Kubernetes Service)** : Gratuit pour le contrôle plan, mais les nœuds nécessitent des instances EC2.

### b) Stockage et Base de Données
- **S3 (Simple Storage Service)** : 5 Go de stockage standard gratuits.
- **EBS (Elastic Block Store)** : 30 Go de volume SSD gratuits.
- **RDS (Relational Database Service)** : 750 heures/mois d’instance db.t3.micro pour MySQL, PostgreSQL, MariaDB.
- **DynamoDB** : 25 Go de stockage et 1 million de requêtes gratuites par mois.

### c) Réseaux et Sécurité
- **VPC (Virtual Private Cloud)** : Gratuit avec 1 NAT Gateway payante si nécessaire.
- **IAM (Identity and Access Management)** : Gratuit pour la gestion des accès.
- **CloudFront** : 1 To de transfert de données gratuits.
- **Route 53** : Facturation appliquée selon l’utilisation.

### d) Outils DevOps
- **CodeCommit** : 5 utilisateurs gratuits.
- **CodeBuild** : 100 minutes gratuites par mois.
- **CodeDeploy** : Gratuit pour les déploiements EC2 et Lambda.
- **CodePipeline** : 1 pipeline gratuit par mois.

### e) Monitoring et Sécurité
- **CloudWatch** : 1 million de métriques gratuites et 5 Go de logs.
- **CloudTrail** : Enregistrements d’activité gratuits pour 90 jours.
- **GuardDuty** : Essai gratuit de 30 jours.

---

## 3. Déploiement avec Terraform sur AWS Free Tier

### a) Installation de Terraform
```sh
wget https://releases.hashicorp.com/terraform/1.x.x/terraform_1.x.x_linux_amd64.zip
unzip terraform_1.x.x_linux_amd64.zip
sudo mv terraform /usr/local/bin/
terraform --version
```

### b) Configuration des Identifiants AWS
```sh
aws configure
# Saisir AWS Access Key et Secret Key
```

### c) Création d’une instance EC2 avec Terraform (Free Tier)
#### Fichier `main.tf`
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-12345678"  # Remplacer par une AMI Free Tier
  instance_type = "t2.micro"
  tags = {
    Name = "ServeurTerraform"
  }
}
```

- **Commande pour appliquer la configuration :**
```sh
terraform init
terraform apply -auto-approve
```

### d) Déploiement d’un bucket S3 avec Terraform (Free Tier)
#### Fichier `s3.tf`
```hcl
resource "aws_s3_bucket" "mon_bucket" {
  bucket = "mon-bucket-terraform"
  acl    = "private"
}
```
- **Commande pour créer le bucket :**
```sh
terraform apply -auto-approve
```

---

## 4. Bonnes Pratiques
- **Utiliser les services AWS Free Tier** pour tester sans coût.
- **Définir des alertes CloudWatch** pour éviter des dépassements de coût.
- **Automatiser les infrastructures** avec Terraform pour une gestion efficace.
- **Limiter les permissions IAM** pour la sécurité.
- **Supprimer les ressources non utilisées** pour éviter des coûts imprévus.

---

## 5. Ressources
- AWS Free Tier : [https://aws.amazon.com/free/](https://aws.amazon.com/free/)
- Documentation Terraform AWS : [https://registry.terraform.io/providers/hashicorp/aws/latest/docs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- Outils de coût AWS : [https://calculator.aws/](https://calculator.aws/)

---

Cette fiche vous offre une vue d'ensemble rapide et efficace sur AWS, Terraform et les services gratuits ! 🚀

