# Stage 1: Build with Maven and Java 21
FROM maven:3.9.6-eclipse-temurin-21 AS build

WORKDIR /app
COPY . .
RUN chmod +x mvnw
RUN ./mvnw clean package -DskipTests

# Stage 2: Run the Spring Boot JAR
FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app
COPY --from=build /app/target/CRM-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]

