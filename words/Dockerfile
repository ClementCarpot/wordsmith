FROM maven:3.9.5-eclipse-temurin-17 AS builder

WORKDIR /app
COPY pom.xml .
COPY src src/

RUN mvn verify

FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

COPY --from=builder /app/target/words.jar .
COPY --from=builder /app/target/dependency/ dependency/

EXPOSE 8081

CMD ["java", "-Xmx8m", "-Xms8m", "-jar", "words.jar"]