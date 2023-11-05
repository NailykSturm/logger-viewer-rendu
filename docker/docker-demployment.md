[toc]

# Prérequis

Pour pouvoir déployer ce projet, il vous faut :
- un environnement docker fonctionnel (que ce soit en local, ou sur un serveur).
- cloner ce répertoire sur la machine qui va déployer ce projet (Ou à minima, le dossier `docker` de ce répertoire).
- avoir installer docker-compose sur la machine qui va déployer ce projet.

# Déploiement

Pour déployer ce projet grâce à docker-compose, il faut suffit de lancer la commande suivante :
`docker-compose up -d`

# Accès aux services

## Accès au frontend

Pour accéder au frontend de notre application, vous pouvez y accéder via l'adresse suivante :
`http://localhost:8080/`