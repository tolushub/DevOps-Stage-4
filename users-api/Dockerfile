# users-api/Dockerfile
FROM maven:3.8.5-openjdk-17 AS build-stage
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY --from=build-stage /app/target/*.jar ./users-api.jar
ENV SERVER_PORT=8083
ENV JWT_SECRET=myfancysecret
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]