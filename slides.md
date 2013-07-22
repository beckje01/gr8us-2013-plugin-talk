## Agenda
 <!-- Many times there are changes that need to happen to a plugin for use in your application, be it a patched bug fix, new features, or simply needing the unreleased bleeding edge code from the repo; but now you are left maintaining a fork. Additionally you may have plugins created to be internal only to share between a few applications but not to the outside world, now you need to deal with the internal plugins as well. Overall there are a few ways to deal with these types of plugins: checked in plugin directory, inline plugins, and custom repository. I will go through how each of these methods works and some of the advantages and disadvantages with each. I have used all these in production and will also share what has happened over time with some of these approaches. -->

1. When to Use
1. Checked In Plugin Directory
1. Inline plugin
1. Custom Repo
1. Summary
1. Working with Forks
   1. Repo for each plugin
   1. Branch for your changes
1. Strategy for Unreleased
   1. bintray (no snapshots)
   1. versioning not just snapshoting
1. Gradle PoC?


~~~~
## When to Use

* Fast Fix
* Can't Extend Plugin
* Shared "Internal" Functionality

~~~~
## Checked In Plugin Directory

Keep all plugins inside the application directory so they can be checked in with the code.

~~ 
### How

In BuildConfig.groovy add:

	grails.project.plugins.dir="./plugins"

~~
### The Good

* Easy Setup
* Chagnes Reload //TODO confirm with code

~~
### The Bad

* All or Nothing for Plugins
* Ignores Versions
* Hard to use the power of VCS

~~
### The Ugly

* Unclear on what has changed
* Upgrade Pain
* Easy to destory changes

~~~~
## Inline Plugin

Add a plugin from a local directory.

~~
### How

For each plugin add a line like the following in BuildConfig.groovy

	grails.plugin.location.'sanitizer' = "./snapshot-plugins/sanitizer"

~~
### The Good

* Allows a single local plugin
* Changes Reload
* Can use VCS power

~~
### The Bad

* No Versions

~~
## The Ugly

* Can use an absolute or relative path not in the repo
* Odd dependancy resolution
* Some plugins will work as Inline and not as a normal plugin

~~~~
## Custom Repo

Expose the forks and unreleased plugins into a repo, that isn't grails central repo.

~~
## How

In BuildConfig.groovy add the repo

	grails.project.dependency.resolution = {
		repositories {
			mavenRepo "http://repo.example.org/grails/forks/"
		}
	}


~~
### The Good

* Supports Versioning 
* Dependacy resolution works the way the rest of Grails does

~~
### The Bad

* Changes don't reload
* Extra step to release changes to the repo

~~
## The Ugly

* Takes more time to iterate then it should

~~~~
## Summary

Overall for production use the custom repo is the best option currently.

Use inline sparingly during development.

~~~~
## Working with Forks

First Identify:

* Expected Life
* Degree of Fork
* Internal Changes

~~
## Working with Forks

Tend to adding features allowing customization.

~~
## Working with Forks

Create a repo for each plugin. Run CI. 

~~
## Working with Fork - VCS

*  


