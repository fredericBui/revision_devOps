# Fiche de Révision : Ansible

---

## 1. Introduction
Ansible est un outil open-source d'automatisation informatique permettant la gestion de configuration, le déploiement d'applications et l'orchestration d'infrastructure. Il fonctionne sans agent et utilise SSH pour communiquer avec les machines cibles.

---

## 2. Concepts Clés

### a) Playbook
Un playbook est un fichier YAML contenant une liste de tâches à exécuter sur les hôtes cibles.

### b) Inventaire
L'inventaire est un fichier listant les machines cibles organisées en groupes.

### c) Module
Un module est une unité de travail réutilisable exécutée par Ansible pour effectuer une tâche spécifique (ex. : gestion des utilisateurs, configuration réseau, etc.).

### d) Rôle
Un rôle est une structure organisée permettant de réutiliser et de partager des tâches, variables et fichiers liés à une configuration spécifique.

### e) Variable
Les variables permettent de personnaliser l'exécution des playbooks en fonction des besoins.

---

## 3. Commandes de Base

### a) Exécution de commandes
- **Vérifier la connexion aux hôtes** : `ansible all -m ping`
- **Exécuter une commande sur les hôtes** : `ansible all -m command -a "uname -a"`

### b) Gestion des Playbooks
- **Exécuter un playbook** : `ansible-playbook playbook.yml`
- **Tester un playbook en mode check** : `ansible-playbook playbook.yml --check`
- **Utiliser un fichier d'inventaire spécifique** : `ansible-playbook -i inventory.ini playbook.yml`

---

## 4. Exemple de Playbook

### Fichier `playbook.yml` :
```yaml
- name: Installer et démarrer Nginx
  hosts: webservers
  become: yes
  tasks:
    - name: Installer Nginx
      apt:
        name: nginx
        state: present
    
    - name: Démarrer Nginx
      service:
        name: nginx
        state: started
```

### Commandes associées :
```sh
ansible-playbook -i inventory.ini playbook.yml
```

---

## 5. Bonnes Pratiques
- Utiliser des **rôles** pour organiser les configurations.
- Sécuriser les **variables sensibles** avec Ansible Vault.
- Utiliser des **handlers** pour redémarrer des services uniquement si nécessaire.
- Vérifier les changements avant application avec `--check`.
- Tester les playbooks sur un environnement de développement avant de les appliquer en production.

---

## 6. Ressources
- Documentation officielle : [https://docs.ansible.com/](https://docs.ansible.com/)
- Ansible Galaxy : [https://galaxy.ansible.com/](https://galaxy.ansible.com/)

---

Cette fiche vous offre une vue d'ensemble rapide et efficace sur Ansible !

