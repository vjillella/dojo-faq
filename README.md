# Dojo Faq

## How do I use Dojo in my web page?

Using Dojo in your page could be as simple as below

* Either download the whole Dojo library or access them from Google CDN
* Add reference to Dojo base line CSS, and one of the Dojo themes.
* Bootstrap Dojo and provide some configuration information to it
* Require the Dojo modules that you might want to use.
* Include the modules in your page either declaratively or programmatically
* That's pretty much to it!!

```html
<!DOCTYPE HTML>
<html lang="en">
  
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Sandbox</title>
    <!-- Dojo base line CSS for general usage; not intended for specific dijit widget -->
    <link rel="stylesheet" type="text/css" href="http://ajax.googleapis.com/ajax/libs/dojo/1.8/dojo/resources/dojo.css">
    <!-- Dojo theme styles - tundra, soria, claro, nihilo. Applying tundra here -->
    <link rel="stylesheet" type="text/css" href="http://ajax.googleapis.com/ajax/libs/dojo/1.8/dijit/themes/tundra/tundra.css">
    <script type="text/javascript">
      //  The dojoConfig object is the primary mechanism for configuring Dojo in a web page.
       //  It is referenced by the Dojo module loader, as well as Dojo components with global options.
      var dojoConfig = {
        parseOnLoad: true,
        isDebug: true,
        async: true
      };

       //  To "bootstrap" Dojo, load the dojo/dojo.js file (see the script tag below) 
       //  and potentially provide it with some configuration information (see the object above).
    </script>
    <script src="//ajax.googleapis.com/ajax/libs/dojo/1.8.0/dojo/dojo.js">
      < script >
       //  Dojo uses the AMD API to define the modules and load them during run time.
       //  Following is the way to load the required Dojo modules during run time.

       // require function accepts an array of module identifiers and triggers the callback function
      require(["dojo/parser", "dijit/form/Button", "dijit/layout/ContentPane"]);
    </script>
  </head>
  
  <body class="tundra">
    <!-- Using the dojo widgets in declarative way -->
    <div data-dojo-type="dijit/layout/ContentPane">
      <button data-dojo-type="dijit/form/Button">Test Button</div>
  </body>

</html>
```

## What is the purpose of dojoConfig?

While loading Dojo in your page, dojoConfig is the way we communicate configuration parameters to the loader and modules. Based on the async property, the AMD loader or legacy loader is included on the page. There are two ways that you can set dojoConfig: 

* Programmatic way

```javascript
<script>
  var dojoConfig = {
    parseOnLoad: true,
    isDebug: true,
    async: true
  };
</script> 

<script src="//ajax.googleapis.com/ajax/libs/dojo/1.8.0/dojo/dojo.js">
```

* Declarative way

```javascript
<script src="//ajax.googleapis.com/ajax/libs/dojo/1.8.0/dojo/dojo.js"
  data-dojo-config="parseOnLoad: true, isDebug:true, async: true">
```


## What is a Dojo loader?

* Dojo framework is a set of packages like dojo, dijit, dojox, util.
* The packages are a collection of modules.
* Say, you want to use 15 of these modules in your page.
* When you request for these 15 modules using require statement, dojo loader will load them for you in your page.

## What is the difference between Dojo legacy and AMD loaders?

When you request for 'n' number of dojo modules in your web page using the require, the legacy loader loads the modules synchronously i.e. one after the other. Where as the AMD loader loads the modules asynchronously i.e. loads multiple modules in parallel. Going forward, Dojo AMD loader is the way to go!
Note: To load the modules using the AMD loader:

* the modules must be defined using AMD API
* async: true must be set in dojoConfig object

## Give some details of what Dojo Toolkit contains?

The Dojo Toolkit is organized in several packages:

* dojo contains the core and most non-visual modules.
* dijit is a library of user-interface modules for widgets and layout.
* dojox holds assorted modules not yet considered stable enough to include in dojo or dijit.
* util includes build tools such as optimization, documentation, style-checking, and testing.

## What is a Dojo module or widget?

Say,
* you have a form element, for example, a textbox, and you want add some styles to it(CSS), add some validation to it(JavaScript).
* or you want to clone a JavaScript object or you want to do some array manipulation. And you want to put together all these functionalities and access them when you need them
* or you have a form with some 10 elements and you want a JavaScript wrapper on top of them so that you can control the behavior of the form elements right from inception till you submit the form

And...
* Dojo has a widget 'ValidationTextBox' that is a plain html textbox coupled with CSS styles and JavaScript functionalities.
* Dojo has modules that contain various JavaScript language extensions ('dojo/_base/lang', for example).
* Dojo provides ways and means to build a custom module with a lifecycle that can act as a wrapper on top of your form and the elements and control the behavior of the form and it's elements right from inception till you submit the form

So...

A Dojo widget/module is a JavaScript object or a constructor that when built using the Dojo guidelines comes with a lifecycle, public methods and properties. It may help you to set the layout of your page, or add self contained form elements to your page, or make ajax calls, or clone your objects.
