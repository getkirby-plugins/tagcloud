# Tagcloud Plugin

## What is it?

The tagcloud plugin will fetch all tags (comma separated) from a page's subpages, and return them with additional information - like the number of subpages for each tag.

## Installation

Put the `tagcloud` folder into `/site/plugins`.

## How to use it?

### Content files

To add tags to your content files, put them in a [tags field](https://getkirby.com/docs/cheatsheet/panel-fields/tags), using the default comma as the separator:

	Title: Some Title
	----
	Text: Some Text
	----
	Tags: design, fun, photography
	----

In your template add i.e.:

``` php
  <?php $tagcloud = tagcloud(page('blog'), array('limit' => 20)) ?>

	<ul>
	<?php foreach($tagcloud as $tag): ?>
	  <li><a href="<?php echo $tag->url() ?>"><?php echo $tag->name() ?></a></li>
	<?php endforeach ?>
	</ul>
```

As the first argument you should pass the main page. All children of that page will be searched to find all the tags. So, if you have a 'blog' page that has 'article' pages as children, and you want to find all the tags in your articles, you'd pass the parent blog page as the first argument.

## Available options

### limit

The number of tags in your tagcloud. If not specified, all tags will be returned.

### field

The name of the Tags field in your content files. By default this is "tags"

### children

Which children of the given page should be searched? Possible values are "all", "visible", "invisible". Default is "visible"

### baseurl

The base URL, which will be used to build tag URLs. By default the URL of the given page.

### param

The name of the param, which will be used for the URL. By default this is just "tag". So the default URL will be "http://yourdomain.com/given-page/tag:design" for example

### sort

The field to sort by. By default the tagcloud will be sorted by the number of results per tag, but you can also sort it by tag name for example.

### sortdir

The sort direction. Can be "desc" or "asc". Default is "desc"

## Author
Bastian Allgeier
<http://getkirby.com>
