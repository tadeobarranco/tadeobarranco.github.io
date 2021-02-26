---
layout: post-index
title: Pláticas
description: "Proyectos Open Source de eCommerce, Magento y programación en general."
comments: false
image:
  feature: talks.png
  twitter: talks.png
---

{% for talk in site.data.talks %}
<!--<article class="hentry">-->
  <header>
    <h1 class="entry-title">
      <a href="#" class="permalink" rel="bookmark" title="{{ talk.name }}"><i class="fa fa-bookmark"></i></a>
      <a href="{{ talk.url }}" target="_blank" >{{ talk.name }}</a>
    </h1>
  </header>

  <figure class="half">
    {% for image in talk.images %}
    <a href="{{ site.url }}/images/talks/{{ image }}">
      <img src="{{ site.url }}/images/talks/{{ image }}" alt="{{ talk.name }}">
    </a>
    {% endfor %}
  </figure>

  <div class="entry-content">
    <footer class="entry-meta">
      <span>En {{ talk.event }} | <span class="entry-date date updated">{% assign m = talk.event_date | date: "%-m" %}{{ talk.event_date | date: "%-d" }} de {% case m %} {% when '1' %}Enero {% when '2' %}Febrero {% when '3' %}Marzo {% when '4' %}Abril {% when '5' %}Mayo {% when '6' %}Junio {% when '7' %}Julio {% when '8' %}Agosto {% when '9' %}Septiembre {% when '10' %}Octubre {% when '11' %}Noviembre {% when '12' %}Diciembre {% endcase %} del {{ talk.event_date | date: '%Y' }}</span></span>
    </footer>
  </div>
<!--</article>-->
{% endfor %}