FROM openjdk:11 AS BUILD_IMAGE
LABEL "Description"="image to build the artifact"
RUN apt update && apt install maven -y
RUN git clone https://github.com/mohamedelhaouil/Dockerizing-Java-App.git
#ADD ../.. Dockerizing-Java-App
RUN cd Dockerizing-Java-App && mvn install

FROM tomcat:9-jre11
LABEL LABEL "Description"="App image"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Dockerizing-Java-App/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh",  "run"]