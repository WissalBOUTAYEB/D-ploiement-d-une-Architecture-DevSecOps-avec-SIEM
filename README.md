# Projet DevSecOps & SIEM avec VMs et Docker

## Description

Ce projet a pour objectif de déployer une architecture DevSecOps intégrant une chaîne CI/CD sécurisée et un système de supervision SIEM basé sur la stack ELK (Elasticsearch, Logstash, Kibana). 

Le projet est réalisé en deux phases :

- **TP1 : Déploiement sur des Machines Virtuelles (VM)**  
  Chaque composant est installé et configuré sur des VM distinctes.

- **TP2 : Déploiement via des Conteneurs Docker**  
  Reproduction de la même architecture dans un environnement Docker pour faciliter le déploiement, la portabilité et la gestion.

---

## Fonctionnalités principales

- Mise en place d’une pipeline CI/CD sécurisée avec GitLab CI (analyse statique, scanning de conteneurs, déploiement automatique)
- Centralisation des logs systèmes et applicatifs via Filebeat
- Indexation et stockage des logs avec Elasticsearch
- Visualisation et analyse des logs avec Kibana (dashboards personnalisés)
- Simulation d’activités réseau (scan, brute force) pour tester la détection d’incidents

---

## Architecture

| Composant           | Rôle                                         | Support           |
|---------------------|----------------------------------------------|-------------------|
| GitLab + Runner     | Gestion du code source + pipeline CI/CD       | VM ou Conteneur   |
| Application (Node.js ou Flask) | Application déployée                    | VM ou Conteneur   |
| Elasticsearch       | Stockage et indexation des logs               | VM ou Conteneur   |
| Kibana              | Visualisation et analyse des logs             | VM ou Conteneur   |
| DHCP Server         | Génération de logs réseau pour simulation     | VM ou Conteneur   |
| Filebeat            | Collecte et transfert des logs vers Elasticsearch | VM ou Conteneur   |

---

## Structure des dossiers

- `/tp1-vm` : Configuration et scripts pour déploiement sur machines virtuelles  
- `/tp2-docker` : Fichiers `docker-compose.yml`, Dockerfiles, configurations pour déploiement via Docker  
- `/gitlab-ci` : Exemple de fichier `.gitlab-ci.yml` avec étapes de sécurité  
- `/filebeat` : Configuration Filebeat pour collecte des logs  
- `/docs` : Schémas, captures d’écran, rapports d’analyse

---

## Instructions d’utilisation

### TP1 - Déploiement sur VMs

1. Provisionner les VMs selon le tableau d’architecture.
2. Installer et configurer chaque composant (GitLab, App, Elasticsearch, Kibana, DHCP, Filebeat).
3. Configurer le pipeline CI/CD dans GitLab.
4. Lancer la simulation de logs réseau.
5. Consulter les dashboards Kibana pour analyse.

### TP2 - Déploiement via Docker

1. Installer Docker et Docker Compose.
2. Lancer l’architecture complète avec :  
   ```bash
   docker-compose up -d
