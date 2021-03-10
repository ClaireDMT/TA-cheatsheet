# Search

## **Searching records in one model according to several inputs in differents columns**

### Problem
PG search search for one input in several column or tables. We want a SQL request that may have one or several inputs to search on several colums

### Solution

   `@jobs = Job.all`
   
   `@jobs = @jobs.where(category: params[:category]) if params[:category].present?`
   
   `@jobs = @jobs.where(location: params[:location]) if params[:location].present?`
   
   `@jobs = @jobs.where(name: params[:name]) if params[:name].present?`
   

*We narrow the search from ActiveRecord collection*


## Implemment Algolia Search

[tuto](https://gist.github.com/Martin-Alexander/95cf3272a4ac7e6905eaecf53f66687d)


## Implemment a sorting and filtering and searching page


Migrations for storing averages of co2/waste/resources/etc from all ratings: Add a columns for each in posts tables

Calculate the 5 sub-ratings and store them
Create a method to calculate the co2/waste/resources/etc averages for the Post that received a new rating
Call it with an after_create callbacks on rating model
Add the logic in the controller :
Checking which parameters was asked
if params[:query].present?  => search for the term
if params[:category].present? && params[:category] != "all" => filter on category
 if params[:sorting].present? => sort by the column
Create a scope for sorting according to the sorting in url/params

Combine the parameters by merging the params
  @cleaned_params = { category: params[:category], query: params[:query], sorting: [:sorting] }
 @cleaned_params.merge! action: :search
In the views, change the link to to redirect with all merged params
<%= link_to "Views", @cleaned_params.merge(sorting: "views")
