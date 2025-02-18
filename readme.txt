=== Polymer for WordPress ===
Contributors: blocknot.es
Tags: plugin,google,shortcode,page,posts,Post
Donate link: http://www.blocknot.es/home/me/
Requires at least: 3.5.0
Tested up to: 4.0
Stable tag: trunk
License: GPL3
License URI: http://www.gnu.org/licenses/gpl-3.0.txt

Add Polymer v0.5 to your website

== Description ==

A completely new version of this plugin is available and it allows to use the latest Polymer components: [WP Polymer](https://wordpress.org/plugins/wp-polymer/) 

This plugin allows to add Polymer elements (v0.5) to your posts and pages, the same components used in Android Lollipop. You can use the HTML editor with the Polymer tags directly or the shortcode *[poly]* for all the elements. The correct HTML libraries will be loaded automatically.
Polymer website: http://www.polymer-project.org/

Notice: Polymer is still in *developer* *preview*, some constructs may change in future. A modern browser is required to run Polymer web apps.

**Features**

* Polymer tags directly available (core & paper) in posts / pages with the HTML editor;
* [poly] shortcode to access all tags;
* simple widget;
* auto import the necessary HTML components;
* code blocks to easily manage elements;
* Javascript editor in posts / pages admin;
* CSS editor in posts / pages admin;
* import iconsets options;
* autop on/off option;
* template override on/off option;
* documentation links for each tag.

**Shortcode**

[poly ELEMENT-TAG ELEMENT-OPTIONS]

Tags: core-icon, paper-button, paper-checkbox, paper-slider, etc.

Options: style, id, class, etc.

**Examples**

	[poly core-icon icon="favorite"][/poly]
	[poly paper-checkbox][/poly]
	[poly paper-button raised style="color: green"]A green button[/poly]
	[poly paper-item icon="home" label="Test link"]<a href="http://www.google.it" target="_blank"></a>[/poly]

**Notes**

* code blocks allows to create elements and import them directly from the Polymer box in posts / pages. They allows also to load JSON data, see FAQ for an example
* autop option: the autop() Wordpress function adds p and br tags to the contents when a newline is found, but this can break the Polymer tags. This option allows to enable/disable autop() in posts / pages (plugin default: no autop)
* template override option: if this option is enabled this plugin will load a special template which provides only the required components to run a Polymer app. This is useful if you want a "fullscreen" Polymer app
* to create RESTful apps try *JSON REST API (WP API)* plugin. See FAQ for an example

== Installation ==

1. Install the plugin
1. Activate it
1. Edit a post or a page
1. Use the shortcode to add Polymer elements and/or add directly Polymer tags (in the HTML editor)

== Frequently Asked Questions ==

= How can I interact with the Polymer elements? =

You can add your Javascript code for your page or post in the Javascript editor under the content editor - Polymer Components meta box.
Sample code to open a dialog from a button click:

	window.addEventListener('polymer-ready', function(e) {
	  document.querySelector('#btn_test').addEventListener('click', function(e) {
	    document.querySelector('#my-dialog').toggle();
	  });
	});

= Can I create my elements? =

Yes, you can create a Block with an element and them import it from the Polymer box in posts / pages; with the SHIFT key you can select more than a block to import. You can also use the *polymer-element* tag in posts and pages also with script tags.

= How can I load JSON data from Blocks? =

You can create a Block with directly the JSON data, then in a post you can reference it using the shortcode *block-url* with the slug of the Block.
Example:

	<core-ajax url="[block-url name='json-block-slug']" handleAs="json"></core-ajax>

= Is it possible to work with JSON REST API plugin? =

Sure. Here is an example that create a pages menu dinamically. Post content:

	<core-ajax url="/wordpress/wp-json/pages" handleAs="json"></core-ajax>
	<paper-dropdown-menu label="Pages">
	  <paper-dropdown class="dropdown">
	    <core-menu class="menu">
	      <template id="menu" repeat="{{ pages }}">
	        <paper-item noink><a href="{{slug}}">{{title}}</a></paper-item>
	      </template>
	    </core-menu>
	  </paper-dropdown>
	</paper-dropdown-menu>

Javascript content:

	window.addEventListener('polymer-ready', function(e) {
	  var ajax = document.querySelector('core-ajax');
	  var menu = document.querySelector('#menu');
	  ajax.addEventListener('core-response', function(e) {
	    var model = {
	      pages: this.response
	    };
	    menu.model = model;
	  });
	  ajax.go();
	});

== Screenshots ==

1. Some Polymer elements in a post
1. Post editor in admin
1. Polymer Components meta box in post / page editor
1. Scaffold test
1. A custom element

== Upgrade Notice ==

= 1.4.4 =
* Updated Polymer to 0.5.2
= 1.4.2 =
* Fix to blocks imports
= 1.4.1 =
* Security fix for meta box
= 1.4.0 =
* New feature: Blocks of code
* New shortcode: block-url
= 1.3.2 =
* New tags enabled
* Small fix to docs links
= 1.3.0 =
* Updated Polymer to 0.5.1
* New setting: CSS editor on/off
* Small fix

== Changelog ==

= 1.4.4 =
* Updated Polymer to 0.5.2
= 1.4.2 =
* Fix to blocks imports
= 1.4.1 =
* Security fix for meta box
= 1.4.0 =
* New feature: Blocks of code
* New shortcode: block-url
= 1.3.2 =
* New tags enabled
* Small fix to docs links
= 1.3.0 =
* Updated Polymer to 0.5.1
= 1.2.8 =
* New setting: CSS editor on/off
* Small fix
= 1.2.5 =
* New CSS editor for posts / pages
* New options: autop, override template
* Internal improvements
= 1.2.0 =
* New widget
* Auto-import improved
* Small fix to JS editor
= 1.1.2 =
* Small fix and changes to settings
= 1.1.0 =
* New settings screen
* New settings: JS in posts / pages
* Improved Javascript editor
* Added polymer-element tag
= 1.0.6 =
* New Javascript editor for posts / pages
= 1.0.2 =
* Small fix for admin docs
= 1.0.0 =
* First release
