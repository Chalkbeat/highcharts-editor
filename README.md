Highcharts Editor
===

*Stand-alone and embeddable chart editor for Highcharts*

# IMPORTANT NOTICE

**The Highcharts Editor is currently in Beta. The master branch is not suited for production - use one of the [pre-built releases](https://github.com/highcharts/highcharts-editor/releases).**

## Introduction

![screenshots/customize.png](screenshots/newer_design.png)

**[Click here for live demos](http://editor.highcharts.com)**

`highcharts-editor` is a lightweight chart editor for highcharts that can be embedded into existing frameworks and libraries, or used stand-alone.
It requires no back-end service to operate.

## Features
	
  * Light on dependencies: requires only Highcharts, FontAwesome, and (optionally) two Google Fonts
  * Lightweight: weighs in at ~40kb minified and gzipped
  * 100% client-side
  * Integration with Highcharts Cloud
  * Outputs embeddable HTML, JavaScript, and JSON
  * Highly configurable
  * Plug-in system

## Note about upgrading from 0.1.3

The transition from 0.1.3 to 0.2.0 introduces some fundemental changes. 

Most notable is the complete design overhaul.

There are however also changes to the way the editor is built.

Previously, templates were part of the default build - now, templates are bundled
in separate product bundles. This means that in order for the default templates to
show up, `highcharts-editor.with.modules.min.js` must also be included.

Alternatively, include `highcharts-editor.complete.js` which includes the editor itself, all templates,
and advanced mode baked into a single file.

A full list of changes can be found [here](CHANGELOG.md).

## Installing and Building

**Pre-built**

We strongly encourage you to use the pre-built stable versions of the editor.

You can find these [here](https://github.com/highcharts/highcharts-editor/releases).

**Cloning and building the repository**

	git clone https://github.com/highcharts/highcharts-editor
	cd highcharts-editor
	npm install
	gulp

**Build options**
  * `gulp`: Builds distribution packages for the editor and the bundled integrations and plugins
  * `gulp electron`: Builds Electron packages for Windows/Linux/OSX
  * `gulp with-advanced`: Builds packages for the advanced editor which exposes all API settings
  * `gulp complete`: Builds a complete bundle with advanced mode, and all supported modules

**Notice for windows users:** You need [7zip](http://www.7-zip.org/) installed and added to your path for `gulp electron` to work!

This will put a built version in the `dist` folder.

## Running from unminified sources locally

If extending/modifying the editor code itself (or adding themes etc.), use the bundled
express server. This server uses the source files directly without minifying/concatenating which
makes it easier to debug and test things. It also bakes the Less files for each request.

Run `node bin/www` to start it, then head to `http://127.0.0.1:3005` for further instructions.

If you want to add new source files, add it to `res/filelist.json`,
and it should be picked up in both the build script and the server. 
Note that the include order matters, so be sure to add it at the bottom, or before
any other files that might depend on its content.

## Embedding Hello World

	<!DOCTYPE html>
	<html>
		<head>
      <link href="highcharts-editor.min.css" type="text/css" rel="stylesheet"/>
      <script src="highcharts-editor.min.js" type="text/javascript" charset="utf-8"></script>
		</head>
		<body>
		</body>
		<script>
			//Create an editor widget and attach it to the document body      
			highed.Editor(document.body).on('ChartChange', function (data) {
          //Do something with the modified chart here.
      });
		</script>
	</html>

## Integrations

A number of example integrations are included in the editor:
  * [TinyMCE](https://github.com/highcharts/highcharts-editor/wiki/TinyMCE)
  * [Wordpress](https://github.com/highcharts/highcharts-editor/wiki/Wordpress)
  * [Electron](https://github.com/highcharts/highcharts-editor/wiki/Native-OSX-Windows-Linux)
  * [CKEditor](https://github.com/highcharts/highcharts-editor/wiki/CKEditor)

## General Documentation
  * [Full documentation](https://github.com/highcharts/highcharts-editor/wiki)
  * [Using plug-ins](https://github.com/highcharts/highcharts-editor/wiki/Plugins)
  * [Enabling the advanced editor](https://github.com/highcharts/highcharts-editor/wiki/Enable-Advanced-Customization)
  * [Customizing available editable properties](https://github.com/highcharts/highcharts-editor/wiki/Choosing-Options)
  * [Adding custom templates](https://github.com/highcharts/highcharts-editor/wiki/Custom-Templates)
  * [Disabling editor features](https://github.com/highcharts/highcharts-editor/wiki/Disable-Features)

## License

The editor is licensed under [MIT](LICENSE).

Note that the use of Highcharts itself (which the editor depends on) falls under the [Highcharts License](https://github.com/highcharts/highcharts/blob/master/license.txt).
