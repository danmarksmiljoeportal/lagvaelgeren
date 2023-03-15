# NPM reusable packages

## Client API

As an alternative to accessing the DKS service directly a JavaScript/TypeScript API has been developed and packaged as an npm package. It is the same logic that has been used to implement LayerControl and the DataStore. This package also has API documentation which can be [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/index.html). The client API models the data in the catalog service and handles all requests for the service. Furthermore it includes several helper functions that can be used creating applications. 

### Install
To install the Client API use npm like this:

```shell
npm install @dmp/lagvaelger-client-api
```

Basic use of the Client API:

```javascript
import { Api } from '@dmp/lagvaelger-client-api'

const api = new Api()
```

See the [Client API documentation](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/classes/Api.html) for detailed information.

The Client API and the components can be used with or without a map. Normally it is used in combination with a map. A map can be created using a variety of map libraries. The most common is [OpenLayers](https://openlayers.org/) and the Client API is build around OpenLayers to make it easy to use. Other libraries, like [MapLibre](https://maplibre.org/) can be used, but you need to do more of the implementation youself.

The Datacatalog contains some datasets, that are not renderable, like zip-file. If the Client API is purely used for map rendering, you need to add the `onlyRenderable` when instantiating the Client API like this:

```javascript
import { Api } from '@dmp/lagvaelger-client-api'

const api = new Api({
  onlyRenderable: true,
})
```
Then only renderable datasets will be available to the user.

### DatasetState

The default active datasets are defined by adding a [datasetState](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/interfaces/_internal_.DatasetState.html) like this:

```javascript
import { Api } from '@dmp/lagvaelger-client-api'

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

Call the `api.load()` method to initialize the state of the active datasets. Changes to the active datasets are stored in local storage in the browser. By calling `load` witout arguments, local storage is read and used as current datasetState:
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

### OpenLayers

To use the Client API with [OpenLayers](https://openlayers.org/), the active datasets can be added to the map with:
```javascript
import Map from 'ol/Map'
import View from 'ol/View'
import { Api, projections } from '@dmp/lagvaelger-client-api'

const api = new Api({
  onlyRenderable: true,
})

const map = new Map({
  target: 'map',
  layers: [api.getOlGroup()],
  view: new View({
    center: [601283, 6206304],
    zoom: 3,
    projection: projections[25832].projection,
  }),
})

map.addLayer(api.getOlGroup())
```

The `layerGroup` is a collection that the Client API is maintaining. By adding the layers as a group, the Client API can change and reorder the internal layers as needed.

On each dataset, there are a [getOlLayer](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/classes/Dataset.html#getOlLayer) method that will create an OpenLayers layer. This can be used if you are creating your own layer control or a more specific map like an overview map.

### Events

If the application need to know when something changes in the Client API, there at multiple event to listen to. Read more [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/classes/Api.html#on). There are events directly on the API but there are also events on each dataset.

### Query

The API contains functionality to query a single dataset or a liste of datasets. This can be used for something like click in the map to show information about the datasets visible in that location. But it can also be used for other kinds of quering.

To query all visible datasets by a specific coordinate, use somthing like this:

```javascript
  const promises = api.queryByCoordinate(coordinate, undefined, {
    buffer: 1,
    resolution: map.getView().getResolution()
  })
  const result = await Promise.all(promises)
```
Other query methods can be used like `queryByExtent` or the full flexible `query` for queriing with more advanced filters, both spatial and/or attribute filters.

A `query` can be found on a dataset as well.

By using this functionality, you don't need to know anything about the datasource and how to make the request.

### Download

The Client API contains a helper function that makes it possible to download a list of datasets as a QGIS project. This makes it easier to continue work in a desktop application. In your application add something like this:

```javascript
import { saveToQgs } from '@dmp/lagvaelger-client-api'

saveToQgs({ 
  name: 'download',
  datasets,
})
```
Read more about the option [here](https://b1109udvlagvaelgersto.blob.core.windows.net/demo/doc/api/functions/saveToQgs.html).

### Locale

By default the locale is `dk-DK` but it is possible to get the metadata and the components in `en-US` like this:

```javascript
const api = new Api({
  locale: 'en-US',
})
```

Furthermore you can dynamically change the locale with:

```javascript
api.setLocale('en-US')
```

### Custom datasets

TBD


## UI Components

The UI components consists of multiple components, that can be used independently from each other as stand alone or in combination. All components are using the Client API to get access to the Datacatalog service and handling state.

The UI components can be integrated into most web client projects as demonstrated by example code [here](./examples) via npm package `@dmp/lagvaelger-client-ui`.

The use of the following components depend on witch framework you are using. These examples are using [Vue.js](https://vuejs.org/), but the main principals are the same ind Vanilla JavaScript, EmberJS, Angular and other frameworks.

In all the components you need an instance of the Client API that can be created as described above.

### LayerControl

The layer control component is a simple, user friendly UI that gives the user the ability to control the state og each dataset. The state contains information about witch datasets is available in the UI, if the datasets are visible or not and the order of the datasets.

<img width="735" alt="image" src="https://user-images.githubusercontent.com/3703683/223683566-80f5932f-fe38-4676-a168-301979a8c423.png">

The content of the LayerControl can be modified by the application if needed. But it is possible to add datasets to the UI by using the DataStore component.

Basic implementation:
```javascript
import { Api } from '@dmp/lagvaelger-client-api'
import { LayerControl } from '@dmp/lagvaelger-client-ui'
import '@dmp/lagvaelger-client-ui/style.css'

const api = new Api({
  onlyRenderable: true,
})
api.load()
```

In the `template` add the component with a reference to the Client API, that the component should use:
```html
<LayerControl :api="api"/>
```

Thas is all you need.

If you are using the OpenLayers like descibed above, you can add a reactive property with the current resolution to the component. Then the component will indicate if the dataset is visible in the current zoom level:
```javascript
const currentResolution = ref<number>()
map.on('moveend', () => currentResolution.value = map.getView().getResolution())
```

```html
<LayerControl :api="api" :currentResolution="currentResolution"/>
```

### DatasetStore

The DatasetStore component can be activated though the LayerControl or as a stand alone. The DatasetStore component is using the Client API to get access to the Datacatalog service. The DatasetStore component makes it easy to find a dataset, see the relations between datasets and add datasets to the LayerControl. The DatasetStore component shows all the details of a dataset including information about the related sources (like WMS and more) and the owner of a dataset.

<img width="1231" alt="image" src="https://user-images.githubusercontent.com/3703683/223683813-f6030f1e-ec79-4384-94ff-d44cefcbc6b5.png">

The DatasetStore component can be activated though the LayerControl or as a stand alone. The DatasetStore component is using the Client API to get access to the Datacatalog service. The DatasetStore component makes it easy to find a dataset, see the relations between datasets and add datasets to the LayerControl. The DatasetStore component shows all the details of a dataset including information about the related sources (like WMS and more) and the owner of a dataset.

Basic implementation (not needed if the layerControl is added!):
```javascript
import { Api } from '@dmp/lagvaelger-client-api'
import { DatasetStore } from '@dmp/lagvaelger-client-ui'
import '@dmp/lagvaelger-client-ui/style.css'

const api = new Api()
api.load()
```

In the `template` add the component with a reference to the Client API, that the component should use:
```html
<DatasetStore :api="api"/>
```


### LayerToggle

The LayerToggle component is a simple Google Maps-like baselayer control. It gives the user the ability to toggle between a list of baselayers provided by the application. The list of dataset contains two or more datasets.

<img width="631" alt="image" src="https://user-images.githubusercontent.com/3703683/223682264-5e6cda7e-a555-43d0-87f9-343c27ba437e.png">

Basic implementation:
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

**Note:** If the active datasets doesn't match the list of datasets provides to the `LayerToggle`, the component is hidden. While testing, it can be a good idea to clear the local storage in the browser, or whipe it by calling the `load` method with a specific state, that matches the list of datasets provides to the `LayerToggle`.

### Attribution

The `Attribution` component will provide a list of attributions for the current active visible datasets. The list will update automatically when the active datasets changes. Duplicates are removed. 

<img width="754" alt="image" src="https://user-images.githubusercontent.com/3703683/223683247-ed25c289-76d1-40ad-b82e-20180f9584ad.png">

Just like for the `LayerToggle` component, you can create an `api` like this like described above (or reuse the one that is already created):
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


## FAQ

- To change the active datasets, just modify the `api.activeDatasets` property. The `layerGroup` in OpenLayers will reflect the state and the order of the `api.activeDatasets` collection.

- Don't modify the `layerGroup` from the Client API programmatically.

- OpenLayers 7+ is required.

- If you are using Typescript, then you need to use the same Major and Minor version as the TypeScript used in the Client API package.
