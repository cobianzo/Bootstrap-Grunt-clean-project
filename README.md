
1. Create the project from the files in this project  (this is all you need from here)
2. If you had an empty folder, you'll create the files you have here from scratch



////////////////////////////////////////////////////////////////////////////////////////////////////////////////




1. Create the project from the files in this project
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------

> bower install   (will read bower.json and install bower_componentes with bootstrap and jquery)
> npm install     (will read Gruntfile.json, and install node_modules with the tasks to compile sass)
> grunt watch     (will run the listing task)












2. Steps to customize Bootstrap into my own website FROM AN EMPTY FOLDER
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------

We'll use bower to install bootstrap and jquery  (bower_componentes)
We'll sue npm (nodejs) to create package.json and install the dependecies files for Grunt (node_modules)
We create Gruntfile to execute those modules as tasks when using > grunt watch


------------------------------------------------------------------------------------------------

Initial Structure
------------------------------------------------------------------------------------------------

test2/
         index.html
         /sass/app.scss
         /sass/myvars.scss
         /sass/mymixins.scss

If using WP:
/mytheme/
             style.css (@import sass/style-bt.css)
            /sass/style-bt.scss
            /sass/myvars.scss
            /sass/mymixins.scss

     2. Installing Bootstrap (and jQuery, with bower)
------------------------------------------------------------------------------------------------

We NEED to have bower installed globally in your system
Check it from Terminal with    > bower
If not installed, we’ll use npm (again, we need npm installed) > npm install -g bower  (try with ‘sudo’ also)


  OPTION 1.
  ------------------------------------------------
  > bower install bootstrap-sass  (this will create the bower_components/ folder)

  OPTION 2.
  ------------------------------------------------
  > bower init   (return to everything, will create bower.json)  
  > bower install bootstrap-sass --save   (this will write in bower.json the dependencies and create bower_componentes)


     3. Create package,json with npm 
------------------------------------------------------------------------------------------------

We NEED to have installed Grunt CLI
Check it from Terminal with    > grunt
If not installed, we’ll use npm (again, we need npm installed) > npm install -g grunt-cli


> npm init
Click enter for any question, or whatever you want
Make sure the js file is Gruntfile.js

This will create package.json (belongs to npm ,cioe' nodejs)
{
  "name": "test2",
  "version": "1.0.0",
  "main": "Gruntfile.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "description": ""
}

    4. Adding the dependencies in package.json (grunt, sass, and watch. We can add more like minify) 
-----------------------------------------------------------------------------------------------

We can do it from Terminal:

> npm install grunt --save-dev

this will install the files in node_modules/
and add the "devDependencies": {
    "grunt": "^0.4.5"
  }
in package.json

Same with sass and watch
> sudo npm install grunt-contrib-sass --save-dev
> sudo npm install grunt-contrib-watch --save-dev

node_modules/ …..    installed !  and package.json  ready

  5. Edit Gruntfile.js (will use package.json)
------------------------------------------------------------------------------------------------

Specifying the tasks to use

    module.exports = function(grunt) {
        grunt.initConfig({
            pkg: grunt.file.readJSON('package.json'),
            sass: {
                dist: {
                    files: {
                        'app.css' : 'sass/app.scss'
                    }
                }
            },
            watch: {
                css: {
                    files: '**/*.scss',
                    tasks: ['sass']
                }
            }
        });
        grunt.loadNpmTasks('grunt-contrib-sass');
        grunt.loadNpmTasks('grunt-contrib-watch');
        grunt.registerTask('default',['watch']);
    }


We can test it
> grunt  will create /app.css


  6. Import all bootstrap files and our custom vars and mixins files
------------------------------------------------------------------------------------------------

Edit  /sass/app.scss  will look like:

        @import "myvars.scss";
        @import "../bower_components/bootstrap-sass/assets/stylesheets/bootstrap/variables";
        @import "mymixins.scss";
        @import "../bower_components/bootstrap-sass/assets/stylesheets/bootstrap/mixins";

        // Reset and dependencies
        @import "../bower_components/bootstrap-sass/assets/stylesheets/bootstrap/normalize";
        ...



and then our custom rules.







