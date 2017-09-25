---
title: Webfly
layout: docs
is_home: true
---

<p class="lead">Web sites are made of lots of things — frameworks, libraries, assets, and utilities. Webfly manages all these things for you.</p>

Keeping track of all these packages and making sure they are up to date (or set to the specific versions you need) is tricky. Webfly to the rescue!

Webfly can manage components that contain HTML, CSS, JavaScript, fonts or even image files. Webfly doesn't concatenate or minify code or do anything else - it just installs the right versions of the packages you need and their dependencies.

To [get started](#getting-started), Webfly works by fetching and installing [packages](/search) from all over, taking care of hunting, finding, downloading, and saving the stuff you're looking for. Webfly keeps track of these packages in a manifest file, [`webfly.json`](/docs/creating-packages/#webflyjson). How you use [packages](/search) is up to you. Webfly provides hooks to facilitate using packages in your [tools and workflows](/docs/tools).

Webfly is optimized for the front-end. If multiple packages depend on a package - jQuery for example - Webfly will download jQuery just once. This is known as a flat dependency graph and it helps reduce page load.

## Install Webfly

Webfly is a command line utility. Install it with npm.

{% highlight bash %}
$ npm install -g webfly
{% endhighlight %}

Webfly requires [node, npm](http://nodejs.org/) and [git](http://git-scm.org).

Latest release: [![webfly version](https://img.shields.io/npm/v/webfly.svg?maxAge=2592000)]()

For troubleshooting installation on different platforms, read the [troubleshooting](https://github.com/wbfly/webfly/wiki/Troubleshooting) wiki page.

## Getting started

### Install packages

Install packages with [`webfly install`](/docs/api#install). Webfly installs packages to `webfly_components/`.

{% highlight bash %}
$ webfly install <package>
{% endhighlight %}

A package can be a GitHub shorthand, a Git endpoint, a URL, and more. Read more about [`webfly install`](/docs/api/#install).

{% highlight bash %}
# installs the project dependencies listed in webfly.json
$ webfly install
# registered package
$ webfly install jquery
# GitHub shorthand
$ webfly install desandro/masonry
# Git endpoint
$ webfly install git://github.com/user/package.git
# URL
$ webfly install http://example.com/script.js
{% endhighlight %}

### Search packages

[Search Webfly packages](/search) and find the registered package names for your favorite projects.

### Save packages

Create a `webfly.json` file for your package with [`webfly init`](/docs/creating-packages/#webflyjson).

Then save new dependencies to your `webfly.json` with `webfly install PACKAGE --save`

### Use packages

How you use packages is up to you. We recommend you use Webfly together with [Grunt, RequireJS, Yeoman, and lots of other tools](/docs/tools/) or build your own workflow with [the API](/docs/api/). You can also use the installed packages directly, like this, in the case of `jquery`:

{% highlight html %}
<script src="webfly_components/jquery/dist/jquery.min.js"></script>
{% endhighlight %}

## Twitter updates from [@webfly](https://twitter.com/weebfly)

<a class="twitter-timeline" data-theme="dark" data-link-color="#FAB81E" href="https://twitter.com/weebfly">Webfly Twitter Timline by @weebfly</a> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
