## SNOMED tests
Repository contains some tests on querying the SNOMED CT ontology.
```
docker-compose up
```

This command starts and initializes the database, ontop and jena-fuseki.  
Once the database is ready, it launches the SPARQL endpoint from Ontop at http://localhost:8080.  
Once Ontop is ready, Apache Jena-Fuseki UI will be ready at http://localhost:5050

For this tutorial, we assume that the ports 7777 (used by database), 8080 (used by Ontop) and 5050 (used by Jena-Fuseki) are free. If you need to use different ports, please edit the file .env.

In order to switch between various ontologies:
- For Ontop modify the parameter for ONTOLOGY in the docker-compose.yml file.
- For Jena-Fuseki modify the filename in both the [Dockerfile](jena-fuseki/Dockerfile) and [config.ttl](jena-fuseki/config.ttl) file.

### SERVICE Query over Ontop
In order to run SERVICE queries within Apache Jena over Ontop, please note that the SERVICE query should use host.docker.interal i.e.:
```
SERVICE <http://localhost:8080/sparql>   { ?s rdf:type <http://purl.obolibrary.org/obo/BFO_0000001> . }
```
should instead be:
```
SERVICE <http://host.docker.internal:8080/sparql>   { ?s rdf:type <http://purl.obolibrary.org/obo/BFO_0000001> . }
```


### Running Apache Jena locally
If you would rather run Apache Jena locally then use docker-compose to setup the database and Ontop.  
Then unzip [fhir-apache-jena-fuseki-4.6.1.zip](jena-fuseki/fhir-apache-jena-fuseki-4.6.1.zip) and:
- Modify the file config.ttl by adding the absolute path to ja:content of the respective owl file in RDF/XML format.
- Run as follows:
```
./fuseki-server --conifg config.ttl
```