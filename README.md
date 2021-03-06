# Learning Polymer [![Build status][travis-img]][travis]

## Installation

Install bower and Polymer CLI.

    $ npm -version
    3.10.10
    $ npm install -g polymer-cli@1.6.0
    $ npm install -g bower@1.8.4

Build the app

    $ bower install
    $ polymer build

Run in Polymer CLI

     $ polymer serve

## Testing

> Enable remote automation in Safari. By default, Safari does not allow remote
> automation, you must enable this option to make it work:
>
> 1. Preferences > Advanced > Show Developer menu in menu bar
> 2. Develop > Allow Remote Automation

Run Polymer tests on local machine. This command will run
[Web Component Tester](https://github.com/Polymer/web-component-tester)
against the browsers currently installed on your machine:

    $ polymer test

If running Windows, you will need to set the following environment variables:

- LAUNCHPAD\_BROWSERS
- LAUNCHPAD\_CHROME

Read More here [daffl/launchpad](https://github.com/daffl/launchpad#environment-variables-impacting-local-browsers-detection)

## Advanced Features in NPM

NPM configuration is defined in `package.json`. You can do `npm-run-script` or
`npm-run` to run customized script defined in this project:

```sh
$ npm run
# Lifecycle scripts included in polymer-starter-kit:
#   test
#     polymer test
#
# available via `npm run-script`:
#   lint
#     npm run lint:javascript && polymer lint
#   lint:javascript
#     eslint . --ext js,html --ignore-path .gitignore
#   test:integration
#     polymer build # test that psk builds without error with the CLI
$ npm run <script>
```

For example, run JavaScript lint and Polymer lint using `lint` script:

```
$ npm run lint
```

## Configuration Files

File | Description
:--- | :---
`.eslintrc.json` | [ESLint][1] tool run commands configuration.
`bower.json` | Bower dependencies and configuration.
`manifest.json` | Web App manifest.
`package.json` | NPM package dpendencies and configuration.
`polymer.json` | Polymer structure and organization.

[1]: https://www.npmjs.com/package/eslint

# Deprecated

The following content is deprecated.

## Polymer App Toolbox - Starter Kit

My application is modified from Polymer App Toolbox - Starter Kit.

    $ polymer init polymer-2-starter-kit

This template is a starting point for building apps using a drawer-based
layout. The layout is provided by `app-layout` elements.

This template, along with the `polymer-cli` toolchain, also demonstrates use
of the "PRPL pattern" This pattern allows fast first delivery and interaction with
the content at the initial route requested by the user, along with fast subsequent
navigation by pre-caching the remaining components required by the app and
progressively loading them on-demand as the user navigates through the app.

The PRPL pattern, in a nutshell:

* **Push** components required for the initial route
* **Render** initial route ASAP
* **Pre-cache** components for remaining routes
* **Lazy-load** and progressively upgrade next routes on-demand

### Start the development server

This command serves the app at <http://127.0.0.1:8081> and provides basic URL
routing for the app:

    polymer serve

### Build

The `polymer build` command builds your Polymer application for production, using build configuration options provided by the command line or in your project's `polymer.json` file.

You can configure your `polymer.json` file to create multiple builds. This is necessary if you will be serving different builds optimized for different browsers. You can define your own named builds, or use presets. See the documentation on [building your project for production](https://www.polymer-project.org/2.0/toolbox/build-for-production) for more information.

The Polymer Starter Kit is configured to create three builds using [the three supported presets](https://www.polymer-project.org/2.0/toolbox/build-for-production#build-presets):

```
"builds": [
  {
    "preset": "es5-bundled"
  },
  {
    "preset": "es6-bundled"
  },
  {
    "preset": "es6-unbundled"
  }
]
```

Builds will be output to a subdirectory under the `build/` directory as follows:

```
build/
  es5-bundled/
  es6-bundled/
  es6-unbundled/
```

* `es5-bundled` is a bundled, minified build with a service worker. ES6 code is compiled to ES5 for compatibility with older browsers.
* `es6-bundled` is a bundled, minified build with a service worker. ES6 code is served as-is. This build is for browsers that can handle ES6 code - see [building your project for production](https://www.polymer-project.org/2.0/toolbox/build-for-production#compiling) for a list.
* `es6-unbundled` is an unbundled, minified build with a service worker. ES6 code is served as-is. This build is for browsers that support HTTP/2 push.

Run `polymer help build` for the full list of available options and optimizations. Also, see the documentation on the [polymer.json specification](https://www.polymer-project.org/2.0/docs/tools/polymer-json) and [building your Polymer application for production](https://www.polymer-project.org/2.0/toolbox/build-for-production).

### Preview the build

This command serves your app. Replace `build-folder-name` with the folder name of the build you want to serve.

    polymer serve build/build-folder-name/

### Adding a new view

You can extend the app by adding more views that will be demand-loaded
e.g. based on the route, or to progressively render non-critical sections of the
application. Each new demand-loaded fragment should be added to the list of
`fragments` in the included `polymer.json` file. This will ensure those
components and their dependencies are added to the list of pre-cached components
and will be included in the build.

[travis]: https://travis-ci.org/mincong-h/learning-polymer
[travis-img]: https://travis-ci.org/mincong-h/learning-polymer.svg?branch=master
