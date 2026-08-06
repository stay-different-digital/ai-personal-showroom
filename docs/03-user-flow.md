# Gebruikersflow

## Hoofdflow

| Stap | Gebruiker | Actie | Resultaat |
| --- | --- | --- | --- |
| 1 | Accountmanager | Voert een beursgesprek | Klantbehoefte wordt duidelijk |
| 2 | Accountmanager | Vult formulier in of spreekt notitie in | Leadinformatie wordt opgeslagen |
| 3 | AI | Analyseert de notitie | Gestructureerde klantbriefing |
| 4 | Workflow | Filtert mogelijke producten | Veilige voorselectie |
| 5 | AI | Rangschikt producten | Persoonlijke productselectie |
| 6 | AI | Schrijft buyer-roomcontent | Persoonlijke teksten |
| 7 | 11ty | Bouwt statische pagina | Preview van buyer room |
| 8 | Accountmanager | Controleert selectie en tekst | Goedgekeurde buyer room |
| 9 | Workflow | Publiceert de pagina | Unieke link voor de klant |
| 10 | Klant | Bekijkt en deelt de buyer room | Interesse wordt zichtbaar |
| 11 | Sales | Volgt gericht op | Vervolgafspraak of aanvraag |

## Intake voor sales

De intake moet binnen twee minuten kunnen worden ingevuld.

### Verplichte velden

- Naam accountmanager
- Naam contactpersoon
- Bedrijfsnaam
- E-mailadres
- Taal
- Type klant
- Productinteresse
- Gespreksnotitie
- Gewenste vervolgstap
- Prioriteit

### Extra velden

- Beursnaam
- Projecttype
- Gewenste stijl
- Planning
- Budgetcategorie
- Belangrijke eisen
- Getoonde producten
- Land
- Toestemming voor opvolging

## Goedkeuringsflow

Sales krijgt een preview met:

- Samenvatting van het gesprek
- Geselecteerde producten
- Reden per product
- Ontbrekende informatie
- Persoonlijke introductie
- Conceptmail
- Confidence score

Sales kan:

- Goedkeuren
- Product verwijderen
- Product vervangen
- Tekst aanpassen
- Publicatie stoppen

## Fallbackflow

### Confidence score 80 tot 100

- Maak automatisch een concept
- Vraag alleen om controle

### Confidence score 50 tot 79

- Maak een concept
- Toon ontbrekende informatie duidelijk

### Confidence score onder 50

- Maak nog geen buyer room
- Vraag sales om aanvullende informatie
