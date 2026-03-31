FROM maven:3.9.9-eclipse-temurin-11 AS build
WORKDIR /app

COPY pom.xml .
COPY .mvn .mvn
COPY mvnw .
COPY mvnw.cmd .
COPY src src

RUN chmod +x mvnw && ./mvnw clean package -DskipTests

FROM eclipse-temurin:11-jre
WORKDIR /app

COPY --from=build /app/target/timelysync-backend-1.0.0.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
