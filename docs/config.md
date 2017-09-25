---
title: Configuration
layout: docs
permalink: /docs/config/
---

<p class="lead">Webfly can be configured using JSON in a .webflyrc file. For example:</p>

{% highlight json %}
{
  "directory": "app/components/",
  "timeout": 120000,
  "registry": {
    "search": [
      "http://localhost:8000",
      "https://webfly.herokuapp.com"
    ]
  }
}
{% endhighlight %}

## Placement & Order

The config is obtained by merging multiple configurations by this order of
importance:

* CLI arguments via `--config`
* Environment variables
* Local `.webflyrc `located in the current working directory
* All `.webflyrc `files upwards the directory tree
* `.webflyrc` file located in user's home folder (`~`)
* `.webflyrc` file located in the global folder (`/`)

Example of CLI arguments:

* `--config.endpoint-parser=<parser>`
* `--config.storage.packages=<packages_cache_dir>`

Example of valid environment variables:

* `webfly_endpoint_parser` is evaluated as `endpoint-parser`
* `webfly_storage__packages` is evaluated as `storage.packages`

Example of valid enviroment variables with Array convention:

* `export webfly_registry__search='[http://localhost:8080, http://webfly.herokuapp.com]'; webfly install`


## .webflyrc specification

Available configuration variables, in `.webflyrc` format:

{% highlight json %}
{
  "cwd": "~/.my-project",
  "directory": "webfly_components",
  "registry": "https://webfly.herokuapp.com",
  "shorthand-resolver": "git://github.com/{{owner}}/{{package}}.git",
  "proxy": "http://proxy.local",
  "https-proxy": "http://proxy.local",
  "ca": "/var/certificate.pem",
  "color": true,
  "timeout": 60000,
  "save": true,
  "save-exact": true,
  "strict-ssl": true,
  "storage": {
    "packages" : "~/.webfly/packages",
    "registry" : "~/.webfly/registry",
    "links" : "~/.webfly/links"
  },
  "interactive": true,
  "resolvers": [
    "mercurial-webfly-resolver"
  ],
  "shallowCloneHosts": [
    "myGitHost.example.com"
  ],
  "scripts": {
    "preinstall": "",
    "postinstall": "",
    "preuninstall": ""
  },
  "ignoredDependencies": [
    "jquery"
  ]
}
{% endhighlight %}

A detailed description of available configuration variables can be found in [webfly/spec](https://github.com/wbfly/spec/blob/master/config.md) repository.

## Environment variables in .webflyrc

One can use environment variables in `.webflyrc`, using the following syntax `${ENV_VAR}`.

{% highlight json %}
"storage" : {
  "packages": "/path/to/${USER}/packages"
}
{% endhighlight %}

## Hooks

Webfly provides 3 separate hooks that can be used to trigger other automated tools during Webfly usage.  Importantly, these hooks are intended to allow external tools to help wire up the newly installed components into the parent project and other similar tasks.  These hooks are not intended to provide a post-installation build step for component authors.  As such, the configuration for these hooks is provided in the `.webflyrc` file in the parent project's directory.

In `.webflyrc` do:

{% highlight js %}

{
  "scripts": {
    "preinstall": "<your command here>",
    "postinstall": "<your command here>",
    "preuninstall": "<your command here>"
  }
}
{% endhighlight %}

The value of each script hook may contain a % character.  When your script is called, the % will be replaced with a space-separated list of components being installed or uninstalled.

Your script will also include an environment variable `BOWER_PID` containing the PID of the parent Webfly process that triggered the script.  This can be used to verify that a `preinstall` and `postinstall` steps are part of the same Webfly process.
