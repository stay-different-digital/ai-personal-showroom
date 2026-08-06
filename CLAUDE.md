# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Wat dit is

Concept- en voorbereidingsrepo voor de **Zuiver AI Personal Showroom**: een systeem dat een beursgesprek omzet in een persoonlijke, statische "buyer room" website per lead. Er is nog **geen werkende codebase** — deze repo bevat alleen concept, architectuur, datamodel, prompts en planning in Markdown. Er is dus (nog) geen build/lint/test-commando; die komen zodra `docs/07-eleventy-structure.md` wordt omgezet naar een echt 11ty-project.

Alle documentatie is in het Nederlands geschreven; houd nieuwe documentatie en commit messages in dezelfde taal, tenzij de gebruiker anders aangeeft.

## Kernprincipe (niet-onderhandelbaar, zie `planning/02-architecture-decisions.md`)

AI bepaalt niet hoe de website technisch wordt opgebouwd — AI levert alleen gecontroleerde JSON aan binnen een vast schema, 11ty rendert die JSON altijd naar dezelfde vaste template.

```
Klantwebsite + productdata + beursnotitie/prompt
        ↓ AI-analyse
Gecontroleerde JSON  (nooit HTML/CSS/JS van AI)
        ↓ 11ty-template
Buyer room (statisch)
        ↓ Sales-goedkeuring (verplicht, status blijft `draft` tot dan)
Publicatie + opvolging
```

Andere vaste beslissingen om bij te houden:
- Producteigenschappen komen **altijd** uit de gecontroleerde productbron, nooit uit AI-output (AI mag niet verzinnen).
- Website-analyse van een klant is alleen een prototype-startpunt, geen definitieve productbron.
- Elke buyer room heeft een `expiresAt`, een niet-raadbare slug (geen e-mail/volledige naam erin) en `noindex`.

## Datamodel (`docs/06-data-model.md`)

Vijf gescheiden entiteiten, bewust niet samengevoegd zodat controle/hergebruik makkelijk blijft: **Brand**, **Product**, **Lead**, **AI-analyse**, **Buyer room**. De buyer room verwijst alleen naar `productId`'s + een reden per product; de template zoekt zelf de feitelijke productdata op in `products.json`. Belangrijkste validatieregels (zie ook `docs/09-security-privacy.md`):
- `selectedProducts` max. 6, elk `productId` moet bestaan in de productdataset.
- `confidenceScore` 0–100; onder 50 wordt er geen buyer room gebouwd (zie fallbackflow in `docs/03-user-flow.md`).
- Status `published` mag alleen na sales-goedkeuring.

## Mappen

| Map | Inhoud |
| --- | --- |
| `docs/` | Concept, architectuur, datamodel, 11ty-structuur, n8n-workflow, security, testplan, roadmap — genummerd, lees in volgorde |
| `prompts/` | De vijf AI-prompts die de pipeline vormen: leadanalyse → productrangschikking → contentgeneratie → (optioneel) websitemerkanalyse → buyer-room-JSON-samenvoeging |
| `examples/` | Voorbeeld-JSON/output per stap uit de pipeline, corresponderend met de prompts |
| `planning/` | Backlog, architectuurbeslissingen (ADR's), open vragen, weekplan |

Aanbevolen leesvolgorde bij oriëntatie: `README.md` → `docs/01` t/m `docs/08` → `prompts/01-lead-analysis-prompt.md` → `examples/04-buyer-room-json-example.md`.

## Toekomstige 11ty-codebase

Wanneer dit van concept naar code gaat, is de voorgestelde structuur al vastgelegd in `docs/07-eleventy-structure.md` (`src/_data`, `src/_includes/components`, `scripts/validate-data.mjs`, `schemas/*.schema.json`, één `rooms/room.njk` met paginatie over `rooms.json`). Volg die structuur i.p.v. een nieuwe te verzinnen — hij is al afgestemd op het datamodel hierboven (data en presentatie strikt gescheiden, AI vult alleen velden in een vast schema).

## MVP-scope (`docs/04-mvp-scope.md`)

Expliciet **niet** in scope, dus geen functionaliteit hiervoor toevoegen tenzij de gebruiker het vraagt: live voorraad, persoonlijke B2B-prijzen, automatische offertes, checkout, CRM-koppeling, volledige productcatalogus, exact interieurontwerp, volledig automatische verzending.
