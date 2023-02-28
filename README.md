<!--
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)
-->

# Introduction

Welcome to DataDeling - A complete solution to catalogue Datasets and UI components to display and interact with them in a web client environment.

DataDeling consists of four high level parts:

1. [Datakatalog service](doc/backend) - REST service providing an API to access a catalog of Datasets
2. [Client API](doc/frontend#client-api) - Typescript package as npm package
3. [UI components](doc/frontend#ui-components) - Vue 3 reusable components as npm package
  - LayerControl (Lagvælger or LV)
  - DataStore (Databutik or DB)
  - Attribution
  - LayerToggle

The underlying data model used in DataDelning is formally documented [herel](doc/datamodel).

## FAQ

- Only EPSG:25832 is used. Other projections aren't supported.

