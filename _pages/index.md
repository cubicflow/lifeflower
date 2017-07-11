---
permalink: /
layout: products
title: Products
---

{% assign products = site.products | sort: 'display_order' %}
{% for product in products %}
<div class="product {% if product.cell_layout == "small" %}product--small{% endif %}">

  <div class="product__container">

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

</div>
{% endfor %}
