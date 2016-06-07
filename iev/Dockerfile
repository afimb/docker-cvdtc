FROM jboss/wildfly:9.0.2.Final
MAINTAINER Cityway

ENV CVDTC_CV_VERSION 1.0.1

LABEL Description="CVDTC IEV" \
      Usage="docker run -it --name cvdtc-iev --link cvdtc-postgres:cvdtc-postgres -p 9992:9990 -p 8082:8080 -d cvdtc-iev" \
      BuildUsage="docker build -t cvdtc-iev ." \
      License="CECILL/B" \
      Version="3.0"

USER root

RUN yum -y install wget nmap

USER jboss

RUN /opt/jboss/wildfly/bin/add-user.sh admin admin --silent

RUN wget -q http://central.maven.org/maven2/org/postgresql/postgresql/9.4-1206-jdbc42/postgresql-9.4-1206-jdbc42.jar -O /tmp/postgresql.jar && \
    wget -q http://maven.chouette.mobi/mobi/chouette/cvdtc_cv/${CVDTC_CV_VERSION}/cvdtc_cv-${CVDTC_CV_VERSION}.ear -O /tmp/cvdtc_cv.ear

EXPOSE 8080 9990

COPY config/wildfly-datasources.cli /tmp/
COPY config/docker-entrypoint.sh /
VOLUME ["/opt/jboss/referentials"]
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD [ "/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]

