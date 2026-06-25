# Etapa 1: compilar Spring Boot
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

# Etapa 2: ejecutar la app
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

ENV SERVER_PORT=8081

EXPOSE 8081

ENTRYPOINT ["java", "-jar", "app.jar"]