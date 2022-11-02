## SNOMED tests
Repository contains some tests on querying the SNOMED CT ontology.
```
docker-compose up
```

This command starts and initializes the database.  
Once the database is ready, it launches the SPARQL endpoint from Ontop at http://localhost:8080.  
Once Ontop is ready, Apache Jena-Fuseki UI will be ready at http://localhost:5050

For this tutorial, we assume that the ports 7777 (used for database), 8080 (used by Ontop) and 5050 (used by Jena-Fuseki) are free. If you need to use different ports, please edit the file .env.

In order to switch between various ontologies:
- For Ontop modify the parameter for ONTOLOGY in the docker-compose.yml file.
- For Jena-Fuseki modify the filename in both the [jena-fuseki/Dockerfile](Dockerfile) and [jena-fuseki/config.ttl](config.ttl) file.

### Apache Jena Federation
Option 1: In order to run only remote endpoints (not localhost like Ontop) the docker-compose setup is sufficient.  
Option 2: In order to run queries over localhost ports, then unzip [jena-fuseki/fhir-apache-jena-fuseki-4.6.1.zip](fhir-apache-jena-fuseki-4.6.1.zip) and:
- Modify the file config.ttl by adding the absolute path to ja:content of the respective owl file in RDF/XML format.
- Run as follows:
```
./fuseki-server --conifg config.ttl
```