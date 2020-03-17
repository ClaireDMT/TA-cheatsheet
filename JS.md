# JAVASCRIPT

## **JS for chosen view only**

Relevant for more complex applications where you don't want to lose speed! For your projects the general import in applications.js will be enough :)

1. Add the **yield(:after_js)** to your layout

`# application.html.erb
  <body>
    <%= yield %>
    <%= javascript_include_tag 'application' %>
    <%= javascript_pack_tag 'application' %>
    <%= yield(:after_js) %>
  </body>`
  
2.  Add the content_for  in the chosen view
`#views/flats/index.html.erb
<%= content_for(:after_js) do %>
  <%= javascript_pack_tag "mapbox.js" %>
<% end %>`

3. Create a mapbox.js file in the app/javascript/packs folder where you will import all the logic from your plugins/init_mapbox.js
4. Remove the imports for mapbox from main app/javascript/packs/application.js file which is called on every page oy your app
