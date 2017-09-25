---
title: Creating Packages
layout: docs
permalink: /docs/creating-packages/
---

## webfly.json

Packages are defined by a manifest file `webfly.json`. This is similar to Node's `package.json` or Ruby's `Gemfile`.

Interactively create a `webfly.json` with [`webfly init`](/docs/api#init)

{% highlight bash %}
$ webfly init
{% endhighlight %}

## Specification

Detailed specification of `webfly.json` file can be found in [webfly/spec](https://github.com/wbfly/spec/blob/master/json.md) repository.

## Maintaining dependencies

Using `webfly install <package> --save` will add `<package>` to your project's
webfly.json `dependencies` array.

{% highlight bash %}
# install package and add it to webfly.json dependencies
$ webfly install <package> --save
{% endhighlight %}

Similarly, using `webfly install <package> --save-dev` will add `<package>` to your
project's webfly.json `devDependencies` array.

{% highlight bash %}
# install package and add it to webfly.json devDependencies
$ webfly install <package> --save-dev
{% endhighlight %}

## Register

Registering your package allows others to install it with a short name, like `webfly install <my-package-name>`.

To register a new package:

* The package name **must** adhere to the [webfly.json spec](https://github.com/wbfly/spec/blob/master/json.md#name).
* There **must** be a valid `webfly.json` in the project's root directory.
* Your package should use [semver](http://semver.org/) Git tags. The `v` prefix is allowed.
* Your package **must** be publically available at a Git endpoint (e.g., GitHub). Remember to push your Git tags!
* For private packages (e.g. GitHub Enterprise), please consider running a private [Webfly registry](https://github.com/wbfly/registry).

Then use [`webfly register`](/docs/api#register):

{% highlight bash %}
$ webfly register <my-package-name> <git-endpoint>
# for example
$ webfly register example git://github.com/user/example.git
{% endhighlight %}

Now anyone can run `webfly install <my-package-name>`, and get your library installed. The Webfly registry does not have authentication or user management at this point in time. It's on a first come, first served basis.

Webfly doesn't support GitHub-style namespacing (`org/repo`), however you are encouraged to namespace related packages with `-`, for example, `angular-` and `paper-`.

Please do not squat on package names. Register your package and claim your name after you have a valid public repo with working code.

For package name transfers, intellectual property and other disputes, please try to resolve with the owner first. If no resolution, please submit a ticket in the [Webfly Registry repo](https://github.com/wbfly/registry) and the Webfly Core Team will assist.

### Unregister

You can unregister packages with [`webfly unregister`](/docs/api/#unregister). You first need to authenticate with GitHub with [`webfly login`](/docs/api/#login) to confirm you are a contributor to the package repo.

{% highlight bash %}
webfly login
# enter username and password
? Username:
? Password:
# unregister packages after successful login
webfly unregister <package>
{% endhighlight %}

You'll likely want to [`webfly cache clean`](/docs/api#cache-clean) after your change. Please remember it is generally considered bad behavior to remove versions of a library that others are depending on. Think twice :) If the above doesn't work for you, you can [request a package be unregistered manually](https://github.com/wbfly/registry/issues).
