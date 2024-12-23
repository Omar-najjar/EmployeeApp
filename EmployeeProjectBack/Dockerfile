# Étape 1 : Construction
FROM maven:3.8.4-openjdk-17 AS build

# Définir le répertoire de travail pour la construction
WORKDIR /app

# Copier les fichiers Maven (pom.xml, mvnw, etc.) et résoudre les dépendances
COPY pom.xml mvnw ./
COPY .mvn .mvn
COPY src ./src
# RUN ./mvnw dependency:resolve

# Copier le code source et construire l'application

#RUN ./mvnw package
RUN mvn clean package -DskipTests

# Étape 2 : Image finale
FROM openjdk:17-jdk-alpine

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier l'artefact généré dans l'image finale
COPY --from=build /app/target/springboot-docker.jar app.jar


# Définir la commande de démarrage
ENTRYPOINT ["java", "-jar", "app.jar"]
