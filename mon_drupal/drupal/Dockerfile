
# Dockerfile
# Créer une image personalisée de Drupal à partir de la version Drupal 9 
# Cours : Installation des Serveurs et services (420-W45-SF)

# Utilise la version 9 de Drupal
FROM drupal:9
COPY . .

RUN apt update && apt install -y git \ rm -rf /var/lib/apt/lists/*
WORKDIR /var/www/html/themes
RUN git clone --branch 5.0.x --single-branch depth 1 https://git.drupalcode.org/project/bootstrap.git

ENTRYPOINT . .

CMD