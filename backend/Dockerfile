# Stage 1: Build the Spring Boot app
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app
COPY backend/. .
RUN mvn clean package -DskipTests

# Stage 2: Run the app
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
