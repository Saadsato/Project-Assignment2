FROM tomcat:11.0.0-M1-jdk17
WORKDIR /usr/local/tomcat/webapps
COPY ./target/ROOT.war .
EXPOSE 8099
CMD ["catalina.sh", "run"]