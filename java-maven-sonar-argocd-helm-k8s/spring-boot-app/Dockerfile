# -------- Build Stage --------
FROM maven:3.8.6-openjdk-17 AS build

WORKDIR /build

# Copy project files
COPY . .

# Build the application
RUN mvn clean package -DskipTests

# -------- Runtime Stage --------
FROM openjdk:17-jdk-slim

WORKDIR /opt/app

# Copy the built JAR from the previous stage
COPY --from=build /build/target/spring-boot-web.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
