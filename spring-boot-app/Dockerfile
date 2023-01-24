FROM maven:3-openjdk-18
COPY . .
RUN mvn clean package


FROM openjdk:19-alpine
VOLUME /tmp
COPY --from=0  target/*.jar app.jar
CMD ["java","-jar","/app.jar"]