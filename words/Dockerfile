# Étape 1 : compiler avec Maven
FROM maven AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn verify
# Étape 2 : seulement le JRE, sur Alpine
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build /app/target/words.jar .
COPY --from=build /app/target/dependency ./dependency
EXPOSE 8080
CMD ["java", "-Xmx8m", "-Xms8m", "-jar", "words.jar"]