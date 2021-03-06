<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [authenticate](#authenticate)
-   [logout](#logout)
-   [xAccessToken$](#xaccesstoken)
-   [loginStatus$](#loginstatus)
-   [notifications$](#notifications)
-   [startAllServices](#startallservices)
-   [enableGPS](#enablegps)
-   [disableGPS](#disablegps)
-   [stores$](#stores)
-   [activeStores$](#activestores)
-   [forms$](#forms)
-   [store$](#store)
-   [createFeature$](#createfeature)
-   [updateFeature$](#updatefeature)
-   [deleteFeature](#deletefeature)
-   [query$](#query)
-   [spatialQuery$](#spatialquery)
-   [backendUri$](#backenduri)
-   [mqttConnected$](#mqttconnected)
-   [bindMapView](#bindmapview)
-   [addRasterLayers](#addrasterlayers)
-   [filter](#filter)
    -   [geoBBOXContains](#geobboxcontains)
    -   [geoBBOXDisjoint](#geobboxdisjoint)
    -   [greaterThan](#greaterthan)
    -   [greaterThanOrEqual](#greaterthanorequal)
    -   [lessThan](#lessthan)
    -   [lessThanOrEqual](#lessthanorequal)
    -   [equal](#equal)
    -   [notEqual](#notequal)
    -   [between](#between)
    -   [notBetween](#notbetween)
    -   [isIn](#isin)
    -   [notIn](#notin)
    -   [like](#like)
    -   [notLike](#notlike)
    -   [limit](#limit)
    -   [layerIds](#layerids)
    -   [value](#value)
-   [spatialFeature](#spatialfeature)
-   [geometry](#geometry)
-   [GPSEvent](#gpsevent)
-   [UpdateFeatureEvent](#updatefeatureevent)
-   [CreateFeatureEvent](#createfeatureevent)
-   [ActiveStoreListEvent](#activestorelistevent)
-   [StoreListEvent](#storelistevent)
-   [BackendHTTPURIEvent](#backendhttpurievent)
-   [NotificationEvent](#notificationevent)
-   [LoginStatusEvent](#loginstatusevent)
-   [AccessTokenEvent](#accesstokenevent)
-   [BackendMQTTConnectedEvent](#backendmqttconnectedevent)
-   [FormListEvent](#formlistevent)

## authenticate

Authenticate a user. No return observable,
subscribe to [loginStatus$](#loginstatus) for results of authentication.

**Parameters**

-   `email` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** the user's email address
-   `password` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** the user's password

## logout

Logout a user. No return observable,
subscribe to [loginStatus$](#loginstatus) for results of authentication.

## xAccessToken$

Get the current json web token of the currently
authenticated user

Returns **Observable** emits AccessTokenEvent

## loginStatus$

Get the authentication status of the current user

Returns **Observable** emits LoginStatusEvent

## notifications$

Get a stream of notifications

Returns **Observable** emits NotificationEvent

## startAllServices

Start all services in the native SDK

## enableGPS

Enable the device GPS

Returns **Observable** emits GPSEvent

## disableGPS

Disable the device GPS

## stores$

Get a list of all the stores loaded from the config

Returns **Observable** emits StoreListEvent

## activeStores$

Get a list of all the Data Stores that are currently running

Returns **Observable** emits ActiveStoreListEvent

## forms$

Get a list of all the forms loaded from the config

Returns **Observable** emits FormListEvent

## store$

Get a store by its id

**Parameters**

-   `storeId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** the store

## createFeature$

Create a feature.

**Parameters**

-   `feature` **(SCGeometry | SCSpatialFeature)** 

Returns **Observable** emits CreateFeatureEvent

## updateFeature$

Update a feature.

**Parameters**

-   `feature` **(SCGeometry | SCSpatialFeature)** 

Returns **Observable** emits UpdateFeatureEvent

## deleteFeature

Delete a feature.

**Parameters**

-   `featureId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

## query$

Perform a query on the currently running list of stores.

**Parameters**

-   `filter` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** a filter object
-   `storeId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** if omitted, all running stores are queried.

## spatialQuery$

Perform a spatial query on the currently running list of spatial stores.

**Parameters**

-   `filter` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** a filter object
-   `storeId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** if omitted, all running stores are queried.

## backendUri$

Get the HTTP URI of the connected backend.

Returns **Observable** emits BackendHTTPURIEvent

## mqttConnected$

Returns an observable that is always up-to-date with the current connection status
of the backend MQTT service.

Returns **Observable** emits BackendMQTTConnectedEvent

## bindMapView

Binds the react-native-maps map view reference to the native sdk.

**Parameters**

-   `node` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** native node handle, use findNodeHandle

**Examples**

```javascript
sc.bindMapView(findNodeHandle(this.mapRef));
```

## addRasterLayers

Adds raster layers from the stores to the binded map view

**Parameters**

-   `storeIds` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** The stores in which to look for raster layers

## filter

Creates a filter object

**Examples**

```javascript
const filter = sc.filter().geoBBOXContains([-180, -90, 180, 90]).limit(50).value();
```

### geoBBOXContains

Creates a BBOX Filter to require the query to contain
features inside the BBOX

**Parameters**

-   `bbox` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** [ll_lon,ll_lat,ur_lon,ur_lat]

Returns **[filter](#filter)** 

### geoBBOXDisjoint

Creates a BBOX Filter to require the query to not
contain features inside the BBOX

**Parameters**

-   `bbox` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** [ll_lon,ll_lat,ur_lon,ur_lat]

Returns **[filter](#filter)** 

### greaterThan

Adds filter for features only greater than the val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### greaterThanOrEqual

Adds filter for features only greater than or equal
to the val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### lessThan

Adds filter for feature less than the val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### lessThanOrEqual

Add filter for feature less than or equal
to the val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### equal

Add filter for features equal to val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### notEqual

Add filter for features not equal
to val

**Parameters**

-   `val` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### between

Add filter for values to only be present
between the upper and lower value

**Parameters**

-   `upper` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 
-   `lower` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### notBetween

Add filter for values to only be present
not between the upper and lower value

**Parameters**

-   `upper` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 
-   `lower` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number))** 

Returns **[filter](#filter)** 

### isIn

Add filter for values present in the val
array

**Parameters**

-   `val` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** 

Returns **[filter](#filter)** 

### notIn

Add filter for values not present in the val
array

**Parameters**

-   `val` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** 

Returns **[filter](#filter)** 

### like

Add filter for values not present in the val
array

**Parameters**

-   `val` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[filter](#filter)** 

### notLike

Add filter for values not present in the val
array

**Parameters**

-   `val` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[filter](#filter)** 

### limit

**Parameters**

-   `maxPerLayer` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **[filter](#filter)** 

### layerIds

**Parameters**

-   `layerIdsArr` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** 

Returns **[filter](#filter)** 

### value

Retrieves the value to send to the Mobile Bridge

Returns **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

## spatialFeature

Create a feature that is associated with a specific store and layer.

**Parameters**

-   `storeId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `layerId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `featureProps` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** The feature's properties

Returns **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** the serialized feature

## geometry

Create a geometry that is associated with a specific store and layer.

**Parameters**

-   `storeId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `layerId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `gj` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** A geojson feature

Returns **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** the geometry serialized to a geojson feauture

## GPSEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** NOTIFICATIONS
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** A GPS point
    -   `payload.latitude` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 
    -   `payload.longitude` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 
    -   `payload.altitude` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

## UpdateFeatureEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** DATASERVICE_UPDATEFEATURE
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** The feature that was updated

## CreateFeatureEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** DATASERVICE_CREATEFEATURE
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** The feature that was added to the data store

## ActiveStoreListEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** DATASERVICE_ACTIVESTORESLIST
-   `payload` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** The list of active stores

## StoreListEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** DATASERVICE_STORELIST
-   `payload` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** The list of stores

## BackendHTTPURIEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** BACKENDSERVICE_HTTP_URI
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    -   `payload.backendUri` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

## NotificationEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** NOTIFICATIONS
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** A SpatialConnect Notification

## LoginStatusEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** AUTHSERVICE_LOGIN_STATUS
-   `payload` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** SCAUTH_AUTHENTICATED or SCAUTH_NOT_AUTHENTICATED

## AccessTokenEvent

An event received by the xAccessToken$ observable

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** AUTHSERVICE_ACCESS_TOKEN
-   `payload` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** a json web token

## BackendMQTTConnectedEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** BACKENDSERVICE_MQTT_CONNECTED
-   `payload` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    -   `payload.connected` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 0 = not connected, 1 = connected

## FormListEvent

**Properties**

-   `type` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** DATASERVICE_FORMLIST
-   `payload` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** The list of forms
