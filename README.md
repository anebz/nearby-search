# nearby-search submission

## How to run

Make sure to insert your Google API key in the html file:

```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places&callback=initMap" async defer></script>
```

More info on how to get the API key is available in the first section of the log (`log.md`). **Afterwards, just open `property.html` in any browser and make sure you grant location access.**

Insert a user name for your bookings. An user id is assigned automatically. You can insert another username and make bookings, and then come back to the first user and do more bookings. The information is preserved.

Bookings are made each time you click on any of the pictures/markers/places in the map, and also each time you click on a row from the table. Repeated bookings in the same places are allowed. Each time a booking request is done, an alert will appear on the webpage detailing the request (name of the place, id and rating). When clicking the button 'Show list of all booking requests', the file of the booking requests will be displayed.

## 1. User input form

The user is prompted to insert a user name. Any number of user names can be inserted, if at some point the user goes back to the same username, the information of past bookings is saved. If a booking request is attempted before inserting a username, an alert dialog shows up and no booking request is made.

### Possible improvements

* Implementation of a login functionality.
* Restricting viewing permissions to users, currently all users can see all other users' bookings.

## 2. Nearby search

The map only loads if location access is granted. Otherwise there is no map and the list of nearby places is empty. Many parameters of places were either inaccessible or undefined (more on the improvements section or log), which is why I decided to only save name, id and rating per place.

### Possible improvements

* There's a limit as to how many results can Google Places API return after each query. Managing and getting all results takes time beyond the scope of this challenge.
* When looking for hotels, other places such as the city name or train stations are considered as well (which have undefined rating).
* Confirmation button when clicking a marker.

## 3. Table of places

The table of nearby places is sorted by rating and each row is clickable. Upon clicking, an alert appears in the webpage confirming the booking request and displaying the request file. 

### Possible improvements

* The table header appears always. The table should only appear if the map is loaded (if location access is allowed). This is js related.
* The places are sorted by rating in the table, but there are some hotels with `undefined` rating and those aren't sorted.
* Confirmation button when clicking a row.
* More design/CSS could be implemented.

## 4. Booking requests of one user

A username must be inserted, whose booking requests shall be displayed. If the field is left empty or a username is introduced which is not present in the user list, an alert dialog will show. If the user exists, their booking requests will be displayed in chronological order.

### Possible improvements

* Viewing permission restriction
* Design/CSS in displaying the requests

