FROM maven:3.9.6-eclipse-temurin-11 AS build_image

WORKDIR /app
COPY . .
RUN mvn -B -DskipTests clean package

FROM tomcat:9.0-jdk11-temurin

RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build_image /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
