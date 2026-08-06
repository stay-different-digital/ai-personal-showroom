# n8n-workflow: beursgesprek naar buyer room

## Doel

Automatiseer de stappen van intake tot een gecontroleerde buyer-roompreview.

## Trigger

Een nieuwe inzending vanuit een formulier of webhook.

## Input

- Leadgegevens
- Gespreksnotitie
- Gewenste taal
- Productinteresse
- Gewenste vervolgactie

## Workflowstappen

1. Ontvang de lead
2. Controleer verplichte velden
3. Maak een unieke `leadId`
4. Sla de lead op
5. Analyseer de gespreksnotitie
6. Valideer de AI-output
7. Haal actieve producten op
8. Filter op categorie, toepassing en stijl
9. Rangschik de overgebleven producten
10. Selecteer maximaal zes producten
11. Genereer persoonlijke buyer-roomcontent
12. Bouw `buyer-room.json`
13. Valideer het JSON-bestand
14. Schrijf het bestand naar de 11ty-codebase
15. Start een previewbuild
16. Stuur sales een controlelink
17. Wacht op goedkeuring
18. Publiceer de buyer room
19. Maak een conceptmail
20. Verstuur na goedkeuring
21. Werk status en meetpunten bij

## Belangrijke nodes

| Stap | Node | Doel |
| --- | --- | --- |
| 1 | Webhook of Form Trigger | Intake ontvangen |
| 2 | Set | Velden normaliseren |
| 3 | Code | ID en slug maken |
| 4 | Google Sheets of Data Table | Lead opslaan |
| 5 | Gemini | Lead analyseren |
| 6 | Code | JSON controleren |
| 7 | Google Sheets of HTTP Request | Producten ophalen |
| 8 | Code | Harde productfilters toepassen |
| 9 | Gemini | Producten rangschikken |
| 10 | Code | Selectie begrenzen |
| 11 | Gemini | Teksten genereren |
| 12 | Code | Buyer-roomobject maken |
| 13 | Code | Schema valideren |
| 14 | GitHub of bestandsschrijfactie | JSON opslaan |
| 15 | Execute Command of deploy-hook | Preview bouwen |
| 16 | Gmail of Teams | Controlelink sturen |
| 17 | Wait | Goedkeuring afwachten |
| 18 | HTTP Request | Publicatie starten |
| 19 | Gmail | Conceptmail maken |
| 20 | Gmail | Mail versturen |
| 21 | Google Sheets | Status bijwerken |

## Dataverwerking

### Voorfiltering

Filter eerst op harde voorwaarden:

- `active` is `true`
- Categorie komt overeen
- Toepassing past bij projecttype
- Product heeft een geldige afbeelding
- Product heeft een geldige productlink

### AI-rangschikking

Laat AI alleen de gefilterde producten rangschikken.

Geef per product alleen de velden mee die nodig zijn voor selectie.

### Validatie

Controleer:

- Geldige JSON
- Maximaal zes producten
- Bestaande product-ID's
- Geen lege introductie
- Geldige taalcode
- Geldige call-to-action

## Foutafhandeling

| Fout | Actie |
| --- | --- |
| Verplicht veld ontbreekt | Stop en vraag sales om aanvulling |
| AI geeft ongeldige JSON | Probeer één herstelprompt, stop daarna |
| Geen passende producten | Maak geen buyer room en meld dit aan sales |
| Product-ID bestaat niet | Verwijder de selectie en laat opnieuw rangschikken |
| Build mislukt | Houd status op `draft` en stuur technische melding |
| Geen toestemming voor opvolging | Verstuur geen klantmail |

## Testscenario's

- Volledige hotellead
- Korte en onduidelijke notitie
- Geen passend product
- Ongeldige e-mail
- Niet-toegestane taal
- Product zonder afbeelding
- AI selecteert onbekend product-ID
- Sales wijst preview af

## Beheer

- Houd prompts onder versiebeheer
- Log modelnaam en promptversie
- Bewaar alleen noodzakelijke leadgegevens
- Controleer productdata voor iedere beurs
- Meet handmatige correcties
