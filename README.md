# gitea-ansible-deployment

Déploiement et configuration automatisés d'un serveur Gitea sur Ubuntu Server à l'aide d'Ansible et Docker.

## Table des matières

- [Technologies](#technologies)
- [Fonctionnalités](#fonctionnalités)
- [Prérequis](#prérequis)
- [Utilisation](#utilisation)
- [Auteur](#auteur)

## Technologies

- Système : Ubuntu Server
- Automatisation : Ansible
- Conteneurisation : Docker
- Orchestration : Docker Compose
- Reverse proxy : NGINX

## Fonctionnalités

- Configuration automatisée du serveur Ubuntu avec Ansible
- Installation et configuration de Docker et Docker Compose
- Déploiement de Gitea avec Docker Compose
- Utilisation de templates Jinja2 pour la configuration
- Sécurisation du serveur avec UFW et Ansible Vault
- Sauvegarde des données de Gitea
- Configuration du reverse proxy NGINX

## Prérequis

Pour déployer le projet, les outils suivants doivent être installés :

- Git
- Accès SSH à un serveur Ubuntu 
- Ansible

Installer la collection Ansible nécessaire :
```bash
ansible-galaxy collection install community.docker
```

Le serveur cible doit disposer d'Ubuntu Server. L'installation de Docker et de ses dépendances est automatisée par Ansible.

## Utilisation

Configurer l'inventaire dans `inventory/hosts.ini` avec l'adresse IP, le port SSH et l'utilisateur du serveur cible.

Configurer les informations de connexion au serveur et renseigner le mot de passe Ansible Vault.

Lancer les playbooks pour configurer le serveur et déployer Gitea :

```bash
ansible-playbook -i inventory/hosts.ini playbooks/site.yml --ask-vault-pass
ansible-playbook -i inventory/hosts.ini playbooks/docker.yml --ask-vault-pass
ansible-playbook -i inventory/hosts.ini playbooks/gitea.yml --ask-vault-pass
ansible-playbook -i inventory/hosts.ini playbooks/nginx.yml --ask-vault-pass
```

Sinon, on peut lancer tous les playbooks de déploiement en une commande :

```bash
ansible-playbook -i inventory/hosts.ini playbooks/deploy.yml --ask-vault-pass
```

On peut aussi faire une sauvegarde avec la commande : 

```bash
ansible-playbook -i inventory/hosts.ini playbooks/backup.yml --ask-vault-pass
```

Une fois le déploiement terminé, Gitea est accessible depuis un navigateur à l'adresse configurée.

## Auteur

L'auteur de ce projet est:
- Tristan Roussat
