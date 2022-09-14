FROM postgres:14.5
RUN apt-get update && apt-get  install -y postgresql-14-postgis-3
#COPY demo-dataset demo-dataset
COPY SNOMEDCT.sql /docker-entrypoint-initdb.d/SNOMEDCT.sql