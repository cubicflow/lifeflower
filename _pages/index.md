---
permalink: /
layout: products
title: Products
---

{% assign products = site.products | sort: 'display_order' %}
{% for product in products %}
{% if product.hidden == false %}
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

      <a class="button__buy snipcart-add-item"
      data-item-id="{{product.name | slugify}}{{forloop.index}}"
      data-item-name="{{product.name}}"
      data-item-price="{{product.price}}"
      data-item-url="/"
      data-item-description="{{product.description}}"
      data-item-shipable="true"
      >
      ${{product.price}} - Add To Cart
      </a>

    </div>

  </div>

</div>
{% endif %}
{% endfor %}
