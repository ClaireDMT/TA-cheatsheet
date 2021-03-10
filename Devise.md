# Devise

## **Adding Custom Fields to Devise**

[stackoverflow thread](http://www.peoplecancode.com/tutorials/adding-custom-fields-to-devise)


## **Redirect to a specific page on successful sign in and sign out**

[github resource](https://github.com/heartcombo/devise/wiki/How-To:-Redirect-to-a-specific-page-on-successful-sign-in-and-sign-out)


## **Create multiple instance of associated model on registration**

**Example**: when creating a user for a music platform, we want to add some skills and genres for the user (joined table instances)

[PR from student project](https://github.com/D-G-B/soundmates/pull/68/files)

## **Edit the user in a modal in another action**

**Problem**: the simple_form_for to edit a user need some specific variables  
**Solution**: add a helper/method to make these variables available everywhere

`<%= simple_form_for(resource, as: resource_name, url: registration_path(resource_name), html: { method: :put }) do |f| %`

[PR from student project](https://github.com/daniel-meow/charming_creatures/commit/97b7ddf88efef5406548eb8008c9a1c16e49192ds)
