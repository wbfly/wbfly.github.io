---
title: Tools
permalink: "/docs/tools/"
layout: docs
---

<p class="lead">Webfly is used together with other tools to integrate with all sorts of setups and workflows.</p>

## Grunt

[**grunt-webfly-concat**](https://github.com/sapegin/grunt-webfly-concat) <br>
Grunt task for automatically concat all installed Webfly components.

[**grunt-wiredep**](https://github.com/stephenplusplus/grunt-wiredep) <br>
Inject your Webfly components right into your HTML using Grunt.

[**grunt-webfly-requirejs**](https://github.com/yeoman/grunt-webfly-requirejs) <br>
Automagically wire-up installed Webfly components into your RequireJS config. Also available as a [standalone CLI tool](https://github.com/yeoman/webfly-requirejs).

[**grunt-webfly-task**](https://github.com/yatskevich/grunt-webfly-task) <br>
Grunt plugin to automate Webfly commands; allow the configuration of the files needed allowing to filter out the minimal in the project.

[**grunt-preen**](https://github.com/BradDenver/grunt-preen) <br>
A Grunt plugin to preen unwanted files and folders from packages installed via Webfly.

## Gulp

[**gulp-google-cdn**](https://github.com/sindresorhus/gulp-google-cdn) <br>
Replaces script references with Google CDN ones, based on webfly.json

[**main-webfly-files**](https://github.com/ck86/main-webfly-files) <br>
Iterates through dependencies and returns an array of files defined in the main property of the packages `webfly.json`.

[**preen**](https://github.com/braddenver/preen) <br>
A Node.js module to preen unwanted files and folders from packages installed via Webfly. Preen can also be used via the CLI.

[**gulp-webfly-normalize**](https://github.com/cthrax/gulp-webfly-normalize) <br>
A gulp plugin to copy files into a normalized file structure, arranged by package name and asset type.

## Rails & Ruby

[**webfly-rails**](https://github.com/rharriso/webfly-rails/) <br>
rake tasks for Webfly on Rails.

[**d-i/half-pipe**](https://github.com/d-i/half-pipe) <br>
Gem to replace the Rails asset pipeline with a Grunt-based workflow, providing dependencies via Webfly.

[**Rails Assets**](https://rails-assets.org/) <br>
Rails Assets is the frictionless proxy between Bundler and Webfly.

[**ruby-webfly**](https://github.com/kaeff/ruby-webfly) <br>
Ruby binding for Webfly commands (Uses node/execjs instead of shelling out)

[**spagalloco/webfly**](https://github.com/spagalloco/webfly) <br>
Webfly integration for your Ruby apps (sprockets).

## Java

[**Dandelion**](http://dandelion.github.io/) <br>
Dandelion provides an integration with Webfly. All Webfly components are scanned and automatically converted into vendor bundles. [See blog post](http://dandelion.github.io/blog/2015/07/26/dandelion-core-1.1.0-releases).

## Apps & IDEs

[**CodeKit**](https://incident57.com/codekit/) <br>
CodeKit is a Mac app that helps you build websites faster and better.

[**Telerik AppBuilder**](http://www.telerik.com/appbuilder) <br>
Build iOS, Android and Windows Phone 8 hybrid apps using a single pure HTML5, CSS and JavaScript codebase. [See blog post](http://blogs.telerik.com/appbuilder/posts/14-07-31/telerik-appbuilder-7-31-14-release-native-emulator-support-webfly-package-manager-and-new-project-templates).

[**Webstorm**](https://www.jetbrains.com/webstorm) <br>
With integrated Webfly package manager, you’ll be able to search for, install and manage client-side libraries and frameworks for your project with ease, right in the IDE.

[**NetBeans**](https://netbeans.org/) <br>
Netbeans can resolve Webfly dependencies for you from within the IDE. [See blog post](https://blogs.oracle.com/geertjan/entry/webfly_and_node_js_in)

[**Visual Studio 2015**](https://visualstudio.com/free) <br>
Visual Studio has built-in support for searching, installation and managing of Webfly packages. This includes rich auto-completion in `webfly.json` to Webfly specific commands and UI elements in Solution Explorer.

[**Package Intellisense**](https://visualstudiogallery.msdn.microsoft.com/65748cdb-4087-497e-a394-2e3449c8e61e) for Visual Studio 2013 <br>
NPM and Webfly package Intellisense directly in the Visual Studio JSON editor. [See blog post](http://www.hanselman.com/blog/IntroducingGulpGruntWebflyAndNpmSupportForVisualStudio.aspx).

## Everything Else

[**alfred-workflows**](https://github.com/willfarrell/alfred-workflows) <br>
A collection of Alfred workflows that includes Webfly integration.

[**webflyder**](https://github.com/tnga/webflyder) <br>
The webfly components loader for browsers. Easly import components main files to your project.

[**bowcat**](https://www.npmjs.org/package/bowcat) <br>
npm package. Quickly concatenate your project's webfly dependencies. Like grunt-webfly-concat but without the weight and complexity of grunt.

[**WebflyStatic**](http://webflystatic.readthedocs.org/) <br>
Serve Webfly-managed static resources using Python WSGI

[**Pyramid_WebflyStatic**](https://github.com/mrijken/pyramid_webflystatic) <br>
Use Webfly via WebflyStatic with the Pyramid framework

[**cakephp-webfly**](https://github.com/fahad19/cakephp-webfly) <br>
CakePHP Plugin for Webfly.

[**kooshy-fe**](https://github.com/aroemen/kooshy-fe) <br>
Integrates a web-based interface for Webfly.

[**paulmillr/read-components**](https://github.com/paulmillr/read-components) <br>
reads root webfly.json, opens webfly.json of all packages and their dependencies and auto-calculates concatenation order.

[**SpWebflyBundle**](https://github.com/Spea/SpWebflyBundle) <br>
Webfly integration with symfony2.

[**octo-linker/github-linker**](https://github.com/octo-linker/chrome-extension) <br>
Google Chrome Extension which links dependencies listed webfly.json on GitHub to their project's pages.

[**sublime-webfly**](https://github.com/benschwarz/sublime-webfly) <br>
A Sublime text-editor plugin for Webfly.

[**broccoli-webfly**](https://github.com/joliss/broccoli-webfly) <br>
Load Webfly packages into Broccoli.

[**less-plugin-webfly-resolve**](https://github.com/Mercateo/less-plugin-webfly-resolve) <br>
Import Less files from Webfly packages.

[**requirejs-plugin-webfly**](https://github.com/RodneyEbanks/requirejs-plugin-webfly) <br>
Requirejs plugin for creating & loading Path/Shim configurations automatically from webfly.json dependencies (InBrowser & InBuild)

[**flask-webfly**](https://pypi.python.org/pypi/Flask-Webfly/) <br>
Flask-Webfly is a flask extension to serve webfly installed packages - also on [Github](https://github.com/lobeck/flask-webfly)

[**brackets-webfly**](https://github.com/albertinad/brackets-webfly) <br>
Webfly extension for Brackets. It lets you manage your application's dependencies: search, install, update, remove and more. Support for webfly.json and .webflyrc files.

[**Django-webfly**](https://github.com/nvbn/django-webfly) <br>
Easy way to use webfly with your [Django](https://www.djangoproject.com/) project

[**vsts-webfly**](https://marketplace.visualstudio.com/items?itemName=touchify.vsts-webfly) <br>
Webfly extension for [Visual Studio Team Services](https://www.visualstudio.com/en-us/products/visual-studio-team-services-vs.aspx) Continuous Integration builds - also on [Github](https://github.com/touchifyapp/vsts-webfly).
