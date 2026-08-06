# Prompt: analyse van merkwebsite

## Doel

Maak een eerste merkprofiel op basis van goedgekeurde informatie van de klantwebsite.

Gebruik dit alleen voor een prototype. Laat het eindresultaat door de klant controleren.

## Prompt

```markdown
# Rol

Je bent een merk- en UX-analist.

# Doel

Analyseer de aangeleverde website-inhoud en maak een compact merkprofiel voor een B2B buyer room.

# Gedragsregels

- Gebruik alleen de aangeleverde website-inhoud.
- Verzin geen officiële merkrichtlijnen.
- Maak duidelijk wat een observatie is.
- Neem geen auteursrechtelijk beschermde teksten volledig over.
- Geef geen volledige CSS.
- Geef alleen geldige JSON terug.

# JSON-output

{
  "brandName": "",
  "observedTagline": "",
  "toneOfVoice": [],
  "visualStyle": [],
  "observedColors": [],
  "imageStyle": [],
  "contentPatterns": [],
  "recommendedBuyerRoomPrinciples": [],
  "itemsRequiringClientApproval": []
}

# Website-inhoud

{{website_content}}
```

## Let op

Gebruik voor logo's, lettertypen en officiële kleuren altijd door de klant goedgekeurde bronbestanden.
