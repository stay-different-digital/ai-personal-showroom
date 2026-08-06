# Technische architectuur

## Overzicht

```text
Klantwebsite of productfeed
        ↓
Merkprofiel en productdataset
        ↓
Beursformulier of vrije prompt
        ↓
AI-analyse
        ↓
Productfiltering
        ↓
AI-rangschikking en content
        ↓
JSON-validatie
        ↓
11ty-build
        ↓
Preview en salescontrole
        ↓
Publicatie
        ↓
E-mail en opvolging
```

## Verantwoordelijkheden

| Onderdeel | Verantwoordelijkheid |
| --- | --- |
| AI | Analyse, selectieadvies en teksten |
| n8n | Processtappen verbinden en status beheren |
| Productbron | Feitelijke productinformatie leveren |
| JSON-schema | Grenzen stellen aan AI-output |
| 11ty | HTML, structuur en consistente vormgeving |
| Sales | Controleren en goedkeuren |
| Hosting | Buyer rooms veilig publiceren |

## Waarom 11ty

11ty past goed bij deze use case omdat:

- De output statisch en snel is
- Eén template veel buyer rooms kan genereren
- Data losstaat van de presentatie
- JSON eenvoudig te valideren is
- Er weinig runtime-complexiteit nodig is
- De pagina goed te hosten is op statische hosting

## Belangrijk technisch principe

AI genereert geen HTML, CSS of JavaScript voor iedere lead.

AI vult alleen vooraf bepaalde velden in.

Voorbeeld:

```json
{
  "slug": "haven-hotels-a8f29c",
  "language": "de",
  "introduction": "Vielen Dank für das angenehme Gespräch.",
  "selectedProductIds": ["ZUV-001", "ZUV-006"],
  "primaryCta": {
    "label": "Gespräch planen",
    "url": "https://example.com/book"
  }
}
```

## Publicatiemodel

### Eerste demo

- Lokale 11ty-build
- Handmatig publiceren
- Geen echte persoonsgegevens

### Pilot

- Unieke URL per lead
- Moeilijk te raden slug
- Eventueel wachtwoord of toegangstoken
- Verwijdering na afgesproken bewaartermijn

## Aanbevolen componenten

- Node.js
- 11ty
- Nunjucks
- JSON Schema of Zod voor validatie
- n8n
- Gemini API of ander goedgekeurd AI-model
- Google Sheets, CSV of PIM-export
- GitHub voor versiebeheer
- Netlify, Cloudflare Pages of vergelijkbare statische hosting
