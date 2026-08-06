# Zuiver AI Personal Showroom

## Doel

Dit project beschrijft een standalone AI-oplossing voor Zuiver.

De oplossing zet een beursgesprek om in een persoonlijke digitale buyer room. De buyer room bevat relevante Zuiver-producten, inspiratie, een samenvatting van de klantvraag en een duidelijke vervolgstap.

De eerste versie gebruikt:

- 11ty als vaste presentatielaag
- JSON als gegevensformaat
- Gemini of een ander AI-model voor analyse en teksten
- n8n voor automatisering
- Google Sheets of een CSV-bestand als tijdelijke productbron
- Een vaste goedkeuringsstap voor sales

## Kernprincipe

AI bepaalt niet hoe de website technisch wordt opgebouwd.

AI levert alleen gecontroleerde gegevens aan. 11ty zet deze gegevens om naar een vaste en consistente buyer room.

```text
Klantwebsite en productdata
        +
Beursnotitie of prompt
        ↓
AI-analyse
        ↓
Gecontroleerde JSON
        ↓
11ty-template
        ↓
Persoonlijke buyer room
        ↓
Controle door sales
        ↓
Publicatie en opvolging
```

## Projectstatus

- Status: concept en technische voorbereiding
- Eerste doelgroep: Zuiver Project Sales en dealer sales
- Eerste use case: opvolging na een beursgesprek
- Eerste demo: Duitse hotelketen met drie nieuwe hotellobby's

## Mappen

| Map | Inhoud |
| --- | --- |
| `docs` | Concept, architectuur, workflow, MVP en testplan |
| `prompts` | Herbruikbare AI-prompts |
| `examples` | Voorbeelddata, JSON en template-opbouw |
| `planning` | Backlog, roadmap en beslissingen |

## Aanbevolen leesvolgorde

1. `docs/01-concept.md`
2. `docs/02-demo-scenario.md`
3. `docs/03-user-flow.md`
4. `docs/04-mvp-scope.md`
5. `docs/05-technical-architecture.md`
6. `docs/06-data-model.md`
7. `docs/07-eleventy-structure.md`
8. `docs/08-n8n-workflow.md`
9. `prompts/01-lead-analysis-prompt.md`
10. `examples/04-buyer-room-json-example.md`

## Eerste technische proef

Bouw eerst één buyer room zonder volledige automatisering.

Gebruik hiervoor:

- Eén merkprofiel
- Twintig tot dertig producten
- Eén fictieve beurslead
- Eén `buyer-room.json`
- Eén Nunjucks-template
- Eén lokale 11ty-build

## Definition of Done voor de eerste demo

- De buyer room werkt op desktop en mobiel
- De pagina gebruikt echte productafbeeldingen
- De pagina toont maximaal zes producten
- De introductie is persoonlijk
- Producteigenschappen komen alleen uit de brondata
- De pagina bevat één hoofdactie
- Sales kan de inhoud controleren voor publicatie
- De demo gebruikt geen vertrouwelijke klantgegevens

## Belangrijke beperking

De eerste versie is een visueel verkoopvoorstel. Het is geen offerte, configurator of technisch interieurontwerp.
