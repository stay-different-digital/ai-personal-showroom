# Testplan

## Doel

Test zowel technische werking als commerciële bruikbaarheid.

## Testgebieden

### 1. Leadanalyse

Controleer of AI correct herkent:

- Klanttype
- Projecttype
- Stijl
- Productcategorieën
- Belangrijke eisen
- Planning
- Ontbrekende informatie

### 2. Productselectie

Controleer:

- Alleen actieve producten
- Alleen bestaande product-ID's
- Passende categorieën
- Passende toepassingen
- Geen verzonnen kenmerken
- Maximaal zes producten

### 3. Content

Controleer:

- Juiste taal
- Persoonlijke maar zakelijke toon
- Geen ongefundeerde claims
- Geen officiële offertetaal
- Duidelijke call-to-action

### 4. 11ty-build

Controleer:

- Geldige build
- Werkende productlinks
- Werkende afbeeldingen
- Goede mobiele weergave
- Toegankelijke knoppen
- `noindex`
- Juiste slug

### 5. Salescontrole

Meet:

- Tijd om intake in te vullen
- Tijd om preview te controleren
- Aantal tekstcorrecties
- Aantal productwissels
- Reden van afwijzing

## Testcases

| ID | Scenario | Verwacht resultaat |
| --- | --- | --- |
| T01 | Volledige hotellead | Buyer room wordt als concept gemaakt |
| T02 | Geen productinteresse | Workflow vraagt om aanvulling |
| T03 | Confidence onder 50 | Geen automatische build |
| T04 | Onbekend product-ID | Validatie stopt publicatie |
| T05 | Meer dan zes producten | Selectie wordt begrensd |
| T06 | Duits als taal | Duitse content wordt gemaakt |
| T07 | Geen toestemming | Geen klantmail wordt verstuurd |
| T08 | Product zonder afbeelding | Product valt uit de voorselectie |
| T09 | Buildfout | Status blijft `draft` |
| T10 | Verlopen buyer room | Pagina wordt verwijderd of geblokkeerd |

## Acceptatiecriteria

- Minimaal 80 procent van de analyses klopt zonder grote correctie
- Minimaal 70 procent van de productselectie blijft staan
- Geen verzonnen producteigenschappen
- De build slaagt bij alle geldige datasets
- De pagina werkt op mobiel en desktop
- Sales kan de preview afkeuren
