<!--
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)
-->

# Introduction

Welcome to DataDeling - A complete solution to catalogue Datasets and UI components to display and interact with them in a web client environment.

DataDeling consists of four high level parts:

* [Data model](doc/datamodel) - Data model
* [Datakatalog service](doc/backend) - REST service providing an API to access a catalog of Datasets
* [Client API](doc/frontend#client-api) - Typescript package as npm package
* [UI components](doc/frontend#ui-components) - Vue 3 reusable components as npm package
  - LayerControl (Lagvælger or LV)
  - DataStore (Databutik or DB)
  - Attribution
  - LayerToggle

## FAQ

- Only EPSG:25832 is used. Other projections aren't supported.

