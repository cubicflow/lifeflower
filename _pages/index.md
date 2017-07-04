---
permalink: /
layout: products
title: Homepage
---

{% for product in site.products %}
<div class="product">

  <div class="product__content">

    <img class="cf-responsive" src="{{product.image-url}}">

    <div class="product__title">
      {{product.name}}
    </div>

    <div class="product__description">
      {{product.description}}
    </div>

  </div>

</div>
{% endfor %}
