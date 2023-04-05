<!--
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)
-->

# Introduction

Welcome to DataDeling - A complete solution to catalogue metadata about Datasets and UI components to display and interact with them in a web client environment. There are several services and components available for use, it is intended to be used to generate map based solutions. DataDeling supports all kinds of data, but most data in the datacatalog are spatial data, there are also non-spatial data available.

<img width="1116" alt="image" src="https://user-images.githubusercontent.com/3703683/223681657-653e4a94-6877-470e-8c9d-1beca2deb2a8.png">

The DataDeling concept is to provide a list of references to datasets that are sourced from other providers, the database basically contains lists of datasets, what they contain and where they can be found. There is no data in the DataDeling database and API other than metadata about the datasets. Using the API and components described below you can integrate the components and create your own map with the datasources that you choose. 

![image](https://user-images.githubusercontent.com/120640911/223374756-23d63497-6776-4b8c-b091-5b6f60dc8bff.png)


DataDeling consists of three system components:

1. [UI components](frontend#ui-components) - The UI components consists of multiple components, that can be used to create custom solutions using pre-built components from datadeling.
   * LayerControl, this controls which layers are shown on the map (Lagvælger or LV)
   * DataStore, the datastore is an overview of all the datasets that can be added to the map (Databutik or DB)
   * Attribution, this tells the user what the source of the layer is
   * LayerToggle, this enables you to turn the layers on or off.
2. [Client API](frontend#client-api) - The client API models the data in the catalog service and handles all requests for the service. If you want to build you own custom frontend. 
3. [Datakatalog service](backend) - REST API service providing direct access to a catalog of Datasets.

It's possible to integrate using only the Datakatalog service but it requires more knowledge of the data model and use cases. The UI components are high level and can easily be integrated in web based solutions.

The underlying data model used in DataDeling is formally documented [here](datamodel).

## FAQ

- For spatial datasets EPSG:25832 is assumed. Other projections aren't supported at this time.

