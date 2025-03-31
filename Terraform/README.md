# Fiche de Révision : Terraform

---

## 1. Introduction
Terraform est un outil d'infrastructure en tant que code (IaC) développé par HashiCorp. Il permet de définir, provisionner et gérer des infrastructures de manière déclarative à l'aide de fichiers de configuration.

---

## 2. Concepts Clés

### a) Provider
Un provider est un plugin qui permet à Terraform d'interagir avec un service cloud (AWS, Azure, GCP, etc.).

### b) Ressource
Une ressource représente un élément de l'infrastructure, comme une machine virtuelle, un réseau ou une base de données.

### c) Variable
Les variables permettent de paramétrer les configurations Terraform et d'améliorer leur réutilisabilité.

### d) État
Terraform conserve un état de l'infrastructure dans un fichier `terraform.tfstate` afin de suivre les modifications et garantir la cohérence.

### e) Module
Un module est un ensemble de fichiers Terraform réutilisables pour organiser et structurer le code.

---

## 3. Commandes de Base

### a) Initialisation
- **Initialiser un projet Terraform** : `terraform init`
- **Afficher les providers installés** : `terraform providers`

### b) Planification et Application
- **Vérifier les changements avant application** : `terraform plan`
- **Appliquer les modifications** : `terraform apply`
- **Détruire l'infrastructure** : `terraform destroy`

### c) Gestion de l'État
- **Afficher l'état actuel** : `terraform show`
- **Lister les ressources gérées** : `terraform state list`
- **Supprimer une ressource de l'état** : `terraform state rm resource_name`

---

## 4. Exemple de Configuration

### Fichier `main.tf` (Exemple sur AWS) :
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
}
```

### Commandes associées :
```sh
terraform init
terraform plan
terraform apply
```

---

## 5. Bonnes Pratiques
- Utiliser des **modules** pour organiser le code.
- Stocker l'état dans un **backend distant** (S3, Terraform Cloud, etc.) pour éviter les conflits.
- Utiliser des **variables** pour rendre le code plus flexible.
- Appliquer le principe **d'infrastructure immuable** en remplaçant les ressources au lieu de les modifier.

---

## 6. Ressources
- Documentation officielle : [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)
- Registry des modules : [https://registry.terraform.io/](https://registry.terraform.io/)

---

Cette fiche vous offre une vue d'ensemble rapide et efficace sur Terraform !

