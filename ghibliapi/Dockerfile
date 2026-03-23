# Stage 1: Build the application using Java 21
FROM maven:3.9.6-eclipse-temurin-21 AS build
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the application using Java 21 JRE
FROM eclipse-temurin:21-jre-jammy
# This copies the generated jar. Ensure the name matches your pom.xml artifactId
COPY --from=build /target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
