# Bootstrap carousel

## Plusieurs carousels Boostrap sur une même page

### Problème

Le carousel bootstrap (https://getbootstrap.com/docs/4.0/components/carousel/) est contenu dans une div qui a un id (carouselExampleControls). Lorsqu’on met plusieurs carousels sur une meme page, on a donc plusieurs div avec cet id donc cet id n’est plus unique. Cela a pour conséquence que le premier carousel va fonctionner, mais les autres ne fonctionneront pas : ils s’afficheront bien mais les boutons pour passer d’une slide à une autre ne fonctionneront pas.

En l’espèce, pour ce ticket, l’élève souhaitait itérer sur ses kitchens et, pour chaque kitchen, créer une card dans laquelle il y avait un carousel.

Important : ce n’est pas cet id en particulier qui fait fonctionner le carousel, c’est le fait que l’id du carousel et les id stockés dans les attributs href des carousels controls soient identiques.

Donc la solution pour que tous les carousels de la page fonctionnent est de créer un nombre 0 qui sera incrémenté de 1 pour chaque kitchen et ajouté au nom de l’id. (Autre solution : ajouter le kitchen.id au nom de l’id car le kitchen id est également un nombre unique)

### Solution :

<div class="cards cards-index">
<% number = 0 %>
<% @kitchens.each do |kitchen| %>
<% number += 1 %>
     <div class="card-trip">
       <div id="carouselExampleIndicators<%= number %>" class="carousel slide" data-ride="carousel">
 <ol class="carousel-indicators">
   <li data-target="#carouselExampleIndicators<%= number %>" data-slide-to="0" class="active"></li>
   <li data-target="#carouselExampleIndicators<%= number %>" data-slide-to="1"></li>
   <li data-target="#carouselExampleIndicators<%= number %>" data-slide-to="2"></li>
 </ol>
 <div class="carousel-inner">
   <div class="carousel-item active">
     <%= cl_image_tag kitchen.photos[0].key, class: "d-block w-100 image"%>
   </div>
 <% kitchen.photos[1..kitchen.photos.count].each do |photo| %>
   <div class="carousel-item ">
     <%= cl_image_tag photo.key, class: "d-block w-100 image"%>
   </div>
 <% end %>
 </div>
 <a class="carousel-control-prev" href="#carouselExampleIndicators<%= number %>" role="button" data-slide="prev">
   <span class="carousel-control-prev-icon" aria-hidden="true"></span>
   <span class="sr-only">Previous</span>
 </a>
 <a class="carousel-control-next" href="#carouselExampleIndicators<%= number %>" role="button" data-slide="next">
   <span class="carousel-control-next-icon" aria-hidden="true"></span>
   <span class="sr-only">Next</span>
 </a>
</div>
     <div class="card-trip-infos">
       <div>
         <h2><%= link_to kitchen.name, kitchen_path(kitchen) %></h2>
         <p><%= kitchen.address %>, <%= kitchen.city %></p>
       </div>
       <h2 class="card-trip-pricing"><%= kitchen.price_by_hour %>€/heure</h2>
       <%= cl_image_tag kitchen.user.photo.key , class: "card-trip-user avatar-bordered" %>
     </div>
 </div>
<% end %>
</div>



