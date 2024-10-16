# Mes Petites Recettes

## Prérequis
 - Docker & Dockercompose

## Installation
1. Copiez le fichier `.env.example` en `.env`, modifiez-le si nécessaire.
2. Copiez le fichier `drush/example.drush.yml` en  `drush/drush.yml`.
3. Lancez les container avec `docker compose up -d`.
4. Importez le dump de base de données situé dans `files/dumps/mpr.sql.gz`.
5. Installez les dépendances PHP via `docker compose exec php composer install`
6. Prenez le contenu de l'archive `files/files.tar.gz` est mettez le dans `web/sites/default/files/` (attention à ne pas avoir de dossier `files` dans `files`)
7. Le site devrait être accessible via [http://mes-petites-recettes.localhost:8000](http://mes-petites-recettes.localhost:8000)


--> Quel fichier modifier pour changer l'url local du site ?
Le fichier qu'il faut modifier est le fichier .env : PROJECT_BASE_URL=mes-petites-recettes.localhost:8000PROJECT_BASE_URL=mes-petites-recettes.localhost:8000

--> Quelle est l'adresse du phpMyAdmin ?
Le phpMYAdmin se trouve dans le fichier docker-compose à la ligne : 

 
"traefik.http.routers.${PROJECT_NAME}_pma.rule=Host(pma.${PROJECT_BASE_URL})"

--> Quel est le fichier qui contient les paramètres de la base de données ?

Le fichier .env contient les paramètres de la base de données avec : 

DB_NAME=mpr
DB_USER=drupal
DB_PASSWORD=drupal
DB_ROOT_PASSWORD=password
DB_HOST=mariadb
DB_PORT=3306
DB_DRIVER=mysql

--> Comment sont-ils lu par drupal ?

--> Quelle est la commande drush qui permet de se connecter en tant qu'administrateur ?



Il  ne ma pas été possible de verifier le fonctionnement du projet dû à un timeout lors de l'utilisation de la commande docker compose exec php composer install`

PS C:\Users\nansg\Desktop\Cours\R5.A.09 Virtualisation avancé\mes-petites-recettes-main> docker compose exec php composer install
> DrupalProject\composer\ScriptHandler::checkComposerVersion
Installing dependencies from lock file (including require-dev)
Verifying lock file contents can be installed on current platform.
Package operations: 1 install, 0 updates, 0 removals
  - Downloading drupal/core (10.1.8)
  - Installing drupal/core (10.1.8): Extracting archive
    Install of drupal/core failed
Check https://getcomposer.org/doc/06-config.md#process-timeout for details

In Process.php line 1204:

  The process "'/usr/bin/unzip' -qq '/var/www/html/vendor/composer/tmp-1a9b7cc44bab991e4565d52b71d14179' -d '/var/www/html/vendor/composer/6fc386ff'" exceeded the timeout of 300 seconds.  


install [--prefer-source] [--prefer-dist] [--prefer-install PREFER-INSTALL] [--dry-run] [--download-only] [--dev] [--no-suggest] [--no-dev] [--no-autoloader] [--no-progress] [--no-install] [--audit] [--audit-format AUDIT-FORMAT] [-v|vv|vvv|--verbose] [-o|--optimize-autoloader] [-a|--classmap-authoritative] [--apcu-autoloader] [--apcu-autoloader-prefix APCU-AUTOLOADER-PREFIX] [--ignore-platform-req IGNORE-PLATFORM-REQ] [--ignore-platform-reqs] [--] [<packages>...]
