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
