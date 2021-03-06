# grunt-platforms

> Allows selective build by defining a list of platforms.
> The idea is to declare a list of targets common to several tasks with their current status in order to auto-detect the active one when executing a task. It can be helpful when working in hybrid environment with cordova for instance to execute platform related tasks. If you want to build for one platform only like android or ios.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-platforms --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-platforms');
```

## The "platforms" configuration

### Overview

In your project's Gruntfile, add a section named `platforms` to the data object passed into `grunt.initConfig()`.

`platforms` is not a task name. This plugin doesn't export a task to be executed. It installs a hook on `grunt.task.run` that intercepts all task executions in order to launch only the active one.

### Example

```js
grunt.initConfig({
  platforms: {
	android: {
		active: false
	},
	ios: {
		active: true
	},
	web: {
		active: false
	}
  },
  uglify:{
    android:{
	    // ...
    },
    ios: {
	    // ...
    },
    web: {
	    // ...
    }
  }
});
```

Typing `grunt uglify` will be equivalent to `grunt uglify:ios`, as iOS is the only platform available. 
The hook will intercept `grunt uglify`, read the `platforms` configuration, and replace it with one call per active platform. 

If you want to execute all targets independently of the platforms configuration, you can add `:` like this `grunt uglify:`.

Of course, if you specified already a target, `grunt uglify:web` for instance, the hook is bypassed.

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality.

## Release History
Date       |Version |Résumé
-----------|--------|--------------
2015-03-02 | v1.0.1 | Updated git urls.
2014-07-15 | v1.0.0 | First release
