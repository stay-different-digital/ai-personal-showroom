# 11ty-projectstructuur

## Voorgestelde technische mapstructuur

Deze documentatiemap bevat nog geen werkende 11ty-installatie. Gebruik onderstaande structuur als start voor de codebase.

```text
zuiver-buyer-room/
├── src/
│   ├── _data/
│   │   ├── brand.json
│   │   ├── products.json
│   │   └── rooms.json
│   ├── _includes/
│   │   ├── layouts/
│   │   │   └── buyer-room.njk
│   │   └── components/
│   │       ├── hero.njk
│   │       ├── project-summary.njk
│   │       ├── style-concept.njk
│   │       ├── product-grid.njk
│   │       ├── product-card.njk
│   │       ├── documents.njk
│   │       └── call-to-action.njk
│   ├── assets/
│   │   ├── css/
│   │   │   └── main.css
│   │   ├── js/
│   │   │   └── analytics.js
│   │   └── brands/
│   │       └── zuiver/
│   └── rooms/
│       └── room.njk
├── scripts/
│   ├── validate-data.mjs
│   ├── build-room.mjs
│   └── publish-room.mjs
├── schemas/
│   ├── brand.schema.json
│   ├── product.schema.json
│   └── buyer-room.schema.json
├── eleventy.config.js
├── package.json
└── README.md
```

## Pagina-generatie

Gebruik één template om meerdere buyer rooms te genereren.

Conceptueel voorbeeld:

```njk
---
pagination:
  data: rooms
  size: 1
  alias: room
permalink: "/rooms/{{ room.slug }}/index.html"
layout: layouts/buyer-room.njk
---

{% include "components/hero.njk" %}
{% include "components/project-summary.njk" %}
{% include "components/style-concept.njk" %}
{% include "components/product-grid.njk" %}
{% include "components/call-to-action.njk" %}
```

## Productdata koppelen

De buyer room bevat alleen product-ID's en persoonlijke redenen.

De template zoekt de feitelijke productinformatie op in `products.json`.

Voordeel:

- AI kan geen prijs of materiaal verzinnen
- Productdata blijft centraal beheerd
- Correcties gelden direct voor alle nieuwe builds
- De buyer-roomdata blijft klein

## Componenten

### Hero

- Klantnaam of bedrijfsnaam
- Persoonlijke introductie
- Beursnaam
- Groot merkbeeld

### Project summary

- Projecttype
- Gewenste stijl
- Productinteresse
- Planning

### Product grid

- Afbeelding
- Productnaam
- Feitelijke kenmerken
- Persoonlijke selectiereden
- Productlink

### Call-to-action

- Eén primaire actie
- Optioneel één tweede actie

## Styling

Gebruik een vaste designset met:

- CSS-variabelen voor kleuren
- Vaste typografieschaal
- Herbruikbare spacing
- Mobiele opmaak vanaf het begin
- Duidelijke focusstijlen voor toegankelijkheid

## URL-opbouw

Voorbeeld:

```text
https://buyerrooms.example.com/zuiver/haven-hotels-a8f29c/
```

Gebruik geen e-mailadres of volledige persoonsnaam in de URL.
