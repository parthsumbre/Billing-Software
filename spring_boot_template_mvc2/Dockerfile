FROM maven:3.8.3-openjdk-11 AS build
COPY..
RUN mvn clean package -DskipTests

FROM openjdk:11.0.11-jdk-slim
COPY --from==build /target/demo-0.0.1-SNAPSHOT.jar spring_boot_template_mvc2.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","spring_boot_template_mvc2.jar"]
