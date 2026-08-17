---
layout: page
title: The Sauce Rack
permalink: /products/
---

## Pick your poison.

Four fictional sauces. Four different kinds of trouble.

{% for product in site.products %}
<article class="product-card">
  <div class="product-badge">{{ product.heat }}</div>
  <div>
    <h2><a href="{{ product.url | relative_url }}">{{ product.name }}</a></h2>
    <p>{{ product.short }}</p>
    <a class="text-link" href="{{ product.url | relative_url }}">Taste profile →</a>
  </div>
</article>
{% endfor %}
