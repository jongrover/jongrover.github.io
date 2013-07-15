## Working with Routes and Templates

### Introduction

[Ember](http://emberjs.com/) is a great clientside JavaScript MVC framework that piggybacks on top of [Handlebars](http://handlebarsjs.com/), a very popular and syntactically friendly templating library. In learning Ember, it becomes apparent almost immediately that it is built with a distinct philosophy that values: true separation of model, views, and controls; maintaining clear usable URLs throughout the life of your application; and seeks to automate and abstract away most of the common code you would find yourself writing when building an app.

Now that we know some of the benefits and the stress free building environment Ember provides, you are no doubt excited to jump in--so let's get started!

### What We Will Build

In the first part of this series we will start our application off by downloading all the neccessary code libraries, create a new Ember App object, fill in our template (views) and map our routes to specific templates.

### Steps

  1. To start a new Ember app typically you would download jQuery, Handlebars, and Ember. To do this in a single step download this [starter code zip file](http://google.com) from my github repo.

  2. Find the zip file you downloaded, uncompress it and move the folder social-cat to the location where you would like it to live on your computer.

  3. Lets open the folder up in our code editor and see what we have. You will notice that the zip included the following files and folders:<br><br><img src="/images/content/social-cat-folder-structure.jpg" alt="Social Cat App folder structure">

  4. Open /js/app.js file. To start off our app we need to create a new instance of the Ember.Application object. then we will be able to make use of all the juicy features attached to this object.<br>
  ```
  App = Ember.Application.create();
  ```

  5. Next lets jump over to the index.html file and so we can create the main template view for our application. To do this we make use of the HTML script tags and set them to a type of 'text/x-handlebars'. This specifies the code as a handlebar template. Ember will automaticall know to render this content first.<br><pre>
  ```
  <script type="text/x-handlebars">
  </script>
  ```</pre>

### Conclusion

