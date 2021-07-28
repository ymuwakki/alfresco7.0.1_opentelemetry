FROM alfresco/alfresco-share:7.0.1

RUN yum update -y
ARG TOMCAT_DIR=/usr/local/tomcat
RUN mkdir -p $TOMCAT_DIR/amps_share
COPY amps/*.amp $TOMCAT_DIR/amps_share/
RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install \
              $TOMCAT_DIR/amps_share $TOMCAT_DIR/webapps/share -directory -nobackup -force -verbose
