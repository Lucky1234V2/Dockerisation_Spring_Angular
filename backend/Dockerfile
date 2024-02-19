# Étape de construction
FROM openjdk:17 AS build
WORKDIR /workspace/app

COPY backend/mvnw .
COPY backend/.mvn .mvn
COPY backend/pom.xml .
COPY backend/src src

RUN ./mvnw install -DskipTests

# Étape de mise en production
FROM openjdk:17
VOLUME /tmp
ARG DEPENDENCY=/workspace/app/target
COPY --from=build ${DEPENDENCY}/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
