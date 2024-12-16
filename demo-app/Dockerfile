# Utilisation de l'image Node.js certifiée par Red Hat
FROM registry.access.redhat.com/ubi8/nodejs-16

#Variables d'en
ARG .env

# Définir le répertoire de travail
WORKDIR /app

# Donner les permissions à tous les utilisateurs
RUN chmod -R 777 /app

# Copier le fichier de dépendances
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Exposition du port
EXPOSE 3000

# Exécuter l'application en tant que non-root
USER 1001

# Démarrage de la base
RUN npm run database

# Démarrage du noeud
RUN npm run node
