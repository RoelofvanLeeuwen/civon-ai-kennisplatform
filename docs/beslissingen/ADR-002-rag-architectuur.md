# ADR-002 — RAG als architectuurpatroon

**Datum:** Juni 2025  
**Status:** Geaccepteerd  
**Besloten door:** Roelof van Leeuwen

---

## Context

Het platform moet interne kennis doorzoekbaar maken en via een chatbot ontsluiten. De kennis zit in bestaande documenten, rapporten en andere bronnen.

## Beslissing

Het systeem is gebaseerd op het **Retrieval Augmented Generation (RAG)** patroon.

```
[Bronnen: documenten, rapporten, SharePoint, etc.]
        ↓
[Verwerking: tekst extractie, chunken, embedden]
        ↓
[Vectordatabase: doorzoekbare kennisbank]
        ↓
[Chatbot: vraag → zoek relevante chunks → genereer antwoord]
        ↓
[Gebruiker krijgt gericht antwoord met bronverwijzing]
```

## Redenen

1. Bewezen patroon voor kennisontsluitingsvraagstukken
2. Kwaliteit van antwoorden hangt af van de bronnen, niet alleen van het model
3. Werkt goed in combinatie met lokale LLM's
4. Bronverwijzingen zijn mogelijk — transparantie over herkomst van antwoord

## Consequenties

- Documentverwerking (chunken en embedden) is een kritische stap in de kwaliteit
- Kwaliteit van ingevoerde documenten bepaalt kwaliteit van antwoorden
- Er is een redactioneel proces nodig voor kennisbeheer (nog uit te werken)
- Cursussen en modules genereren is fase 2 — buiten scope PoC
