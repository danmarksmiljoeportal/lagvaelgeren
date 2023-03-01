# Datakatalog service

The datakatalog service is a REST API service containing a catalouge of Dataset metadata including technical details about Dataset sources so that they can be consumed in a mapping solution.

## Getting Started

The Datakatalog service REST API is formally described and documented [here](https://datakatalog.miljoeportal.dk/api/swagger).

As detailed in the API documentation, the REST API adheres to the [JSON-API standard](https://jsonapi.org/). This allows the payload to be parsed by existing client implementations and offers standardised means to fetch hierarchical structures and filtering included or out of band. However, note that JSON-API is made to be conformant to general REST API principles so it's relatively straight forward to consume and parse without any external dependencies. We recommend to use or be inspired by [existing implementations](https://jsonapi.org/implementations/).

A basic example request is a HTTP GET request against URL [https://datakatalog.miljoeportal.dk/api/datasets](https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource) which will give you all Datasets with all attributes but without any related information. To get related information without
additional requests the include parameter (part of JSON-API) can be used. For example, [https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource](https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource) will provide the same Datasets as the previous request but including the related WmsSource that describes a WMS service which can the be used by the consumer to request actual data as map images.

Note that [WMS](https://www.ogc.org/standard/wms/), [WMTS](https://www.ogc.org/standard/wmts/) and [WFS](https://www.ogc.org/standard/wfs/) are protocols that most mapping software can consume. These are open specifications extensively documented at [OGC](https://www.ogc.org).

To fully understand the endpoints and schemas that the REST API is exposing we recommend to study the data model that is the API is based on. The data model is documented [here](../datamodel).
