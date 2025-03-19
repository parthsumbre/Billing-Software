# FROM maven:3.8.3-openjdk-11 AS build
# COPY..
# RUN mvn clean package -DskipTests

# FROM openjdk:11.0.11-jdk-slim
# COPY --from==build /target/demo-0.0.1-SNAPSHOT.jar spring_boot_template_mvc2.jar
# EXPOSE 8080
# ENTRYPOINT ["java","-jar","spring_boot_template_mvc2.jar"]


# Use Maven image to build the project
FROM maven:3.8.3-openjdk-11 AS build

# Copy source code into the container
COPY . .

# Build the project, skipping tests
RUN mvn clean package -DskipTests

# Use a lightweight OpenJDK image for running the application
FROM openjdk:11.0.11-jdk-slim

# Copy the built JAR file from the previous stage
COPY --from=build /target/demo-0.0.1-SNAPSHOT.jar spring_boot_template_mvc2.jar

# Expose port 8080 for the application
EXPOSE 8080

# Set the entry point for running the application
ENTRYPOINT ["java", "-jar", "spring_boot_template_mvc2.jar"]
