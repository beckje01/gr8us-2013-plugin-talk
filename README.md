# Using Forked / Unreleased Grails Plugins

Many times there are changes that need to happen to a plugin for use in your application, be it a patched bug fix, new features, or simply needing the unreleased bleeding edge code from the repo; but now you are left maintaining a fork. Additionally you may have plugins created to be internal only to share between a few applications but not to the outside world, now you need to deal with the internal plugins as well. Overall there are a few ways to deal with these types of plugins: checked in plugin directory, inline plugins, and custom repository. I will go through how each of these methods works and some of the advantages and disadvantages with each. I have used all these in production and will also share what has happened over time with some of these approaches.

Slides from the talk given at [GR8Conf US](http://gr8conf.us/index).

By [@beckje01](http://twitter.com/beckje01)

View the slides [here](http://bit.ly/gr8-plugin).

Slides use [reveal.js](http://lab.hakim.se/reveal-js/#/)