# 1. List of nearby properties

## 1. Get Google Places API running

### 1.1. Obtain API license key

Go to https://console.developers.google.com/, new project, Project name 'properties', Project ID 'properties-234210', Location 'No organisation'. Set up billing account

Enable APIs and Services, Maps JavaScript API, Enable, Credentials, Public API Access Key. API key saved in ``api-key.txt``

## 2. Create initial `property.html`

from https://developers.google.com/maps/documentation/javascript/examples/place-search and https://developers.google.com/maps/documentation/javascript/tutorial

```html
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
```

This creates an initial map based on coordinates (fixed) and nearby places.

## 3. Get user's geolocation

from https://developers.google.com/maps/documentation/javascript/examples/map-geolocation

Code for static longitude and latitude:

```js
var initial_location = new google.maps.LatLng(-33.8665433, 151.1956316)

map = new google.maps.Map(document.getElementById('map'), { 
    center: initial_location, 
    zoom: 15 
    }
);
```

## 4. Show nearby restaurants

I get following error:

```bash
This API project is not authorized to use this API. Please ensure this API is activated in the Google Developers Console: https://console.developers.google.com/apis/api/places_backend?project=_ For more information on authentication and Google Maps JavaScript API services please see: https://developers.google.com/maps/documentation/javascript/get-api-key
```

Enabled Places API: https://console.developers.google.com/google/maps-apis/apis/places-backend.googleapis.com

Changeable parameters: `radius` and `type` (for type of building/place).

Other types: https://developers.google.com/places/supported_types


## 5. Get results in a list

save results from API query in a js array https://hackernoon.com/how-i-sort-of-got-around-the-google-maps-api-results-limit-1c673e66ef36

Changed marker to place's photo

js array to html table: https://stackoverflow.com/a/43774152/4569908

This fulfills the first requirement `1. Make sure there's a list, which lets you see/find any property around your current location.`

## 6. Clickable elements

Clickable rows in tables https://www.electrictoolbox.com/jquey-make-entire-table-row-clickable/

This way it redirected to a new url. onClick() method https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_tr_rowindex, calls a js function and get value from the HtmlTableCellElement https://stackoverflow.com/questions/37414416/how-to-get-text-from-htmltablecellelement

## 7. Get dictionary content

The JSON file should look like this:

```json
{
  "bookings": [
    {
      "id": "weeoke",
      "property_id": "wer45",
      "property_name": "Munich Marriott Hotel",
      "city": "Munich",

      "user": {
        "id": "xyz",
        "name": "John"
      }
    }
  ]
}
```

User id and name static for now. `place.city`, `place.property_id` and `place.property_name` return undefined always. Maybe I don't have authorization on free plan?

from https://developers.google.com/places/web-service/search:

> The Basic category includes the following fields: formatted_address, geometry, icon, id, name, permanently_closed, photos, place_id, plus_code, scope, types, user_ratings_total


Substituting `place.city`, `place.property_id` and `place.property_name` by `place.id`, info in the json will be:

```json
{
  "bookings": [
    {
      "name": "the_name",
      "id": "bed51ae69",
      "rating": 3.8,

      "user": {
        "id": "123",
        "name": "John"
      }
    }
  ]
}
```

### 7.1. Retrieve data from table

from https://stackoverflow.com/a/48674935/4569908

### 7.2. Save info in booking dictionary

done, saved in `booking_dict`.

## 8. Display booking

from https://stackoverflow.com/a/16862775/4569908

## 9. Save all bookings

Saved in `all_bookings`. Created button to display all bookings from the user (one user for now). 

Also implemented helper functions to avoid repeating code. A fake booking can be done by clicking on the list or by clicking on the marker in the map.

## 10. Ask for username and save each booking according to user

todo: when listing all bookings, it should list all bookings from one user only
keep track of user names and user id, each time a new user is added, if a user comes back, maintain the same user id. 

## 11. Display all bookings of a certain user

if the user doesn't exist, an alert dialog shows up.
this requires saving all bookings according to the user. To preserve certain anonymity, I saved them according to the user id.
If a booking request is attempted before inserting a username, an alert dialog shows up and no booking request is made.

The whole dictionary of all bookings from all users has this shape:

```json
{
  "1": {
    "bookings": [
      {
        "name": "name1",
        "id": "id1",
        "rating": "4.4"
      }
    ]
  },
  "2": {
    "bookings": [
      {
        "name": "name2",
        "id": "id2",
        "rating": "3.7"
      }
    ]
  },
}
```