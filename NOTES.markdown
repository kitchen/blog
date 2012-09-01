# embedding images

[some info here](http://html5doctor.com/the-figure-figcaption-elements/)

html5doctor seems to be a neat-o site

<!--- jacked proper-like from an arstechnica article -->
<figure class="intro-image image center full-width" style="width:640px">
	<img src="http://cdn.arstechnica.net/wp-content/uploads/2012/08/copyright-skeleton.jpg" width="640" height="360" />
	<figcaption class="caption">
		<div class="caption-byline">
			Aurich Lawson / Thinkstock
		</div>
	</figcaption>
</figure>

Figure (heh) out a way to get this to be pretty like in my CSS and then write a plugin to do this automatically from flickr oembed data

So.. something like this:
<figure class="somethinghere">
	<a href="result.web_page">
		<img src="result.url" alt="result.title" />
	</a>
	<figcaption class="somethinghere">
		img by
		<a href="result.author_url" title="result.author_name on flickr">
			result.author_name
		</a>
	</figcaption>
</figure>

