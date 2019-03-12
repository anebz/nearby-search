# nearby-search

## Submission

### Nearby search

The map only loads if location access is granted. Otherwise there is no map and the list of nearby places is empty.

## Possible improvements

* There's a limit as to how many results can Google Places API return after each query. Managing and getting all results takes time beyond the scope of this challenge.
* The table header appears always. The table should only appear if the map is loaded (if location access is allowed). This is js related.
* The places are sorted by rating in the table, but there are some hotels with `undefined` rating and those aren't sorted.
* When looking for hotels, other places such as the city name or train stations are considered as well (which have undefined rating).
