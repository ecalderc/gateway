FROM maven:3.8.5-openjdk-17-slim AS build
VOLUME /tmp
COPY .. ./
RUN mvn clean package -DskipTests

FROM openjdk:17
VOLUME /tmp
EXPOSE 9000
COPY --from=build /target/gateway-0.0.1-SNAPSHOT.jar ./gateway.jar
ENTRYPOINT ["java","-jar","/gateway.jar"]