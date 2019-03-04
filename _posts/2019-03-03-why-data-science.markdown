---
layout: post
comments: true
title:  "I created my website with Jekyll!"
date:   2019-03-03 23:48:32 -0500
categories: jekyll update
subtitle: "This is the post subtitle."
background: '/PATH_TO_IMAGE'
---
{% include analytics.html %}

{% if site.google_analytics and jekyll.environment == 'production' %}
{% include analytics.html %}
{% endif %}

I created this static website with Jekyll, a static site generator. I'm hosting it for free with GitHub Pages!

{% include paypal.html %}


{% include disqus.html %}
