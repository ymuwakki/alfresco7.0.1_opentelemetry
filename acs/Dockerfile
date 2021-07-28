FROM quay.io/alfresco/alfresco-content-repository:7.0.1
#FROM quay.io/alfresco/alfresco-content-repository:7.1.0-M1

USER root

RUN yum update -y

ARG TOMCAT_DIR=/usr/local/tomcat

RUN mkdir -p $TOMCAT_DIR/shared/classes/alfresco/extension/license

COPY artifacts/amps/*.amp $TOMCAT_DIR/amps/
COPY artifacts/Alfresco-ent70-ArmediaLLCexpires28Aug2021.lic $TOMCAT_DIR/shared/classes/alfresco/extension/license
COPY artifacts/alfresco-governance-services-enterprise-rest-api-explorer-3.5.0.war $TOMCAT_DIR/webapps/ags-api-explorer.war

#  Install AMPS
RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar list $TOMCAT_DIR/webapps/alfresco
RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar install \
              $TOMCAT_DIR/amps $TOMCAT_DIR/webapps/alfresco -directory -nobackup -force -verbose
RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar list $TOMCAT_DIR/webapps/alfresco



#RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar uninstall org.alfresco.integrations.google.docs $TOMCAT_DIR/webapps/alfresco
#RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar uninstall alfresco-share-services $TOMCAT_DIR/webapps/alfresco
#RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar uninstall alfresco-trashcan-cleaner $TOMCAT_DIR/webapps/alfresco
#RUN java -jar $TOMCAT_DIR/alfresco-mmt/alfresco-mmt*.jar list $TOMCAT_DIR/webapps/alfresco
