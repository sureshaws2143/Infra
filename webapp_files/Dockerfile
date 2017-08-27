FROM debian:jessie
RUN apt-get update && apt-get install -y wget
RUN cd /opt && wget --no-cookies --no-check-certificate -c --header "Cookie: oraclelicense=accept-securebackup-cookie oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz && \
tar xvzf jdk-8u144-linux-x64.tar.gz && \
     wget http://www.us.apache.org/dist/tomcat/tomcat-7/v7.0.81/bin/apache-tomcat-7.0.81.tar.gz && \ 
     tar zxpvf apache-tomcat-7.0.81.tar.gz

ENV JAVA_HOME /opt/jdk1.8.0_144
ENV CATALINA_HOME /opt/apache-tomcat-7.0.81
ENV PATH $PATH:$JAVA_HOME/bin
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin
ADD ./run.sh /usr/local/bin/run
EXPOSE 8080
RUN chmod +x /usr/local/bin/run
ENTRYPOINT ["/usr/local/bin/run"]
COPY AngularJSRestful-0.0.1-SNAPSHOT.war /opt/apache-tomcat-7.0.81/webapps
RUN cd /opt/apache-tomcat-7.0.81/webapps && mv AngularJSRestful-0.0.1-SNAPSHOT.war todo.war
