# Utiliser une image Node.js en tant que base
FROM registry.access.redhat.com/ubi8/nodejs-16

# Créer un répertoire de travail pour l'application
WORKDIR /app

# Création du groupe et de l'utilisateur non-root
#RUN groupadd -r appgroup && \
#    useradd -r -g appgroup -d /app -s /sbin/nologin appuser

# Donner les permissions à tous les utilisateurs
RUN chmod -R 777 /app

# Copier le fichier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances de l'application
RUN npm install

# RUN npm update

# Copier le reste de l'application
COPY . .

# Changer les droits du répertoire de travail pour l'utilisateur non-root
# RUN chown -R appuser:appgroup /app

# Exécuter l'application en tant que non-root
USER 1001

# Exposer le port 8080 au lieu de 80 (conformité OpenShift)
EXPOSE 8080

# Démarrer l'application en utilisant npm start
CMD ["npm", "start"]
