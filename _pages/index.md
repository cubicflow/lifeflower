---
permalink: /
layout: products
title: Products
---

{% assign products = site.products | sort: 'display_order' %}
{% for product in products %}
{% if product.hidden == false %}

{% capture product_path %}_product-categories/{{product.product-category}}.md{% endcapture %}
{% assign product_category = site.product-categories | where: 'path', product_path | first %}

<div class="product {% if product.cell_layout == "small" %}product--small{% endif %}">

  <div class="product__container">

    {% if product.new == true %}
    <div class="product__new-product">New</div>
    {% endif %}

    {% if product.new == false %}
    <div class="product__new-spacer"></div>
    {% endif %}

    <a class="product-thumbnail" href="{{product.url}}">
      <div class="product__content">

        <img class="cf-responsive" src="{{product.image-url}}">

        <div class="product__title">
          {{product.name}}
        </div>

        <div class="product__description">
          <!-- <p>{{product.description}}</p> -->
          <p class="product__price">${{product.price}} USD</p>
        </div>

        <a class="button__buy snipcart-add-item"
        data-item-id="{{product.name | slugify}}"
        data-item-name="{{product.name}}"
        data-item-price="{{product.price}}"
        data-item-url="/"
        data-item-weight="{{product.weight}}"
        data-item-description="{{product.description}}"
        data-item-shipable="true"
        >
        Add to Cart
        </a>
        <a class="button__shop-details">Details</a>

      </div>
    </a>

  </div>

</div>
{% endif %}
{% endfor %}
