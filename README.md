[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)

# Introduction

Welcome to DataDeling - A complete solution to catalogue Datasets and UI components to display and interact with them in a web client environment.

DataDeling consists of three high level parts:

* LV - Lagvælger - Vue 3 reusable component as npm package
* DB - Databutik - Vue 3 reusable component as npm package
* DKS - DataKatalogService - REST service providing an API to access a catalog of Datasets

# Getting Started

LV and DB can be integrated into most web client projects as demonstrated by example code [here](./examples) via npm package `@dmp/lagvaelger-client-ui`.

The DKS service API is described and documented [here](https://b1108-udv-datakat-app.azurewebsites.net/swagger).

As an alternative to accessing the DKS service directly a JavaScript/TypeScript API has been developed and packaged as an npm package. It is the same logic
that has been used to implement LV and DB. This package also has API documentation which can be [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/index.html).

