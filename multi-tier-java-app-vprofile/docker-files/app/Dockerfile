FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Prajwal"
RUN apt update && apt install maven -y
ADD ./vprofile-project/ vprofile-project
RUN cd vprofile-project && mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]