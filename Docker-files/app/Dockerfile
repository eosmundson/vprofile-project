FROM amazoncorretto:11-alpine AS BUILD_IMAGE
LABEL "Project"="vprofile"
LABEL "Author"="Imran"

RUN apk -U add maven git
RUN git clone https://github.com/eosmundson/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install



FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
