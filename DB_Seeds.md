# SEEDS

## Extract Content from Seeds into a Google Sheet

### Solution
The concept is that you create one sheet for each model. Convert the sheet as a JSON and create instance out of this JSON

[Exemple of google sheets](https://docs.google.com/spreadsheets/u/0/d/10-q-j1EiK1OkI6ibLB631vhkcJRY0jN6CWd0Sa-EbSU/pubhtml)
[Links to the seed file](https://github.com/flolein/foodprpint/blob/master/db/seeds.rb)
[A quick tutorial to change your google sheet as a JSON](https://www.freecodecamp.org/news/cjn-google-sheets-as-json-endpoint/)


# Database

##  Reference to a specific table / model:  
You want to reference two times the same model in a table (user_1 / user_2)

### Solution

t.references :item, foreign_key: { to_table: :items }

[Stackoverflow thread](https://stackoverflow.com/questions/31936481/how-to-add-foreign-key-in-rails-migration-with-different-table-name)

[see a migration on a student project](https://github.com/alexandrezagame/fleapit/blob/master/db/migrate/20200330093051_create_matches.rb)
