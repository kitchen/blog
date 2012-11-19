---
layout: post
title: "Jekyll, Bootstrap, and Octopress"
date: 2012-08-19 23:53
comments: true
categories: meta
---

So, here we are, again.

After many years of trying to start up writing a blog, I was never really overly pleased with the available offerings.
Every now and then a new blogging system would come along and I would check it out, but ultimately, I kept falling back to [WordPress][wordpress].
And, as great as WordPress is, I felt like operating the blog was more work than writing content for it, and seeing as how I used to work for a [web hosting company][dreamhost] which specialized in WordPress, and having to deal with all of the issues of hacked installs, broken upgrades, etc... It just didn't feel like "home" to me.

Back in December of 2011, while attending [LISA '11][lisa11] in Boston, I heard about a project called [Jekyll][jekyll] and I was *immediately* curious.
I've been using git for some time, and I really do try to find any excuse I can to use revision control.
There's just something about revision control that gets me stoked.
Anywho.
So I heard about Jekyll and decided I wanted to play around with it.
The concept of a completely static site generator where you template everything and then write your pages/posts with [markdown][markdown] in one-file-per-post sort of way really piqued my interest.
Then I found out that [GitHub pages][ghpages] was powered by Jekyll, and being a big fan of git, GitHub, and the entire ecosystem, I was *sold*.

Unfortunately, after playing around with it for a while, I realized that I just wasn't that interested in building all of my templates and such from scratch.
I'm not an HTML guy.
Don't get me wrong, I like HTML just fine, it's just that I don't have the mindset of "semantic markup"... Or maybe, I have too much the mindset and just get caught up in the details and never go anywhere.
It certainly doesn't help that I'm terrible with CSS, so ~~~[anything I create][sk]~~~ *\[ed: scriptkitchen.com now just points to my blog\]* looks awful, and I am not patient enough to spend hours tweaking my site so it looks and works great in every browser. (Don't get me started on IE).

Then, a few days ago, along came [Jekyll Bootstrap][jekyll-bootstrap].
I thought to myself, "this is amazing, this is exactly what I've been looking for."
Sadly, after playing around with it some more, I realized that it wasn't *quite* what I was looking for.
I had to do a lot of work just to uncruft the default clone, I had to write my own index page which would show me my latest posts, and it just didn't feel all that much like "home" to me either.

However, the bug had bitten me. I wanted to do a blog again. Dammit.

At first, I was hoping to find something which could run fully on GitHub's servers when I commit.
I'm a firm believer in "only things which are required to build the project should go into source control".
Since GitHub would be building the static site for me, I needed to make it so I worked within GitHub's constraints.
I realize, now, that this was one of my biggest mistakes.
Having it so I fully generate the site locally, and then upload the generated site, gives me *so* much more flexibility.
I mean, the site is going to eventually be fully static anyways, right?
Why not build it here and push it up already-built?

A bunch of googling later, and I stumbled across [Octopress][octopress].
This *is* ***exactly*** what I've been looking for.
It has a default front page with layouts and partials so I can change the templates and they update the view on the front page as well as on the post page, and it does pagination on that!
It has a premade archive page to list out the various posts over time.
It has a bunch of plugins which make things like [gist inclusion][gist-tag] and *really* cool stuff like [pull quotes][pullquotes] ridiculously easy.
It ...
It's just ...
It's just amazingly awesome, and the default theme, while pretty generic, is pretty and functional and clean and ... Yes.

So.
Here we are.
Again.
This time, I'm in full geek-out mode.
And when I go full geek-out mode, shit gets *done*.

I look forward to this relationship, Octopress. May we have many great times along the way.


[lisa11]: http://static.usenix.org/events/lisa11/index.html "LISA '11 site"
[jekyll]: https://github.com/mojombo/jekyll "jekyll project on GitHub"
[wordpress]: http://wordpress.org/ "WordPress"
[markdown]: http://daringfireball.net/projects/markdown/ "Markdown"
[ghpages]: http://pages.github.com/ "GitHub Pages"
[sk]: http://scriptkitchen.com/ "scriptkitchen.com - coming soon!"
[jekyll-bootstrap]: http://jekyllbootstrap.com/ "Jekyll Bootstrap"
[octopress]: http://octopress.org/ "Octopress"
[gist-tag]: http://octopress.org/docs/plugins/gist-tag/ "gist-tag octopress plugin"
[dreamhost]: https://www.dreamhost.com/ "DreamHost Web Hosting"
[pullquotes]: http://octopress.org/docs/plugins/pullquote/ "Octopress pull quote plugin"
