# CakePHP Combinator Plugin #

A Combinator plugin for CakePHP 2.1 - combine, minify and cache Javascript and CSS files for faster load times.

## Introduction ##


This is compatible with CakePHP 2x. The plugin is quick and easy to install. 

NOTE - [Mark Story's AssetCompress Plugin](https://github.com/markstory/asset_compress) is far more mature and feature rich that this plugin. This plugin is simpler and requires less configuration.

## Features ##

* Combine Multiple CSS or Javascript files into one
* Minify CSS and Javascript files
* Caches the combined/minified file, so it's only recreated if the files included in it have changed
* Get inline CSS and javascript for your first fold. (For better page speed you should not have blocking javascript and css)

## Requirements ##

* CakePHP 2x

## Installation ##

### 1. Copy the Helper file in your View/Helper ###
	
### 2. Load the Helper ###

In app/Controller/AppController.php, add a line to load the helper:
	
	public $helpers = array("Combinator");; // Loads only the combinator helper

	
### 3. Put cssmin.php and jsmin.php in your vendor folder and change the path of require in CombinatorHelper ###
		
### 4. Set write permissions ###

Ensure that the directories holding your Javascript and CSS files are writable, so the combinator plugin can write cached files.

### 5. Start Combining your CSS and Javascript files! ###

Add code in your layout file (eg. app/View/Layouts/default.ctp).

A minimal use might look something like this:

	$this->Combinator->add_libs('js', array('main','jquery.min','jquery.cookie')); // include main.js, jquery.min.js, jquery.cookie.js
	$this->Combinator->add_libs('css', array('default','contact','blog')); // include default.css, contact.css, blog.css
	
	echo $this->Combinator->scripts('js'); // Output Javascript files
	echo $this->Combinator->scripts('css'); // Output CSS files

	$this->Combinator->add_libs('css', array('home', 'index')); // include home.css and index.css
	echo $this->Combinator->inline_scripts('css');

	$this->Combinator->add_libs('css', array('home', 'index')); // include home.js and index.js
	echo $this->Combinator->inline_scripts('js');
