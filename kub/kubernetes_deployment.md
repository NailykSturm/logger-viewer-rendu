[toc]

# Prérequis

Pour pouvoir déployer ce projet, il vous faut:
- un cluster kubernetes fonctionnel (que ce soit en local, ou sur un serveur).
- cloner ce répertoire sur la machine qui va déployer ce projet (Ou à minima, le dossier `kub` de ce répertoire).
- avoir créer le raccourci `kubectl` pour pouvoir copier et exécuter les commandes fournies (sinon, il faudra remplacer tous les `kubectl` par `minikube kubectl -- `).

# Déploiement

Pour déployer ce projet, il faut suivre plusieurs étapes :

## Déployment de l'environnement

Dans ce projet, nous avons besoin de lancer kubeernetes avec une configuration spécifique. Pour cela, il va falloir lancer les commandes suivantes :
`minikube start --static-ip 192.168.10.10`

Si vous voulez lancer le dashboard de kubernetes pour surveiller votre cluster, vous pouvez lancer la commande suivante : 
`minikube dashboard --port 42453`

Après que votre cluster kubernetes soit lancé, vous pouvez créer les namespaces qu'on utilise dans ce projet :
`kubectl apply -f ./kub/namespace.yaml` 

Pour gagner du temps pour les commandes suivantes, vous pouvez mettre le namespace `logger-viewer` en namespace par défaut :
`kubectl config set-context --current --namespace=logger-viewer`

## Déployment de la base de données

Avant de déployer l'ensemble de nos ressources, il faut initialiser la base de données. Pour cela, il faut lancer la commande suivante :
`kubectl create configmap mysql-initdb-config --from-file=./kub/mysql/initdb.sql` 

## Déployment des différents services

Désormais il est possible d'exécuter l'ensembe de nos ressources. Pour cela, il faut lancer la commande suivante :
`kubectl apply -f ./kub/ -R`

# Accès aux services

## Accès au frontend

Pour accéder au frontend de notre application, vous pouvez y accéder via le service minikube :
`minikube service lvf-service -n logger-viewer`