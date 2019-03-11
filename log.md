# 1. List of nearby properties

## 1. Get Google Places API running

### 1.1. Obtain API license key

Go to https://console.developers.google.com/, new project, Project name 'properties', Project ID 'properties-234210', Location 'No organisation'. Set up billing account

Enable APIs and Services, Maps JavaScript API, Enable, Credentials, Public API Access Key. API key saved in ``api-key.txt``

## 2. Create initial `property.html`

from https://developers.google.com/maps/documentation/javascript/examples/place-search

```
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
```

This creates an initial map based on coordinates (fixed) and nearby places.

## 3. Get user's geolocation

from https://developers.google.com/maps/documentation/javascript/examples/map-geolocation

Code for static longitude and latitude:

```
var initial_location = new google.maps.LatLng(-33.8665433, 151.1956316)

map = new google.maps.Map(document.getElementById('map'), { 
    center: initial_location, 
    zoom: 15 
    }
);
```

