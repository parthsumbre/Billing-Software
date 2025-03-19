# Stage 1: Build
FROM maven:3.8.3-openjdk-11 AS build

# Set the working directory
WORKDIR /app

# Copy source code into the container
COPY . .

# Build the project, skipping tests
RUN mvn clean package -DskipTests

# Stage 2: Run
FROM openjdk:11.0.11-jdk-slim

# Copy the built JAR file from the build stage
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 for the application
EXPOSE 8080

# Set the entry point for running the application
ENTRYPOINT ["java", "-jar", "app.jar"]
