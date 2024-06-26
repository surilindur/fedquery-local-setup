This setup required NodeJS, Docker and Docker Compose.

Clone the repository, including the submodules:

```bash
git clone --recurse-submodules git@github.com:surilindur/fedquery-local-setup.git
```

For `rdf-dataset-fragmenter.js`, enter the submodule directory and install the dependencies.
After that, install the dependencies for `SolidBench.js` the same way.

```bash
yarn install
```

The dataset can then be generated in the `SolidBench.js` directory:

```bash
node bin/solidbench.js generate
```

The endpoints can be started using Docker Compose:

```bash
docker compose --file templates/endpoints.yaml up
```

To send a SPARQL query to the endpoint:

```bash
curl -X POST -d 'SELECT * WHERE { ?s ?p ?o }' -H 'Content-Type: application/sparql-query' http://localhost:3001/sparql?default-graph-uri=http://localhost:3000/pods/00000017592186045261/
```
