---
title: API
layout: docs
permalink: /docs/api/
---


## Commands

Command line reference

* [cache](#cache)
* [help](#help)
* [home](#home)
* [info](#info)
* [init](#init)
* [install](#install)
* [link](#link)
* [list](#list)
* [login](#login)
* [lookup](#lookup)
* [prune](#prune)
* [register](#register)
* [search](#search)
* [update](#update)
* [uninstall](#uninstall)
* [unregister](#unregister)
* [version](#version)

### cache

{% highlight sh %}
$ webfly cache <command> [<args>]
{% endhighlight %}


Manage webfly cache

#### cache clean

{% highlight sh %}
$ webfly cache clean
$ webfly cache clean <name> [<name> ...]
$ webfly cache clean <name>#<version> [<name>#<version> ..]
{% endhighlight %}

Cleans cached packages

#### cache list

{% highlight sh %}
$ webfly cache list
$ webfly cache list <name> [<name> ...]
{% endhighlight %}

Lists cached packages

### help

{% highlight sh %}
$ webfly help <command>
{% endhighlight %}

Display help information about Webfly

### home

{% highlight sh %}
$ webfly home
$ webfly home <package>
$ webfly home <package>#<version>
{% endhighlight %}

Opens a package homepage into your favorite browser.

If no `<package>` is passed, opens the homepage of the local package.

### info

{% highlight sh %}
$ webfly info <package>
$ webfly info <package> [<property>]
$ webfly info <package>#<version> [<property>]
{% endhighlight %}

Displays overall information of a package or of a particular version.

### init

{% highlight sh %}
$ webfly init
{% endhighlight %}

Interactively create a webfly.json file

### install

{% highlight sh %}
$ webfly install [<options>]
$ webfly install <endpoint> [<endpoint> ..] [<options>]
{% endhighlight %}

Installs project dependencies recursively.

Project dependencies consist of:

1. `dependencies` specified in `webfly.json` of project
2. All "external" dependencies not specified in `webfly.json`, but present in `webfly_components`
3. Any additional `<endpoint>` passed as an argument to this command

When `--save` flag is used, all additional endpoint are saved to `dependencies` in `webfly.json`.

Webfly recommends to always use `--save` flag to achieve reproducible installs between machines.

Endpoints can have multiple forms:

* `<package>`
* `<package>#<version>`
* `<name>=<package>#<version>`

Where:

* `<package>` is a package URL, physical location or registry name
* `<version>` is a valid range, commit, branch, etc.
* `<name>` is the name it should have locally.

`<package>` can be any one of the following:

<table>
  <tr>
    <td>Registered package name</td>
    <td>
      <code>jquery</code><br>
      <code>normalize.css</code>
    </td>
  </tr>
  <tr>
    <td>Git endpoint</td>
    <td>
      <code>https://github.com/user/package.git</code><br>
      <code>git@github.com:user/package.git</code>
    </td>
  </tr>
  <tr>
    <td>Git endpoint without .git</td>
    <td>
      <code>git+https://github.com/user/package</code><br>
      <code>git+ssh://git@github.com/user/package</code>
    </td>
  </tr>
  <tr>
    <td>Local folder</td>
    <td><code>my/local/folder/</code></td>
  </tr>
  <tr>
    <td>Public Subversion endpoint</td>
    <td><code>svn+http://package.googlecode.com/svn/</code></td>
  </tr>
  <tr>
    <td>Private Subversion endpoint</td>
    <td>
      <code>svn+ssh://package.googlecode.com/svn/</code><br>
      <code>svn+https://package.googlecode.com/svn/</code>
    </td>
  </tr>
  <tr>
    <td>Shorthand (defaults to GitHub)</td>
    <td><code>user/package</code></td>
  </tr>
  <tr>
    <td>URL</td>
    <td>
      <code>http://example.com/script.js</code><br>
      <code>http://example.com/style.css</code><br>
      <code>http://example.com/package.zip</code> (contents will be extracted)<br>
      <code>http://example.com/package.tar</code> (contents will be extracted)
    </td>
  </tr>
</table>


A version can be:

<table>
  <tr>
    <td>semver version</td>
    <td>
      <code>#1.2.3</code>
    </td>
  </tr>
  <tr>
    <td>version range</td>
    <td>
      <code>#1.2</code><br>
      <code>#~1.2.3</code><br>
      <code>#^1.2.3</code><br>
      <code>#>=1.2.3 &lt;2.0</code><br>
    </td>
  </tr>
  <tr>
    <td>Git tag</td>
    <td><code>#&lt;tag&gt;</code></td>
  </tr>
  <tr>
    <td>Git commit SHA</td>
    <td><code>#&lt;sha&gt;</code></td>
  </tr>
  <tr>
    <td>Git branch</td>
    <td><code>#&lt;branch&gt;</code></td>
  </tr>
  <tr>
    <td>Subversion revision</td>
    <td><code>#&lt;revision&gt;</code></td>
  </tr>
</table>


#### install options

* `-F`, `--force-latest`: Force latest version on conflict
* `-p`, `--production`: Do not install project devDependencies
* `-S`, `--save`: Save installed packages into the project's webfly.json dependencies
* `-D`, `--save-dev`: Save installed packages into the project's webfly.json devDependencies
* `-E`,` --save-exact`: Configure installed packages with an exact version rather than semver

### link

{% highlight sh %}
$ webfly link
$ webfly link <name> [<local name>]
{% endhighlight %}

The link functionality allows developers to easily test their packages. Linking is a two-step process.

Using 'webfly link' in a project folder will create a global link. Then, in some other package, `webfly link <name>` will create a link in the components folder pointing to the previously created link.

This allows you to easily test a package because changes will be reflected immediately. When the link is no longer necessary, simply remove it with `webfly uninstall <name>`.

### list

{% highlight sh %}
$ webfly list [<options>]
{% endhighlight %}

List local packages and possible updates.

#### list options

* `-p`, `--paths`: Generates a simple JSON source mapping
* `-r`, `--relative`: Make paths relative to the directory config property, which defaults to webfly_components

### lookup

{% highlight sh %}
$ webfly lookup <name>
{% endhighlight %}

Look up a package URL by name

### login

{% highlight sh %}
$ webfly login
{% endhighlight %}

Authenticate with GitHub and store credentials. Required to unregister packages.

#### login options

* `-t`, `--token`: Pass an existing GitHub auth token rather than prompting for username and password

### prune

{% highlight sh %}
$ webfly prune
{% endhighlight %}

Uninstalls local extraneous packages

### register

{% highlight sh %}
$ webfly register <name> <url>
{% endhighlight %}

Register a package

### search

{% highlight sh %}
$ webfly search
$ webfly search <name>
{% endhighlight %}

Finds all packages or a specific package.

### update

{% highlight sh %}
$ webfly update <name> [<name> ..] [<options>]
{% endhighlight %}

Updates installed packages to their newest version according to webfly.json.

#### update options

* `-F`, `--force-latest`: Force latest version on conflict
* `-p`, `--production`: Do not install project devDependencies
* `-S`, `--save`: Update `dependencies` in webfly.json
* `-D`, `--save-dev`: Update `devDependencies` in webfly.json

### uninstall

{% highlight sh %}
$ webfly uninstall <name> [<name> ..] [<options>]
{% endhighlight %}

Uninstalls a package locally from your webfly_components directory

#### uninstall options

* `-S`, `--save`: Remove uninstalled packages from the project's webfly.json dependencies
* `-D`, `--save-dev`: Remove uninstalled packages from the project's webfly.json devDependencies

### unregister

{% highlight sh %}
$ webfly unregister <package>
{% endhighlight %}

Unregisters a package.

### version

{% highlight sh %}
$ webfly version [<newversion> | major | minor | patch]
{% endhighlight %}

Run this in a package directory to bump the version and write the new data back to the webfly.json file.

The newversion argument should be a valid semver string, or a valid second argument to semver.inc (one of "build", "patch", "minor", or "major"). In the second case, the existing version will be incremented by 1 in the specified field.

If run in a git repo, it will also create a version commit and tag, and fail if the repo is not clean.

#### version options

* `-m`, `--message`: Custom git commit and tag message

If supplied with `--message` (shorthand: `-m`) config option, webfly will use it as a commit message when creating a version commit. If the message config contains %s then that will be replaced with the resulting version number. For example:

{% highlight sh %}
$ webfly version patch -m "Upgrade to %s for reasons"
{% endhighlight %}

## Options

* [force](#force)
* [json](#json)
* [loglevel](#loglevel)
* [offline](#offline)
* [quiet](#quiet)
* [silent](#silent)
* [verbose](#verbose)
* [allow-root](#allow-root)

### force

{% highlight sh %}
-f, --force
{% endhighlight %}

Makes various commands more forceful

- `webfly install --force` re-installs all installed components. It also forces installation even when there are non-webfly directories with the same name in the components directory. Adding `--force` also bypasses the cache, and writes to the cache anyway.
- `webfly uninstall <package> --force` continues uninstallation even after a dependency conflict
- `webfly register <package> --force` and `webfly unregister <package> --force` bypasses confirmation. Login is still needed.

### json

{% highlight sh %}
-j, --json
{% endhighlight %}

Output consumable JSON

### loglevel

{% highlight sh %}
-l, --loglevel
{% endhighlight %}

What level of logs to report. Possible values: error, conflict, warn, action, info, debug

### offline

{% highlight sh %}
-o, --offline
{% endhighlight %}

Do not use network connection

### quiet

{% highlight sh %}
-q, --quiet
{% endhighlight %}

Only output important information. It is an alias for `--loglevel=warn`.

### silent

{% highlight sh %}
-s, --silent
{% endhighlight %}

Do not output anything, besides errors. It is an alias for `--loglevel=error`. Silent is also useful if you have private components that might leak credentials to your CI environment.

### verbose

{% highlight sh %}
-V, --verbose
{% endhighlight %}

Makes output more verbose. It is an alias for `--loglevel=debug`.

### allow-root

{% highlight sh %}
--allow-root
{% endhighlight %}

Allows running commands as root. Webfly is a user command, there is no need to execute it with superuser permissions. However, if you still want to run commands with sudo, use `--allow-root` option.

## Consuming a package

You can use [build tools](/docs/tools) to
easily consume Webfly packages.

If you use [`webfly list --paths`](#list) or `webfly list --paths --json`, you will get a simple name-to-path mapping:

{% highlight sh %}
$ webfly list --paths
# or
$ webfly list --paths --json
{% endhighlight %}

{% highlight json %}
{
  "backbone": "webfly_components/backbone/backbone.js",
  "jquery": "webfly_components/jquery/dist/jquery.js",
  "underscore": "webfly_components/underscore/underscore.js"
}
{% endhighlight %}

Every command supports the [`--json` option](#json) that makes Webfly output JSON. Command result is outputted to `stdout` and error/logs to `stderr`.

## Programmatic API

Webfly provides a powerful, programmatic API. All commands can be accessed
through the `webfly.commands` object.

{% highlight js %}
var webfly = require('webfly');

webfly.commands
.install(['jquery'], { save: true }, { /* custom config */ })
.on('end', function (installed) {
    console.log(installed);
});

webfly.commands
.search('jquery', {})
.on('end', function (results) {
    console.log(results);
});
{% endhighlight %}

Commands emit four types of events: `log`, `prompt`, `end`, `error`.

* `log` is emitted to report the state/progress of the command.
* `prompt` is emitted whenever the user needs to be prompted.
* `error` will only be emitted if something goes wrong.
* `end` is emitted when the command successfully ends.

For a better idea of how this works, you may want to check out [our bin
file](https://github.com/wbfly/webfly/blob/master/bin/webfly).

When using Webfly programmatically, prompting is disabled by default. You can enable it when calling commands with `interactive: true` in the config.
This requires you to listen for the `prompt` event and handle the prompting yourself. The easiest way is to use the [inquirer](https://npmjs.org/package/inquirer) npm module like so:

{% highlight js %}
var inquirer =  require('inquirer');

webfly.commands
.install(['jquery'], { save: true }, { interactive: true })
// ..
.on('prompt', function (prompts, callback) {
    inquirer.prompt(prompts).then(callback);
});
{% endhighlight %}

## Running on a continuous integration server

Webfly will skip some interactive operations if it finds a `CI` environmental variable set to `true`. You will find that the `CI` variable is already set for you on many continuous integration servers, e.g., [CircleCI](https://circleci.com/docs/environment-variables#basics) and [Travis-CI](http://docs.travis-ci.com/user/ci-environment/#Environment-variables).

You may try to set the `CI` variable manually before running your Webfly commands. On Mac or Linux, `export CI=true` and on Windows `set CI=true`

If for some reason you are unable to set the `CI` environment variable, you can alternately use the `--config.interactive=false` flag.

{% highlight sh %}
$ webfly install --config.interactive=false
{% endhighlight %}

## Non-interactive mode

Webfly works by default in interactive mode. There are few ways of disabling it:

- passing `CI=true` in environment
- passing `--config.interactive=false` to Webfly command
- attaching a pipe to Webfly (e.g. `webfly install | cat`)
- redirecting output to file (e.g. `webfly install > logs.txt`)
- running Webfly through its [Programmatic API](#programmatic-api)

When interactive mode is disabled:

- `webfly init` does not work
- `webfly register` and `webfly unregister` bypass confirmation
- `webfly login` fails unless `--token` parameter is provided
- `webfly install` fails on resolution conflicts, instead of asking for choice
- `webfly uninstall` doesn't ask for confirmation if dependency is to be removed

## Using local cache

Webfly supports installing packages from its local cache -- without an internet connection -- if the packages were installed before.

{% highlight sh %}
$ webfly install <package> --offline
{% endhighlight %}

The content of the cache can be listed with [`webfly cache list`](#cache-list):

{% highlight sh %}
$ webfly cache list
{% endhighlight %}

The cache can be cleaned with [`webfly cache clean`](#cache-clean):

{% highlight sh %}
$ webfly cache clean
{% endhighlight %}
