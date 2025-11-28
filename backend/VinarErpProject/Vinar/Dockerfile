# Use Maven to build the project
FROM maven:3.8.6-openjdk-11 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy your local project files into the container's /app directory
COPY . .

# Run Maven to clean and package the project
RUN mvn clean package -DskipTests

# Final stage to run the application
# Using openjdk:11-jre-slim-buster as a replacement for openjdk:11-jre-slim
FROM openjdk:11-jre-slim-buster

# Set the working directory inside the container
WORKDIR /app

# Copy the JAR file built in the previous stage
COPY --from=builder /app/target/your-artifact-name.jar /app/your-artifact-name.jar

# Command to run the application
CMD ["java", "-jar", "/app/your-artifact-name.jar"]
