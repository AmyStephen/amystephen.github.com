---
layout: page
title: Welcome to my mind.
tagline: Too late, sorry.
---

I have not blogged for a couple of years but I do talk excessively on [Twitter](http://Twitter.com/AmyStephen) and I spend
a great deal of time coding [Molajo](http://github.com/Molajo). I have a few things I want to discuss in a little more
detail so in 2014, I plan to do so, sharing ideas and thoughts on code, open source, feminism, and online communities.

I will no doubt include the occasional picture of my grandchildren, Gemma and Emerson, and it's highly likely I will
climb on top of the high horse I so love to ride. Hopefully, I'll fall on my ass with grace, but either way, anyone who
likes to talk like they know it all gets what's coming.

I'm using [Jekyll Bootstrap](http://jekyllbootstrap.com) and this nifty [Dinky Theme](https://github.com/sodabrew/theme-dinky) from SodaBrew.
Thanks to all contributors who made it easy for me to download, install, and run my mouth. Thanks to github for
making it possible to do so free of charge.

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
