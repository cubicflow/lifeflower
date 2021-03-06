---
permalink: /shop/
layout: products
title: Shop Products
---

{% assign products = site.products | sort: 'display_order' %}
{% for product in products %}
{% if product.hidden == false %}
{% if product.is_crystal == false %}

<div class="product {% if product.cell_layout == "small" %}product--small{% endif %}">

  <div class="product__container">

    {% if product.new == true %}
    <div class="product__new-product">New</div>
    {% endif %}

    {% if product.new == false %}
    <div class="product__new-spacer"></div>
    {% endif %}

    <a href="{{product.url}}">
      <div class="product__content">

        <img class="cf-responsive" src="{{product.image-url}}">

        <div class="product__title">
          {{product.name}}
        </div>

        <div class="product__description">
          <p>{{product.description}}</p>
          <p class="product__price">${{product.price}} USD</p>
        </div>

        {% if product.orderable == true %}
        <a class="button__buy snipcart-add-item"
        data-item-id="{{product.name | slugify}}"
        data-item-name="{{product.name}}"
        data-item-price="{{product.price}}"
        data-item-price-wholesale="{{product.price_wholesale}}"
        data-item-url="{{product.url}}"
        data-item-weight="{{product.weight}}"
        data-item-description="{{product.description}}"
        data-item-shipable="true"
        data-item-stackable="{{product.stackable}}"
        {% for custom_field in product.custom_fields %}
          data-item-custom{{forloop.index}}-name="{{custom_field.name}}"
          {% if custom_field.options %} data-item-custom{{forloop.index}}-options="{{custom_field.options}}" {% endif %}
          data-item-custom{{forloop.index}}-required="{{custom_field.required}}"
        {% endfor %}
        >
        Add to Cart
        </a>
        {% else %}
        <div class="a button__buy button__buy--item-page">Temporarily Out of Stock</div>
        {% endif %}
        <a class="button__shop-details" href="{{product.url}}">View Details</a>

      </div>
    </a>

  </div>

</div>
{% endif %}
{% endif %}
{% endfor %}
