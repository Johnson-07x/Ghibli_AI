# Stage 1: Build the application
# Changed from maven:3.8.5-openjdk-17 to eclipse-temurin for stability
FROM maven:3.9.6-eclipse-temurin-17 AS build
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the application
# Replace the deprecated openjdk:17-jdk-slim
FROM eclipse-temurin:17-jre-jammy
COPY --from=build /target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
