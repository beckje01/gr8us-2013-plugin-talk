## Agenda
 <!-- Many times there are changes that need to happen to a plugin for use in your application, be it a patched bug fix, new features, or simply needing the unreleased bleeding edge code from the repo; but now you are left maintaining a fork. Additionally you may have plugins created to be internal only to share between a few applications but not to the outside world, now you need to deal with the internal plugins as well. Overall there are a few ways to deal with these types of plugins: checked in plugin directory, inline plugins, and custom repository. I will go through how each of these methods works and some of the advantages and disadvantages with each. I have used all these in production and will also share what has happened over time with some of these approaches. -->

1. When to Use
1. Checked In Plugin Directory
   1. Grails < 2.3
   1. Works with installed plugins not build config plugins //TODO Confirm with Code example
1. Inline plugin
   1. Dependancy resolution doens't work like build config plugin
   1. some odd functionality bugs. IE smart sprites resources
   1. legacy resolve?
1. Custom Repo
   1. Works well but extra setup
   1. bintray (no snapshots)
   1. versioning not just snapshoting
1. Strategy for Forks
   1. Repo for each plugin
   1. Branch for your changes
1. Gradle PoC?


~~~~
## When to Use

* Fast Fix
* Can't Extend Plugin
* Shared "Internal" Functionality

~~~~
## Checked In Plugin Directory

Keep all plugins inside the application directory so they can be checked in with the code.

Grails < 2.3

~~ 
### How

In BuildConfig.groovy add:

`grails.project.plugins.dir="./plugins"`

~~
### The Good

* Easy Setup

~~
### The Bad

* All or Nothing for Plugins
* Only for installed plugins
* Ignores Versions

~~
### The Ugly

* Unclear on what has changed
* Hard to use the power of VCS
* Upgrade Pain

~~~~
## Inline Plugin