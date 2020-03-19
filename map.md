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
