# Use a base image with Maven installed
FROM maven:3.8.6-openjdk-11 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy your local project files into the container's /app directory
COPY . .

# Run Maven to clean and package the project
RUN mvn clean package -DskipTests

# Final stage (optional, if you want to run the app, you can use another base image)
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/target/your-artifact-name.jar /app/your-artifact-name.jar
CMD ["java", "-jar", "/app/your-artifact-name.jar"]
