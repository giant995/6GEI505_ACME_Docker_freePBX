# 6GEI505_ACME_Docker_freePBX

# Introduction
Cette application est basée sur le projet [Docker-freePBX par tiredofit](https://github.com/tiredofit/docker-freepbx). S'y référer pour la documentation exhaustive ou pour tout problème.

# Prerequisites

- [Docker](https://docs.docker.com/get-docker/)

# Installation
Les instructions d'installation assument qu'une interface en ligne de commande  (CLI) est utilisée. Sous Windows, Powershell est normalement l'outil utilisé.

1. Cloner la repo (HTTPS, SSH ou GitHub CLI)

    `git clone https://docs.docker.com/get-docker/`

1. Se déplacer dans la repo
    
    `cd path/to/repo/6GEI505_ACME_Docker_freePBX`

1. Démarrer l'application avec docker compose

    `docker-compose up`
    
    Lors du premier lancement du l'application, Docker fait l'installation des images qui sont tout de même volumineuses. Cela peut prendre entre 5 et 30 minutes à installer. L'application est prête à être utilisé lorsque la ligne `[cron] Starting cron` apparait. En cas de problèmes, se référer à la documentation de l'auteur du projet ou à une recherche sur internet.

1. Accéder au panneau d'administrateur à l'adresse

    `https://localhost:443/admin`
    
    Il est normal que le navigateur vous avise que l'accès à cette adresse ne soit pas sécuritaire. Les certificats TLS ne sont pas encore générés.
    
# Recommencer à neuf
Il est possible de supprimer les données dans les volumes pour repartir un conteneur en condition initiale
1. Exécuter la commande suppression des volumes (irréversibles pour les données) dans le dossier du `docker-compose.yml`
    
    `docker-compose down -v`
1. Supprimer les dossiers `/data`, `/db`, `dbbackup`, `certs` et `logs` si la précédente commande ne force pas une réinstallation.
    
`docker-compose` est la commande pour arrêter l'application spécifiée par le `docker-compose.yml` présent dans le répertoire. Le flag `-v` indique la suppression des volumes.
    
# Stopper tous les conteneurs sur l'hôte
Pour arrêter tous les conteneurs sur l'hôte sans supprimer les données
1. Exécuter la commande d'arrêt

    `docker stop $(docker ps -aq)`
    
La commande `docker stop` permet d'arrêter un ou des conteneurs dont on spécifie le tag. La commande `docker ps -aq` permet de lister tous les conteneurs avec les flags permettant de n'afficher que leur tag. `$()` permet de prendre le résultat d'une commande et de le transformer en variable. Dans le cas présent, on utilise la sortie de la commande qui liste les tags de tous les conteneurs pour en faire une variable pour la commande qui arrête les conteneurs.
    
# Considérations
- Un conteneur n'est pas un endroit idéal pour y emmagasiner des données, car il peut être fréquemment détruit et reconstruit. De ce fait, les données sont emmagasinés via des volumes à l'extérieur du conteneur dans les fichiers de l'hôte.
