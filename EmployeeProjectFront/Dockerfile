# Étape 1 : Construction de l'application Angular
FROM node:18-alpine AS build

# Définir le répertoire de travail pour la construction
WORKDIR /app

# Copier les fichiers nécessaires pour installer les dépendances
COPY package.json package-lock.json ./

# Installer les dépendances
RUN npm install

# Copier tout le code source Angular
COPY . .

# Construire l'application pour la production
RUN npm run build --prod

# Étape 2 : Image finale avec Nginx
FROM nginx:alpine

# Copier les fichiers construits dans le répertoire par défaut de Nginx
COPY --from=build /app/dist/employee-project-front /usr/share/nginx/html


# Lancer Nginx
CMD ["nginx", "-g", "daemon off;"]
