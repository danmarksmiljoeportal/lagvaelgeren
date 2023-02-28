# Datakatalog service

The datakatalog service is a REST API service containing a catalouge of dataset metadata including technical details about dataset sources so that they can be consumed in a mapping solution.

## Getting Started

The Datakatalog service REST API is formally described and documented [here](https://datakatalog.miljoeportal.dk/api/swagger).

A basic example request is a HTTP GET request against URL [https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource](https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource) which will give you all datasets in the catalog including metadata about associated WMS service if exists.

As detailed in the API documentation, the REST API adheres to the [JSON-API standard](https://jsonapi.org/). This allows the payload to be parsed by existing client implementations and offers standardised means to fetch hierarchical structures and filtering. JSON-API is however just a REST API that adheres to a spec so it's relatively straight forward to consume and parse without any external dependencies.

To fully understand the endpoints and schemas that the REST API is exposing it can be beneficial to know more details about the data model than the API documentation supplies. The data model is fully [documented here][../datamodel].
