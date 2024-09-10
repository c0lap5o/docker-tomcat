FROM tomcat:9-jdk11-openjdk-slim

# Set Tomcat to use different ports
ENV CATALINA_OPTS="-Dport.http=8888 -Dport.shutdown=8006"

# Remove default Tomcat applications except manager and host-manager
RUN rm -rf /usr/local/tomcat/webapps/* && \
    mv /usr/local/tomcat/webapps.dist/manager /usr/local/tomcat/webapps/manager && \
    mv /usr/local/tomcat/webapps.dist/host-manager /usr/local/tomcat/webapps/host-manager

# Copy your custom tomcat-users.xml file
COPY tomcat-users.xml /usr/local/tomcat/conf/tomcat-users.xml

# Copy custom context.xml to disable IP restriction for manager app
COPY context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml

# Modify server.xml to use the environment variables
RUN sed -i 's/port="8005"/port="${port.shutdown}"/g' /usr/local/tomcat/conf/server.xml && \
    sed -i 's/port="8080"/port="${port.http}"/g' /usr/local/tomcat/conf/server.xml

EXPOSE 8888

CMD ["catalina.sh", "run"]
