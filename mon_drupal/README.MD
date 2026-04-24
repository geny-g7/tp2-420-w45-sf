

Cette partie décrit la création d'une image drupal personalisée.

- Ici, nous pouvons consulter le dépôt de Drupal sur docker hub : https://hub.docker.com/_/drupal.

Nous allons procéder à la création d'un fichier Dockerfile pour l'image visée et ce fichier utilisera la version 9 de drupal :

    ```
    FROM drupal:9
    COPY
    ENTRYPOINT
    ```

- Installation de git avec la commande suivante (la commande devrait pouvoir s'exécuter sans 'sudo', mais le cas échéant ajouter sudo) : 

    ```
    sudo apt update && sudo apt install -y git \ rm - rf /var
    ```



