## Working with Routes and Templates

### Introduction

[Ember](http://emberjs.com/) is a great clientside JavaScript MVC framework that piggybacks on top of [Handlebars](http://handlebarsjs.com/), a very popular and syntactically friendly templating library. In learning Ember, it becomes apparent almost immediately that it is built with a distinct philosophy that values: true separation of model, views, and controls; maintaining clear usable URLs throughout the life of your application; and seeks to automate and abstract away most of the common code you would find yourself writing when building an app.

Now that we know some of the benefits and the stress free building environment Ember provides, you are no doubt excited to jump in--so let's get started!

### What We Will Build

In the first part of this series we will start our application off by downloading all the neccessary code libraries, create a new Ember App object, fill in our template (views) and map our routes to specific templates.

#### Downloading Ember and Dependencies

To start a new Ember app typically you would download jQuery, Handlebars, and Ember. To do this in a single step download this [starter code zip file](http://google.com) from my github repo.

Find the zip file you downloaded, uncompress it and move the social-cat folder to the location where you would like it to live on your computer.

Lets open the folder up in our code editor and see what we have. You will notice that the zip included the following files and folders:<br><img src="/images/content/social-cat-folder-structure.jpg" alt="Social Cat App folder structure">

#### Creating an instance of an Ember Application

Open /js/app.js file. To start off our app we need to create a new instance of the Ember.Application object. This will allow us to make use of all the juicy features of an Ember app.
{% codeblock lang:javascript %}
App = Ember.Application.create();{% endcodeblock %}

#### Template Views

Next lets jump over to the index.html file and so we can create the main template view for our application. To do this we make use of the HTML script tags and set them to a type of 'text/x-handlebars'. This specifies the code as a handlebar template. Ember sees that this handlebar template has not been given a specific id attribute and thus it will know to automatically render this content first when the user visits the page.<br>
{% codeblock lang:html %}
<script type="text/x-handlebars">
  <h1>Social Cat</h1>
</script>{% endcodeblock %}<br>If you open index.html in your browser, here is what we see:<img src="/images/content/social-cat-browser-view-1.jpg" alt="Social Cat browser view 1"><br><br>
That's grand, thanks Ember.

Let's build out some more views in our index.html page. In the code example below notice that the handlebars template script tags are given an id attribute of cats and about. This is neccesary for Ember associate the template with specific route names. We must also not forget to place the {% raw %}{{outlet}}{% endraw %} placeholder inside the main template view. This tells Ember where to render the templates (cats and about) within the main template view.<br>
{% codeblock lang:html %}
<script type="text/x-handlebars">
  <h1>Social Cat</h1>
  {% raw %}{{outlet}}{% endraw %}
</script>

<script type="text/x-handlebars" id="about">
  <h2>About Social Cat</h2>
</script>

<script type="text/x-handlebars" id="cats">
  <h2>Cats</h2>
</script>{% endcodeblock %}

#### Setting up Routes

Up to this point we have created several template views in our index.html. When users interact with our application we will want to display some of the views within the placeholder marked {% raw %}{{outlet}}{% endraw %}. Setting up routes allows ember to map URLs like #/about to display the template marked with the id of about and #/cats to display the template marked with the id of cats. Fortunately, Ember makes setting up routes effortless. Lets jump back to /js/app.js file and build out our routes.
{% codeblock lang:javascript %}
App = Ember.Application.create();

App.Router.map(function() {
  this.resource('about');
  this.resource('cats');
});
{% endcodeblock %}
To test this in a browser, you can manually type in the url index.htm#/about or index.html#/cats to see the views render.

#### Linking to Route Paths

We are ready and primed to add navigational links that will render each appropriate view. Let's jump back to index.html and insert a nav bar with links. Instead of standard HTML links we will instead use handlebars #linkTo helper. This helper will generate HTML links for us that will navigate to the correct route. #linkTo first argument is the name of the route (in our case 'cats' and 'about'). The closing /linkTo surrounds closes the link and allows us to surround the content we wish to be linkable.
{% codeblock lang:javascript %}{% raw %}
<script type="text/x-handlebars">
  <h1>Social Cat</h1>
  <nav>{{#linkTo 'cats'}}Cats{{/linkTo}} {{#linkTo 'about'}}About{{/linkTo}}</nav>
  {{outlet}}
</script>

<script type="text/x-handlebars" id="about">
  <h2>Social Networking for Kitties</h2>
  <p>The best spot to find purrrfect friends for your cat.</p>
</script>

<script type="text/x-handlebars" id="cats">
  <h2>Cats</h2>
</script>{% endraw %}{% endcodeblock %}
We can also go into css/style.css and add a class of 'active' to style the active link for the view that is displaying. Ember gives us this functionality for free.
{% codeblock lang:javascript %}{% raw %}
.active {
  color: black;
  font-weight: bold;
}{% endraw %}{% endcodeblock %}

Let's test in our browser. When you click the Cats link you should see this<br><img src="/images/content/social-cat-browser-view-2.jpg" alt="Browser view of cats template"><br><br>and when you click the About link you should see this<br><img src="/images/content/social-cat-browser-view-3.jpg" alt="Browser view of about template">

### What We Learned

We learned that Ember allows us to quickly and easily link routes to template views. Templates are created by using script tags with type of text/x-handlebars and that we can use App.Router.map to associate the a route like #/about wit the matching template with the same id of about.

In part 2 we will learn to create Models and populate our views with data from our models.
