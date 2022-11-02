FROM stain/jena-fuseki:4.0.0

# Update security file with custom settings
RUN rm shiro.ini
COPY shiro.ini shiro.ini

RUN apt-get update; \
    apt-get install -y --no-install-recommends procps

RUN mkdir -p /fuseki/ontologies/
RUN mkdir -p /fuseki/configuration/

RUN mkdir -p /fuseki
WORKDIR /fuseki

# Add configuration file which specifies inside the ontology name
COPY config.ttl configuration/config.ttl
# Add ontology
COPY SCTO_formatted.owl ontologies/SCTO_formatted.owl