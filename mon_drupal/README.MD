

Cette partie décrit la création d'une image drupal personalisée.

- Ici, nous pouvons consulter le dépôt de Drupal sur docker hub : https://hub.docker.com/_/drupal.

Nous allons procéder à la création d'un fichier Dockerfile pour l'image visée et ce fichier utilisera la version 9 de drupal. Le contenu du fichier docker est tel que suit :

    ```
    FROM drupal:9 
        run sudo apt update && sudo apt install -y git \ rm - rf /var/lib/apt/lists 
        WORKDIR var/www/html/themes 
        run git clone --branch 5.0.x --single-branch --depth 1 https://git.drupalcode.org/project/bootstrap.git 
        chown -R www-data:www-data bootstrap 
        WORKDIR /var/www/html 

        docker volume create -name drupal-data 
        
        docker container run -v drupal-data:/var/lib/postgresql/data --publish 8080:8080 --detach --name postgresdb drupal-data/postgres

    COPY
    ENTRYPOINT
    ```

- Création du volume demndé pour Postgres : 

    ``` 
    docker volume create -name drupal-data 

    docker container run -v drupal-data:/var/lib/postgresql/data --publish 8080:8080 --detach --name postgresdb drupal-data/postgres
    ```



