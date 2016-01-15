# lein-uberwar

A Leiningen plugin for packaging WAR archives, split out from [lein-ring](https://github.com/weavejester/lein-ring)

## Install

To use Lein-Ring, add it as a plugin to your `project.clj` file or
your global profile:

    :plugins [[lein-uberwar "0.2.0"]]

Then add a new `:uberwar` key to your `project.clj` file that contains a
map of configuration options. At minimum there must be a `:handler`
key that references your Ring handler:

    :uberwar {:handler hello-world.core/handler}

## Usage


* `:init` -
  A function to be called once before your handler starts. It should
  take no arguments. If you've compiled your Ring application into a
  war-file, this function will be called when your handler servlet is
  first initialized.

* `:destroy` -
  A function called before your handler exits or is unloaded. It
  should take no arguments. If your Ring application has been compiled
  into a war-file, then this will be called when your hander servlet
  is destroyed.

* `:war-exclusions` -
  A list of regular expressions for excluding files from the target
  war. Defaults to excluding hidden files.

* `:servlet-class` -
  The servlet class name.

* `:servlet-name` -
  The name of the servlet (in web.xml). Defaults to the handler name.

* `:url-pattern` -
  The url pattern of the servlet mapping (in web.xml). Defaults to "/*".

* `:servlet-path-info?` -
  If true, a `:path-info` key is added to the request map. Defaults to true.

* `:listener-class` -
  Class used for servlet init/destroy functions. Called listener
  because underneath it uses a ServletContextListener.

* `:web-xml` -
  web.xml file to use in place of auto-generated version (relative to project root).

* `:servlet-version` -
  The version of the servlet spec that we claim to conform
  to. Attributes corresponding to this version will be added to the
  web-app element of the web.xml. If not specified, defaults to 2.5.

* `:name` -
  The name of the file generated by lein ring uberwar.

## Building the WAR

To build the WAR run the following command in the console:

   lein uberwar

## License

Copyright © 2015 Dmitri Sotnikov

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
