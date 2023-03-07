# Datakatalog service

The datakatalog service is a REST API service containing a catalog of Dataset metadata including technical details about Dataset sources, for example WMS services, so that they can be consumed in a mapping solution.

![image](https://user-images.githubusercontent.com/120640911/223372119-706610ea-ded8-40f2-9e23-d62f5970700b.png)


To fully understand the endpoints and schemas that the REST API is exposing we recommend to study the data model that is the API is based on. The data model is documented [here](../datamodel).

Data source protocols [WMS](https://www.ogc.org/standard/wms/), [WMTS](https://www.ogc.org/standard/wmts/) and [WFS](https://www.ogc.org/standard/wfs/) are industry standards that most mapping software can consume and open specifications extensively documented at [OGC](https://www.ogc.org).

## JSON-API

As detailed in the API documentation, the REST API adheres to the [JSON-API standard](https://jsonapi.org/). This allows the payload, in JSON, to be parsed by existing client implementations and offers standardised means to fetch hierarchical structures and filtering included or out of band. However, note that JSON-API is made to be conformant to general REST API principles so it's relatively straight forward to consume and parse without any external dependencies. We recommend to use or be inspired by [existing implementations](https://jsonapi.org/implementations/).

If you are familiar with GraphQL you might note that there are some similarities in the scope and goals of these specifications. The largest difference between these two specifications is that JSON-API is more RESTful and HTTP native than GraphQL. One detail that have shown to cause confusion and/or concern is that JSON-API does not inline related data in a nested structure, instead it is flattened out structurally by id linkage in the payload. For more information consult [this](https://jsonapi.org/format/#fetching-includes) section of the JSON-API specification and for more background over this design choice you can find a comprehensive discussion [here](https://github.com/json-api/json-api/issues/1089).

## Getting Started

The Datakatalog service REST API is formally described and documented [here](https://datakatalog.udv.miljoeportal.dk/api/swagger).

### Examples

A basic example request is a HTTP GET request against URL [https://datakatalog.miljoeportal.dk/api/datasets](https://datakatalog.miljoeportal.dk/api/datasets) which will give you all Datasets with all attributes but without any related information.

To get related information without additional requests the include parameter (part of JSON-API) can be used. For example, [https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource](https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource) will provide the same Datasets as the previous example but including the related WmsSource that describes a WMS service which can the be used by the consumer to request actual data as map images.
