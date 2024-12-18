# Utiliser une image Node.js en tant que base
FROM registry.access.redhat.com/ubi8/nodejs-16

RUN rm -rf /app

# Créer un répertoire de travail pour l'application
WORKDIR /app

# Copier le fichier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances de l'application
RUN npm install

RUN npm update

# Copier le reste de l'application
COPY . .

# Ajouter un utilisateur non-root
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Changer les droits du répertoire de travail pour l'utilisateur non-root
RUN chown -R appuser:appgroup /app

# Exécuter le processus en tant qu'utilisateur non-root
USER appuser

# Exposer le port 8080 au lieu de 80 (conformité OpenShift)
EXPOSE 8080

# Démarrer l'application en utilisant npm start
CMD ["npm", "start"]
