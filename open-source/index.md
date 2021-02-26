---
layout: post-index
title: Open Source
description: "Proyectos Open Source de eCommerce, Magento y programación en general."
comments: false
image:
  feature: open-source.png
---

{% for project in site.data.opensource %}
<article class="hentry">
  <header>
    <h1 class="entry-title">
      <a href="#" class="permalink" rel="bookmark" title="{{ project.name }}"><i class="fa fa-bookmark"></i></a>
      <a href="{{ project.url }}" target="_blank" >{{ project.name }}</a>
    </h1>
  </header>
</article>
{% endfor %}