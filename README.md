# tp2-420-w45-sf
Cours Installation Serveurs et Services - TP2

Nom : Eugénio Georges
Date : 2026-04-22

Description du projet (Tiré de l'énoncé de travail) :
Ce projet a pour but de :
- Démontrer l'installation d'un système de container docker;
- Configurer le sytème de container en fonction d'une utilisation sécuritaire;
- Vérifier que les éléments installés fonctionnent comme prévu;
- et enfin configurer les règles de gestion des accès sécuritaires


Avant toute chose, nous allons véritier que les composants de Docker onté été bel et bien installés.
Il s'agit de deux cmoposants, Docker Engine et Docker Compose. Les commandes à utiliser pour ces vérifications sont les suivantes : 
docker version et docker compose version. Une fois ces deux commandes exécutées, si les composants sont effectivement installés, les informations y associées sont affichées. la fenêtre affiche les détails semblables à ceux-ci : ![Version de Docker](images/docker_engine_version.png) et  ![Version de Docker Compose](images/docker_compose_version.png)


Section 1 - Étape 2
Création de containers et d'un réseau privé :

Dans cette section, nous allons démontrer la création de containers et d'un réseau local auquel sera associé les dits containers.
- Avec la commande suivante : 'docker network create -d bridge mon_reseau', nous procédons à la création d'un réseau privé nommé mon_reseau pour connecter des containers que nous allons créons.
- Deux containers à créer : Apache, avec l'image httpd:latest et MongoDb avec l'image  
- Commandes utilisées pour le container 
    - Apache : docker container run --rm --publish 80:80 --net mon_reseau --detach --name apache httpd:latest
    - Créer le volume de MongoDb : docker volume create mongoDb
    - Création d'un dossier mongoDb pour servir comme point de montage : mkdir mongoDb
    - MongoDb : docker container run --rm -v mongoDb:/point_montage busybox ls -l /point_montage --publish 8765:8765 --net mon_reseau --detach --name mongodb mongodb/mongodb-community-server
    - MongoDb : docker container run --rm -v mongoDb:/point_montage busybox ls -l /point_montage --publish 8765:8765 --net mon_reseau --detach --name mongodb mongodb/mongodb-community-server


Sites de référence : 
- Gemini pour la recherche de la méthode pour inclure une image dans un fichier README.MD;
- Documentation de Docker sur la création de réseaux privés : https://docs.docker.com/engine/network/


