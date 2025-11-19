# Stage 1 - Build the Jar 
FROM maven:3.8.3-eclipse-temurin-17 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests=true

# Stage 2 - Run the jar
FROM eclipse-temurin:17-jre-jammy

WORKDIR /app

COPY --from=builder /app/target/*.jar /app/target/expenseapp.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app/target/expenseapp.jar"]

