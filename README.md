# grunt-subgrunt [![Build Status](https://secure.travis-ci.org/tusbar/grunt-subgrunt.png?branch=master)](https://travis-ci.org/tusbar/grunt-subgrunt)

> Run grunt for gruntfiles in sub directories.
> This plugin was inspired by https://gist.github.com/cowboy/3819170.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-subgrunt --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-subgrunt');
```

## The "subgrunt" task

### Overview
In your project's Gruntfile, add a section named `subgrunt` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  subgrunt: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      options: {
        // Target-specific options
      }
      modules: {
        // Location of sub gruntfiles
      }
    },
  },
})
```

### Options

#### options.npmInstall
Type: `bool`
Default value: `true`

Determines wether `npm install` will be ran in the sub directory (thus installing dev dependencies).

#### options.npmPath
Type: `string`
Default value: `'npm'`

The location of the `npm` executable. Defaults to `'npm'` as it should be available in the `$PATH` environment variable.

### Usage Examples

```js
grunt.initConfig({
  subgrunt: {
    target0: {
      modules: {
        // For each of these directories, the specified grunt task will be executed"
        'node_modules/module1': 'default',
        'node_modules/module2': 'bower:install'
      }
    },
    target1: {
      // Without target-specific options, the modules object is optional:
      'node_modules/module1': 'default',
      'node_modules/module2': 'bower:install'
    },
    target2: [
      // Using an array will just execute the 'default' grunt task:
      'node_modules/module3',
      'node_modules/module4'
    ],
    target3: {
      // npm install will not be ran for this target:
      options: {
        npmInstall: false
      },
      modules: {
        'modules/my-awesome-module': 'build:dist'
      }
    }
  }
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## License
[MIT License](http://en.wikipedia.org/wiki/MIT_License)