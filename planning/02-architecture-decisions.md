# Architectuurbeslissingen

## ADR-001: 11ty als presentatielaag

### Besluit

Gebruik 11ty voor het genereren van buyer rooms.

### Reden

- Statische output
- Snelle pagina's
- Vaste template
- Data en presentatie blijven gescheiden
- Eenvoudig te hosten

## ADR-002: AI levert JSON, geen HTML

### Besluit

AI mag alleen data leveren binnen een vast schema.

### Reden

- Minder fouten
- Betere validatie
- Consistente merkuitstraling
- Minder securityrisico
- Eenvoudiger testen

## ADR-003: productdata is leidend

### Besluit

Producteigenschappen komen alleen uit een gecontroleerde productbron.

### Reden

AI mag geen feitelijke productinformatie verzinnen.

## ADR-004: sales keurt publicatie goed

### Besluit

Iedere buyer room blijft in de eerste pilot op `draft` tot sales deze goedkeurt.

### Reden

- Kwaliteitscontrole
- Commerciële controle
- Minder risico op verkeerde verwachtingen

## ADR-005: website-analyse is alleen startpunt

### Besluit

Gebruik de openbare website voor een prototype, maar niet als definitieve commerciële productbron.

### Reden

Een website kan onvolledige, consumentgerichte of verouderde informatie bevatten.
