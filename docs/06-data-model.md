# Datamodel

## Doel

Houd merkdata, productdata, leaddata en AI-output gescheiden.

Dit maakt controle, onderhoud en hergebruik eenvoudiger.

## Brand

```json
{
  "brandId": "zuiver",
  "name": "Zuiver",
  "tagline": "",
  "logo": "/assets/brands/zuiver/logo.svg",
  "primaryColor": "#000000",
  "secondaryColor": "#F3EFE8",
  "toneOfVoice": ["modern", "inspirerend", "toegankelijk"],
  "visualStyle": ["veel witruimte", "grote beelden", "rustige typografie"]
}
```

## Product

```json
{
  "productId": "ZUV-001",
  "articleNumber": "1000001",
  "name": "Voorbeeld fauteuil",
  "category": "fauteuil",
  "subcategory": "lounge chair",
  "styleTags": ["warm", "modern", "afgerond"],
  "useCaseTags": ["hotel", "lobby", "lounge"],
  "color": "groen",
  "materials": ["stof", "metaal"],
  "dimensions": {
    "widthCm": 80,
    "heightCm": 75,
    "depthCm": 82
  },
  "sustainabilityTags": [],
  "shortDescription": "Feitelijke productomschrijving uit de bron.",
  "imageUrl": "https://example.com/image.jpg",
  "productUrl": "https://example.com/product",
  "documentUrls": [],
  "active": true
}
```

## Lead

```json
{
  "leadId": "LEAD-2026-0001",
  "createdAt": "2026-08-06T14:00:00+02:00",
  "eventName": "Voorbeeldbeurs",
  "accountManager": "Voorbeeldnaam",
  "contact": {
    "firstName": "Anna",
    "lastName": "Müller",
    "company": "Haven Hotels Group",
    "email": "anna@example.com",
    "language": "de"
  },
  "customerType": "hotelketen",
  "notes": "Vrije beursnotitie",
  "permissionFollowUp": true,
  "status": "new"
}
```

## AI-analyse

```json
{
  "leadId": "LEAD-2026-0001",
  "customerType": "hotelketen",
  "projectType": "hotellobby",
  "projectCount": 3,
  "summary": "",
  "styleTags": ["warm", "modern", "toegankelijk"],
  "productCategories": ["fauteuil", "bijzettafel", "verlichting"],
  "useCaseTags": ["hotel", "lobby"],
  "importantRequirements": ["duurzaamheid"],
  "timing": "start over zes maanden",
  "recommendedFollowUp": "online gesprek",
  "missingInformation": ["budget", "afmetingen"],
  "confidenceScore": 86
}
```

## Buyer room

```json
{
  "roomId": "ROOM-2026-0001",
  "leadId": "LEAD-2026-0001",
  "slug": "haven-hotels-a8f29c",
  "language": "de",
  "status": "draft",
  "introduction": "",
  "projectSummary": "",
  "styleConcept": {
    "title": "Warm Welcome",
    "description": "",
    "colorLabels": ["warm beige", "donker hout", "zacht groen"]
  },
  "selectedProducts": [
    {
      "productId": "ZUV-001",
      "reason": ""
    }
  ],
  "combinations": [],
  "documents": [],
  "primaryCta": {
    "label": "Gespräch planen",
    "url": "https://example.com/book"
  },
  "expiresAt": "2026-11-06T23:59:59+01:00"
}
```

## Validatieregels

- `selectedProducts` bevat maximaal zes producten
- Ieder `productId` moet bestaan in de productdataset
- Producteigenschappen komen niet uit de AI-output
- `primaryCta.url` moet een toegestane URL zijn
- `slug` bevat geen e-mailadres of volledige persoonsnaam
- `confidenceScore` ligt tussen 0 en 100
- Een buyer room met status `published` moet goedgekeurd zijn
