FROM postgres:9.4
MAINTAINER Cityway

LABEL Description="CVDTC DB" \
      Usage="docker run --name cvdtc-postgres -p 5434:5432 -e POSTGRES_USER=chouette -e POSTGRES_PASSWORD=chouette -d cvdtc-postgres" \
      BuildUsage="docker build -t cvdtc-postgres ." \
      License="CECILL/B" \
      Version="3.0"

RUN apt-get update && apt-get install -y postgresql-contrib-9.4

COPY docker-entrypoint-initdb.d/* /docker-entrypoint-initdb.d/

