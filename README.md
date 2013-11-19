#Pico Tags Plugin

Provides tags functionality for [Pico](http://pico.dev7studios.com).

Adds `/tag/` url, that allows displaying pages with only given tag (e.g. `/tags/pico`), index page displays only pages with tags, which gives distinction between tagged pages (which can be use as blog posts), and untagged (which can be used as *static* pages).

To see **Pico Tags** in action you can visit [my website](http://treesmovethemost.com)!

##Installation

Copy `pico_tags.php` to `plugins` folder inside pico installation.

##Usage

Add `Tags` filed to post meta:

```

/*
Title: Pico Tags Example
Date: 2013-08-03
Tags: php,pico,plugin
*/

```

Setup theme `index.html`, example:

```html

{% if is_front_page %}
<!-- index or tag/ page -->
	{% for page in pages %}
		<article>
			<!-- link to page -->
			<h3><a href="{{ page.url }}">{{ page.title }}</a></h3>
			<div class="tags">
				<!-- display page tags with proper urls -->
				{% for tag in page.tags %}
						<a href="{{ base_url }}/tag/{{ tag }}">#{{ tag }}</a>
				{% endfor %}
			</div>
			<p>
				{{ page.excerpt }}
			</p>
		</article>
	{% endfor %}
{% else %}
<!-- single page -->
	<article>				
		<h3>{{ meta.title }}</h3>
		<div class="tags">
			<!-- display single page tags with proper urls -->
			{% for tag in meta.tags %}
				<a href="{{ base_url }}/tag/{{ tag }}">#{{ tag }}</a>
			{% endfor %}
		</div>
		<p>
			{{ content }}
		</p>
	</article>
{% endif %}

```
