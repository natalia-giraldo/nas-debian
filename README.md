# 🗄️ Projet Serveur NAS Securisé sous Debian

Titre : Nas_Debian
Auteur : Evan Bonnal, Natalia Giraldo, Ludovic Dos Santos
Formation : Bachelor IT en Cyber
Période : 2 mars 2026 – 7 février 2026 (1 semaine)
Établissement : La plateforme_

# 📝 Description

Ce projet consiste en la conception, l'installation et la configuration complète d'un serveur NAS (Network Attached Storage) à vocation professionnelle, basé sur une distribution Debian Linux.

L'objectif principal est de fournir une solution de stockage robuste, hautement disponible et sécurisée, permettant à différents utilisateurs d'accéder à leurs données via de multiples protocoles, tout en garantissant une tolérance aux pannes matérielles et un plan de reprise d'activité (PRA).

# 🏗️ Architecture et Fonctionnalités

## 1. Stockage et Redondance (RAID 5)
- Technologie : Mise en place d'un RAID 5 logiciel avec l'outil mdadm.
- Configuration : Grappe composée de 3 disques de données actifs et d'1 disque de secours (Spare) pour une auto-réparation en cas de défaillance matérielle.
- Isolation : Séparation stricte entre le disque contenant le système d'exploitation (OS) et la grappe
- RAID dédiée aux données utilisateurs.

## 2. Protocoles d'Accès aux Données
Samba (SMB) : Configuration de partages pour le réseau local, avec gestion stricte des permissions (espaces privés par utilisateur et dossier collaboratif).
SFTP Sécurisé : Accès distant chiffré. Les utilisateurs sont "emprisonnés" dans leur répertoire personnel pour protéger l'arborescence du serveur. Le port SSH par défaut a été modifié (6500) pour contrer les attaques automatisées (bots).
WebDAV (Apache2) : Accès web aux fichiers. Sécurisé par un certificat SSL auto-signé, avec une redirection forcée de tout le trafic HTTP vers HTTPS (Port 443).

## 3. Sauvegarde et Plan de Reprise d'Activité (PRA)
Automatisation : Sauvegardes incrémentielles planifiées (via cron) vers un second serveur distant.
Technologie : Utilisation de l'outil rsync à travers un tunnel SSH sécurisé (authentification par clés asymétriques, sans mot de passe).

## 4. Interface d'Administration (GUI)
Webmin : Déploiement d'une interface web de gestion complète (accessible en HTTPS sur le port 10000) permettant le monitoring des ressources (CPU, RAM, état du RAID) et la gestion simplifiée des utilisateurs et des partages.

# 🛠️ Technologies Utilisées

- OS : Linux Debian
- Stockage : mdadm, ext4
- Réseau & Protocoles : Apache2, Samba, OpenSSH, Rsync
- Administration : Webmin, bash scripting, Cron

# 🤝 Équipe

[Evan Bonnal](https://github.com/EvanBonnal/nas-debian)
[Ludovic Dos Santos](https://github.com/ludovicdos-santos-io/nas-debian)
[Natalia Giraldo](https://github.com/natalia-giraldo/nas-debian)

# 🎓 Contexte
Projet réalisé dans le cadre de la formation d'Administration Système / Cybersécurité à La Plateforme.
