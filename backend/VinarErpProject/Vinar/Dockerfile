# Build stage: Use Maven to build the project with OpenJDK 11
FROM maven:3.8.6-openjdk-11 AS builder

# Set the working directory inside the container to /app
WORKDIR /app

# Copy the local project files (including pom.xml) into the container's /app directory
COPY . .

# Run Maven to clean and package the project (skipping tests)
RUN mvn clean package -DskipTests

# Final stage: Use OpenJDK to run the application
# Using openjdk:11-jre-slim as a more reliable, commonly available base image
FROM openjdk:11-jre-slim

# Set the working directory inside the container for runtime to /app
WORKDIR /app

# Copy the built JAR file from the builder stage into the /app directory of the final image
COPY --from=builder /app/target/your-artifact-name.jar /app/your-artifact-name.jar

# Command to run the application when the container starts
CMD ["java", "-jar", "/app/your-artifact-name.jar"]
