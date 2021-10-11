# 6GEI505_ACME_Docker_freePBX

# Introduction
Cette application est basée sur le projet [Docker-freePBX par tiredofit](git@github.com:giant995/6GEI505_ACME_Docker_freePBX.git). S'y référer pour la documentation exhaustive ou pour tout problème.

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
    
# Considérations
- Un conteneur n'est pas un endroit idéal pour y emmagasiner des données, car il peut être fréquemment détruit et reconstruit. De ce fait, les données sont emmagasinés via des volumes à l'extérieur du conteneur dans les fichiers de l'hôte.
