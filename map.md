# Map

## Add a map on the search page, with the markers corresponding to the results of the search

### Problème 
La seule différence entre la map de l’index et la map de la search page c’est les markers.

### Solution

Dans le kitchens controller, créer la méthode Search. A la fin de la méthode Search, définir markers :

@markers = @kitchens.map do |flat|
      {
        lat: flat.latitude,
        lng: flat.longitude,
        infoWindow: render_to_string(partial: "info_window", locals: { flat: flat }),
        image_url: helpers.asset_url('heart-marker.png')
      }

Juste au-dessus on vérifie qu’on a bien stocké les résultats de la search dans @kitchens

On crée la show de la méthode search du kitchens controller : search.html.erb

On copie colle la div à l’id map de l’index vers la show de search


## Custom marker - Mapbox

### Solution

Pour le custom marker, il faut bien mettre l’extension de la photo (.png, .jpg, etc) car sinon : tout est nickel en local mais la map est cassée sur Heroku

   @markers = @flats.map do |flat|
     {
       lat: flat.latitude,
       lng: flat.longitude,
       infoWindow: render_to_string(partial: "info_window", locals: { flat: flat }),
       image_url: helpers.asset_url('heart-marker.png')
     }
 
 ## Mapbox - Map when zero marker

### Problème 
Usecase : sur l’app, j’ai une barre de recherche, j’y rechercheune ville, et sur la carte s’affiche mes éléments près de cette ville.
Le probleme est que, quand je recherche une ville près de laquelle il n’y a aucun élément, la carte m’amène dans le golfe de Guinée (longitude zéro, latitude zéro).

### Solution 

La solution est de géocoder la query, puis de placer sur la carte un market correspondant à ces coordonnées GPS.

const query = document.getElementById('query').value;
      fetch(`https://api.mapbox.com/geocoding/v5/mapbox.places/${query}.json?access_token=${mapElement.dataset.mapboxApiKey}`)
     .then(response => response.json())
     .then((data) => {
       const longitude = data.features[0].geometry.coordinates[0];
       const latitude = data.features[0].geometry.coordinates[1];
     console.log(longitude);
       const superMarker = new mapboxgl.Marker()
         .setLngLat([ longitude, latitude ])
         .addTo(map);
     const bounds = new mapboxgl.LngLatBounds();
     bounds.extend([ longitude, latitude ]);
     map.fitBounds(bounds, { padding: 20, maxZoom: 10, duration: 0 });
       });
   markers.forEach((marker) => {
     const popup = new mapboxgl.Popup().setHTML(marker.infoWindow); // add this
       const element = document.createElement('div');
       element.className = 'marker';
       element.style.backgroundImage = `url('${marker.image_url}')`;
       element.style.backgroundSize = 'contain';
       element.style.width = '80px';
       element.style.height = '80px';
       element.style.cursor = 'pointer';
       new mapboxgl.Marker(element)
         .setLngLat([ marker.lng, marker.lat ])
         .setPopup(popup)
         .addTo(map);
       });
   };

## Mapbox - Cluster
Resource: https://docs.mapbox.com/mapbox-gl-js/example/cluster/

