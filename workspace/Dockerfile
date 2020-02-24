FROM tomcat:9.0.30-jdk8-openjdk
MAINTAINER Fabian Dsouza

#ENV CATALINA_HOME /usr/local/tomcat
ENV PATH /usr/local/tomcat/bin:$PATH
ENV UNIVERSAL_HOME /usr/local/UM/
ENV JAVA_HOME /usr/local/openjdk-8

WORKDIR /usr/local/tomcat
COPY postgresql-42.2.9.jar /usr/local/tomcat/lib
COPY cmsbs-restproxy.war /usr/local/tomcat/webapps/
RUN chmod +x /usr/local/tomcat/bin/catalina.sh
CMD [ "/usr/local/tomcat/bin/catalina.sh" , "run" ]

WORKDIR $UNIVERSAL_HOME
#VOLUME um_data:$UNIVERSAL_HOME
COPY um_data/cmsbs.license .
COPY um_data/install4j.varfile .
COPY um_data/UM-7_32_0b1400-unix.sh .

RUN chmod +x UM-7_32_0b1400-unix.sh
RUN yes "" | sh UM-7_32_0b1400-unix.sh -varfile install4j.varfile
COPY cmsbs.properties /usr/local/UM/cmsbs-conf/
