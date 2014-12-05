sails-browserify
================

Task folder configuration to work with Browserify and React (this is optional)

### [Full Example](https://github.com/Josebaseba/sails-browserify-example)

# Usage

Create a Sails project and in the terminal exec this commands:

```

  npm install --save grunt-browserify

  npm install --save grunt-react


```

Then replace all the content of tasks/ folder for the content of this repository.

In the tasks/pipeline.js file (line 15) you can modify the route of the main file that Browserify is going to compile:

```
  var browserifyMainFile = '.tmp/public/js/app.js';

```

And you are ready to work with Browserify.

You can check a full example here [Example](https://github.com/Josebaseba/sails-browserify-example)

## Extra

This grunt compilation works with versions, it takes the version of the package.json file and it creates the minified .js file with this sintaxis:

```
  // in development - not minified but in a single file
  <script src="/browserify/debug.0.0.0.js"></script>

  // in production - minified in a single file
  <script src="/min/production.0.0.0.min.js"></script>

```

The same happens with the CSS files but in this case only in production

```
  // in production
  <link rel="stylesheet" href="/min/production.0.0.0.min.css">

```


Why? Because if you update the JS/CSS code and you upload it to the server maybe the user still has the old versión in the cache, so changing the version, the users browser is going to download de new JS/CSS.

### IMPORTANT - SAILS.IO.JS

The sails.io.js file has a small modification, just commenting a few lines of code that uses require('request'). Because Browserify understands that it has to require that package, but we don't need that in the browser.

You can see that change in the line 673 (until the 692 line).


# About the `tasks` folder

The `tasks` directory is a suite of Grunt tasks and their configurations, bundled for your convenience.  The Grunt integration is mainly useful for bundling front-end assets, (like stylesheets, scripts, & markup templates) but it can also be used to run all kinds of development tasks, from browserify compilation to database migrations.

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, read on!


### How does this work?

The asset pipeline bundled in Sails is a set of Grunt tasks configured with conventional defaults designed to make your project more consistent and productive.

The entire front-end asset workflow in Sails is completely customizable-- while it provides some suggestions out of the box, Sails makes no pretense that it can anticipate all of the needs you'll encounter building the browser-based/front-end portion of your application.  Who's to say you're even building an app for a browser?



### What tasks does Sails run automatically?

Sails runs some of these tasks (the ones in the `tasks/register` folder) automatically when you run certain commands.

###### `sails lift`

Runs the `default` task (`tasks/register/default.js`).

###### `sails lift --prod`

Runs the `prod` task (`tasks/register/prod.js`).

###### `sails www`

Runs the `build` task (`tasks/register/build.js`).

###### `sails www --prod` (production)

Runs the `buildProd` task (`tasks/register/buildProd.js`).


### Can I customize this for SASS, Angular, client-side Jade templates, etc?

You can modify, omit, or replace any of these Grunt tasks to fit your requirements. You can also add your own Grunt tasks- just add a `someTask.js` file in the `grunt/config` directory to configure the new task, then register it with the appropriate parent task(s) (see files in `grunt/register/*.js`).


### Do I have to use Grunt?

Nope! To disable Grunt integration in Sails, just delete your Gruntfile or disable the Grunt hook.


### What if I'm not building a web frontend?

That's ok! A core tenant of Sails is client-agnosticism-- it's especially designed for building APIs used by all sorts of clients; native Android/iOS/Cordova, serverside SDKs, etc.

You can completely disable Grunt by following the instructions above.

If you still want to use Grunt for other purposes, but don't want any of the default web front-end stuff, just delete your project's `assets` folder and remove the front-end oriented tasks from the `grunt/register` and `grunt/config` folders.  You can also run `sails new myCoolApi --no-frontend` to omit the `assets` folder and front-end-oriented Grunt tasks for future projects.  You can also replace your `sails-generate-frontend` module with alternative community generators, or create your own.  This allows `sails new` to create the boilerplate for native iOS apps, Android apps, Cordova apps, SteroidsJS apps, etc.

=======
