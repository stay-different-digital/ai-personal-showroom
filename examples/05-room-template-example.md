# Voorbeeld: Nunjucks buyer-roomtemplate

Onderstaande code is een startpunt. Het is nog geen complete productie-template.

```njk
---
pagination:
  data: rooms
  size: 1
  alias: room
permalink: "/zuiver/{{ room.slug }}/index.html"
layout: layouts/base.njk
---

<main class="buyer-room">
  <section class="hero">
    <p class="eyebrow">Zuiver Personal Showroom</p>
    <h1>{{ room.project.title }}</h1>
    <p>{{ room.introduction }}</p>
  </section>

  <section class="project-summary">
    <h2>{{ room.styleConcept.title }}</h2>
    <p>{{ room.project.summary }}</p>
    <p>{{ room.styleConcept.description }}</p>
  </section>

  <section class="products">
    <h2>Selected for {{ room.contact.company }}</h2>

    <div class="product-grid">
      {% for selection in room.selectedProducts %}
        {% set product = products | findProduct(selection.productId) %}

        {% if product %}
          <article class="product-card">
            <img src="{{ product.imageUrl }}" alt="{{ product.name }}">
            <h3>{{ product.name }}</h3>
            <p>{{ selection.reason }}</p>
            <a href="{{ product.productUrl }}">View product</a>
          </article>
        {% endif %}
      {% endfor %}
    </div>
  </section>

  <section class="primary-action">
    <a class="button" href="{{ room.primaryCta.url }}">
      {{ room.primaryCta.label }}
    </a>
  </section>
</main>
```

## Benodigde filter

De template gebruikt conceptueel een `findProduct`-filter. Voeg dit toe aan `eleventy.config.js`.

```js
export default function (eleventyConfig) {
  eleventyConfig.addFilter("findProduct", function (products, productId) {
    return products.find((product) => product.productId === productId);
  });
}
```
