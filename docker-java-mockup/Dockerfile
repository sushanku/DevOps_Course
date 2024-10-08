# Building with multistage to optimize the image size
# stage 1: Build application with gradle
FROM maven:3.8.3-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean install

# Stage 2: Deploy the application
FROM openjdk:17-jdk-slim
ARG RELEASE_VERSION=1.0
WORKDIR /app
COPY --from=build /app/target/*-$RELEASE_VERSION-*-dependencies.jar mockup.jar
# COPY etc ./etc
EXPOSE 4567
ENTRYPOINT ["java", "-jar", "mockup.jar"]