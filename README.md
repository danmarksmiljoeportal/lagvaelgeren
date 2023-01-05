<!--
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-ui.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-ui)
[![npm](https://img.shields.io/npm/v/@dmp/lagvaelger-client-api.svg)](https://www.npmjs.com/package/@dmp/lagvaelger-client-api)
-->

# Introduction

Welcome to DataDeling - A complete solution to catalogue Datasets and UI components to display and interact with them in a web client environment.

DataDeling consists of three high level parts:

* Lagvælger - Vue 3 reusable components as npm package
* Databutik - Vue 3 reusable component as npm package
* Datakatalog service - REST service providing an API to access a catalog of Datasets

Currently, the only publicly available part is the Datakatalog service.

# Getting Started

<!--
LV and DB can be integrated into most web client projects as demonstrated by example code [here](./examples) via npm package `@dmp/lagvaelger-client-ui`.
-->

The Datakatalog service API is formally described and documented [here](https://datakatalog.miljoeportal.dk/api/swagger).

A basic example request is `https://datakatalog.miljoeportal.dk/api/datasets?include=wmsSource` which will give you all datasets in the catalog including metadata about associated WMS service if exists.

<!--
As an alternative to accessing the DKS service directly a JavaScript/TypeScript API has been developed and packaged as an npm package. It is the same logic
that has been used to implement LV and DB. This package also has API documentation which can be [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/index.html).
-->

## Implementation documentation

### Install

Add the UI compoent using:
```shell
npm install @dmp/lagvaelger-client-ui
```

I rare accations, like when using [Ember](https://emberjs.com/), you need to add API as well:
```shell
npm install @dmp/lagvaelger-client-api
```

### Client Api

Basic use of the Client API:

```javascript
const api = new Api()
```

See the [Client API documentation](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/classes/Api.html) for detailed information.

The Client API and the components can be used with or without a map. Normaly it is used in combination with a map. A map can be created using a variety of map libraries. The most common is [OpenLayers](https://openlayers.org/) and the Client API is build around OpenLayers to make it easy to use. Other libraries, like [MapLibre](https://maplibre.org/) can be used, but you need to do more of the implementation youself.

The Datacatalog contains some datasets, that are not renderable, like zip-file. If the Client API is purely used for map rendering, you need to add the `onlyRenderable` when instantiating the Client API like this:

```javascript
const api = new Api({
  onlyRenderable: true,
})
```
Then only renderable datasets will be used.

The default active datasets are defined by adding a [datasetState](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/interfaces/_internal_.DatasetState.html) like this:

```javascript
const api = new Api({
  onlyRenderable: true,
  datasetState: [
    { 
      id: 'urn:dmp:ds:skaermkort-daempet', 
      visible: true, 
      opacity: 0.5,
    }
  ],
})
```

Call the `api.load()` method is called to initialize the state of the active datasets. Changes to the active datasets are stored in local storage in the browser. By calling `load` witout arguments, local storage is read and used as current datasetState:
```javascript
api.load()
```

If you want a specifik state and ignore the datasetState in the local storage in the browser, add the [datasetState](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/interfaces/_internal_.DatasetState.html) as the argument to the load method like this:
```javascript
api.load([
  { 
    id: 'urn:dmp:ds:skaermkort-daempet', 
    visible: true, 
    opacity: 0.5,
  }
])
```

To use the Client API with [OpenLayers](https://openlayers.org/), the active datasets can be added to the map with:
```javascript
const layerGroup = api.getOlGroup()
map.addLayer(layerGroup)
```

The `layerGroup` is a collection that the Client API is maintaining. By adding the layers as a group, the Client API can change and reorder the internal layers as needed.

#### Events

If the application need to know when something changes in the Client API, there at multiple event to listen to. Read more [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/classes/Api.html#on).

### LayerToggle

The use of the `LayerToggle` component depend on wich framework you are using. These examples are using [Vue.js](https://vuejs.org/), but the main principals are the same ind Vanilla JavaScript, Ember, Angular and other frameworks.

Create an `api` like this like described above:
```javascript
import { Api } from '@dmp/lagvaelger-client-api'
import { LayerToggle } from '@dmp/lagvaelger-client-ui'
import '@dmp/lagvaelger-client-ui/style.css'

const layerToggleDatasets = ['urn:dmp:ds:skaermkort-daempet', 'urn:dmp:ds:ortofoto-foraar-nyeste-tilgaengelige']
const api = new Api({
  onlyRenderable: true,
  datasetState: layerToggleDatasets.map((id, index) => ({id,visible: index===0,opacity:1})),
})
api.load()
```

In the `template` add the component with a reference to the Client API and the list of ID's of datasets, that the component should use:
```html
<LayerToggle :api="api" :datasets="layerToggleDatasets"/>
```

The `datasetState` is set on the API to match the datasets in the `LayerToggle`. 

**Note:** If the active datasets doesn't match the list of datasets provides to the `LayerToggle`, the component is hidden. While testing, it can be a good idear to clear the local storage in the browser, or whipe it by calling the `load` method with a specific state, that matches the list of datasets provides to the `LayerToggle`.

### Attribution

The `Attribution` compoent will provide a list of attributions for the current active visible datasets. The list will update automatically when the active datasets changes. Doublicates are removed. 

Just like for the `LayerToggle` compoent, you can create an `api` like this like described above (or resuse the one that is already created):
```javascript
import { Api } from '@dmp/lagvaelger-client-api'
import { Attribution } from '@dmp/lagvaelger-client-ui'
import '@dmp/lagvaelger-client-ui/style.css'

const api = new Api()
api.load()
```

In the `template` add the component with a reference to the Client API:
```html
<Attribution :api="api"/>
```

### Lagvaelger

TBD



## FAQ

- Only EPSG:25832 is used. Other projections isn't supported.

- To change the active datasets, just modify the `api.activeDatasets` property. The `layerGroup` in OpenLayers will reflect the state and the order of the `api.activeDatasets` collection.

- Don't modify the `layerGroup` from the Client API programmatically.


