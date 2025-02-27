# Build stage
FROM maven:3.8-openjdk-8 AS build

WORKDIR /app

COPY pom.xml ./

RUN mvn dependency:go-offline

COPY . .

RUN mvn package -DskipTests

# Production stage
FROM openjdk:8-jdk-slim

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8083

CMD ["java", "-jar", "app.jar"]