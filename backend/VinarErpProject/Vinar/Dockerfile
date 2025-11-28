                          # ----- Build Stage -----
FROM maven:3.9.0-eclipse-temurin-17 AS build
WORKDIR /app

COPY pom.xml .
RUN mvn -B -f pom.xml -DskipTests dependency:go-offline

COPY src ./src
RUN mvn -B -DskipTests clean package

# ----- Run Stage -----
FROM eclipse-temurin:17-jre-jammy
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENV JAVA_OPTS="-Xms256m -Xmx512m"

CMD ["sh", "-c", "java $JAVA_OPTS -jar app.jar"]  
