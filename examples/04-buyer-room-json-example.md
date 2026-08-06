# Voorbeeld: `buyer-room.json`

```json
{
  "roomId": "ROOM-2026-0001",
  "leadId": "LEAD-2026-0001",
  "slug": "haven-hotels-a8f29c",
  "language": "de",
  "status": "draft",
  "contact": {
    "firstName": "Anna",
    "company": "Haven Hotels Group"
  },
  "introduction": "Vielen Dank für das angenehme Gespräch auf der Messe. Auf Grundlage Ihrer Pläne haben wir eine erste Auswahl für Ihre neuen Hotellobbys zusammengestellt.",
  "project": {
    "title": "Drei neue Hotellobbys",
    "summary": "Die Auswahl richtet sich auf eine warme, moderne und einladende Atmosphäre. Im Mittelpunkt stehen Sitzmöbel, Beistelltische und Beleuchtung.",
    "styleTags": ["warm", "modern", "einladend"]
  },
  "styleConcept": {
    "title": "Warm Welcome",
    "description": "Weiche Formen, warme Materialien und ruhige Farben schaffen eine zugängliche Lobby.",
    "colorLabels": ["warmes Beige", "dunkles Holz", "sanftes Grün"]
  },
  "selectedProducts": [
    {
      "productId": "ZUV-001",
      "reason": "Die weiche Form unterstützt eine einladende Sitzgruppe in der Lobby."
    },
    {
      "productId": "ZUV-002",
      "reason": "Der kompakte Tisch passt zu kleinen Sitzbereichen und unterstützt die warme Materialauswahl."
    }
  ],
  "combinations": [
    {
      "name": "Warm Welcome",
      "description": "Eine ruhige Sitzgruppe für Empfang und kurze Gespräche.",
      "productIds": ["ZUV-001", "ZUV-002"]
    }
  ],
  "documents": [],
  "primaryCta": {
    "label": "Gespräch mit Project Sales planen",
    "url": "https://example.com/book"
  },
  "expiresAt": "2026-11-06T23:59:59+01:00"
}
```
