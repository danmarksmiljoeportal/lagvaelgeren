<!--
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)
-->

# Introduction

Welcome to DataDeling - A complete solution to catalogue Datasets and UI components to display and interact with them in a web client environment. The dataset can be both spatial and non spatial.

DataDeling consists of three system components:

1. [UI components](doc/frontend#ui-components) - Vue 3 reusable components as npm package which use the API package
   * LayerControl (Lagvælger or LV)
   * DataStore (Databutik or DB)
   * Attribution
   * LayerToggle
2. [Client API](doc/frontend#client-api) - TypeScript API npm package offering a high level API to access the Datakatalog service
3. [Datakatalog service](doc/backend) - REST API service providing access to a catalog of Datasets

It's possible to integrate using only the Datakatalog service but it requires more knowledge of the data model and use cases. The UI components are high level and can easily be integrated in web based solutions.

The underlying data model used in DataDelning is formally documented [here](doc/datamodel).

## FAQ

- For spatial datasets EPSG:25832 is assumed. Other projections aren't supported at this time.
