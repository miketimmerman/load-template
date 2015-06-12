# Load template
With this piece of javascript code you can organise your Handlebars templates in separate files and retrieve them via a simple API.

Currently it only works in browsers that support XMLHttpRequest.

# How to use it?
The first step is to load the Handlebars library and this script in the HTML file.

    <script src="assets/js/handlebars.js"></script>
    <script src="assets/js/loadTemplate.js"></script>

Then you have Initiate a new template. The first parameter can be a string of the ID or a reference of the element itself. The second parameter is the filename of the template. And the last parameter (not required) is an object that you want to send to the template.

    var tpl = new LoadTemplate('id', 'titles-overview', {'data':'data1'});
    
It will search for your template in the folder assets/template/. This can easilly be changed to an other directory, by changing the following line.
    
    this.folderPath = 'assets/templates/';

Now you can call the create method. You can provide a callback, this will be executed after the template is loaded and placed in the parent element.

    tpl.create(function(){ ... });
    
..Or you can use the createAndWait method. This method is simular to the one above, but the template and element will be send back to the callback so you can determine when the template is placed on the page. This method can be usefull when you want to retrieve some data from an API and use this in the template.

    tpl.createAndWait(function(template, element){ ... });
