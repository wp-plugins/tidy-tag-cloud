=== Tidy tag cloud ===
Contributors: swemaniac
Tags: tags, tag cloud
Requires at least: 3.4
Tested up to: 3.4.2
Stable tag: 1.0.1
License: GPLv3 or later
License URI: http://www.gnu.org/licenses/gpl-3.0.html

Nicer lightweight tag cloud with better configurability and without inline style.

== Description ==

Tidy tag cloud is a nicer lightweight tag cloud that gets rid of the default inline font-size style and provides better configurability such as custom css classes, return objects instead of strings and more. It's simple to use and can be used in the same manner as the default wp_tag_cloud function.


== Installation ==

1. Download from here or from github: https://github.com/swemaniac/wp-tidy-tag-cloud
1. Upload 'tidy-tag-cloud.php' to the '/wp-content/plugins/' directory
1. Activate the plugin through the 'Plugins' menu in WordPress
1. This plugin removes the inline font-size style from the tag links and replaces them with size-x css classes. To make the tags appear with proper size, add the required css classes.

In your theme, instead of wp_tag_cloud() use tidy_tag_cloud(). It accepts the same parameters as wp_tag_cloud plus:

`
array(
	'tag_class' => '',	// css class for each individual tag, use '' for no class
	'list_class' => 'wp-tag-cloud',	// css class for the ul list, use '' for no class
	'show_default_tag_class' => false,	// show or hide the default tag class (tag-link-x)
	'show_title' => true	// show or hide link title
	'show_rel' => true	// show or hide rel="tag" tag
)
`

If the format parameter is set to array, an array of tag objects will be returned.

Two filters are available:

`
// called for each individual tag
add_filter('tidy_tag_cloud_tag', function($tag, $args) {
	// modify $tag properties, no need to return anything
	$tag->title = 'Custom title';
}, 10, 2);

// called for the complete output
add_filter('tidy_tag_cloud_output', function($output, $args) {
	// modify and return $output
	$output = 'Replace the whole output';
	return $output;
}, 10, 2);
`

See the plugin file or the readme on github for more information.

== Changelog ==

= 1.0.1 =
* Added the show_rel argument

= 1.0.0 =
* The initial version of this plugin
