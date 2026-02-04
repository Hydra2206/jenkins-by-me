FROM eclipse-temurin:17-jre

WORKDIR /app

COPY target/news-webapp-0.0.1-SNAPSHOT.jar app.jar
COPY .env .env

EXPOSE 9090

ENTRYPOINT ["java", "-jar", "app.jar"]