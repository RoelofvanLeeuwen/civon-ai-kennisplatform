# Civon AI Kennisplatform — Startdocument
**Versie:** 0.1 — Eerste opzet na verkennend gesprek  
**Datum:** Juni 2025  
**Auteur:** Roelof van Leeuwen  
**Status:** Concept — ter voorbereiding op schooljaar 2025–2026

---

## 1. Aanleiding en context

Civon is onderdeel van een bredere samenwerking tussen een AI-community van bedrijven, HAN, Graafschap College en Civon in Ulft. Deelnemende organisaties zijn voornamelijk actief in de maakindustrie en doen ieder op eigen vlak kennis op rondom AI-toepassingen.

De centrale uitdaging: kennis zit versnipperd bij mensen en in systemen — e-mails, gedeelde documenten, SharePoint, rapporten, en hoofden van medewerkers. Die kennis wordt onvoldoende gedeeld en benut.

Het project start als een **intern Civon-initiatief**. Als het binnen Civon werkt, is het de bedoeling dit uit te breiden naar de bredere community.

---

## 2. Doelstelling

Bouwen van een **Proof of Concept (PoC)** van een AI-gestuurd kennisplatform waarmee medewerkers van Civon interne kennis kunnen ontsluiten via een chatbot-interface.

Het PoC moet aantonen:

> *"Als een medewerker een vraag stelt over een onderwerp waarover Civon interne kennis heeft, geeft het systeem een relevant en onderbouwd antwoord op basis van documenten en informatie die de organisatie zelf heeft ingebracht."*

Uitbreiding naar cursusmodules, FAQ's en lesmateriaal is **fase 2** — buiten scope van het PoC.

---

## 3. Kernprincipes en randvoorwaarden

### 3.1 Lokale infrastructuur — harde eis

Het systeem draait volledig op eigen infrastructuur. Er wordt geen gebruik gemaakt van externe AI-diensten zoals OpenAI, Anthropic of Google.

Redenen:
- **Onafhankelijkheid** — geen afhankelijkheid van commerciële partijen en geopolitieke ontwikkelingen
- **Gegevensbescherming** — bedrijfsgevoelige informatie van deelnemers mag niet buiten de eigen omgeving komen

Technische implicaties:
- Lokaal draaiend LLM (bijv. via Ollama met Llama 3.1, Mistral of Phi-4)
- Lokale vectordatabase (bijv. Chroma, Qdrant of Weaviate)
- Lokale embeddingmodellen (geen externe API-calls)
- Hosting op eigen server of contractueel geborgde EU-infrastructuur

### 3.2 Architectuurpatroon: RAG

Het systeem is gebaseerd op het **Retrieval Augmented Generation (RAG)** patroon:

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

### 3.3 Fasering

| Fase | Inhoud | Scope |
|---|---|---|
| PoC | Kennisopslag + chatbot voor Civon intern | In scope |
| Fase 2 | Genereren van cursussen, FAQ's, modules | Buiten scope PoC |
| Fase 3 | Uitrol naar bredere AI-community | Buiten scope PoC |

---

## 4. Gebruikers en gebruik

### Primaire gebruiker (PoC)
Medewerkers van Civon die via een chatbot vragen kunnen stellen over intern beschikbare kennis.

### Kennisleveranciers
Medewerkers of groepen binnen Civon die documenten, rapporten of andere bronnen aanleveren om in het systeem op te nemen.

> **Nog te verhelderen:** Hoe worden documenten aangeleverd? Handmatig uploaden, of automatisch ophalen uit bestaande systemen zoals SharePoint?

---

## 5. Openstaande vragen

De volgende vragen zijn nog niet beantwoord en vormen de basis voor het veldonderzoek (zie hoofdstuk 6):

1. Welke groepen bestaan er binnen Civon en wat zijn hun kennisdomeinen?
2. Welke informatiesystemen zijn al in gebruik (SharePoint, gedeelde schijven, etc.)?
3. Wat voor type documenten hebben de groepen — formele rapporten of ook informele notities?
4. Wie bewaakt de kwaliteit van ingebrachte kennis? Is er een redactioneel proces nodig?
5. Wat is de beschikbare hardware/infrastructuur voor het draaien van een lokale LLM?
6. Wat zijn de verwachtingen van medewerkers ten aanzien van de chatbot?
7. Wat zijn acceptabele antwoordtijden voor de gebruikers?
8. Is er al draagvlak bij leidinggevenden binnen Civon?

---

## 6. Veldonderzoek — eerste opzet

Om bovenstaande vragen te beantwoorden wordt een korte verkenning uitgevoerd voor de start van het nieuwe schooljaar. Het doel is niet een uitputtend onderzoek, maar voldoende basis om gerichte keuzes te maken voor de architectuur en aanpak van het PoC.

### 6.1 Onderzoeksvragen

**Over de organisatie en kennisstructuur**
- Hoe is Civon intern georganiseerd? Welke teams of groepen zijn er?
- Welke kennis heeft elke groep en in welke vorm bestaat die kennis?
- Welke kennis wordt nu het minst gedeeld maar zou het meest waardevol zijn?

**Over informatiesystemen**
- Welke systemen gebruikt Civon al voor documentbeheer en kennisdeling?
- Zijn er al pogingen gedaan om kennis centraal te ontsluiten? Wat werkte wel/niet?

**Over gebruikersverwachtingen**
- Wat voor vragen zou een medewerker willen stellen aan een kennischatbot?
- Wat maakt een antwoord bruikbaar voor hen?
- Welke drempel is er voor adoptie van een nieuw systeem?

**Over technische randvoorwaarden**
- Welke hardware is beschikbaar of kan beschikbaar worden gesteld?
- Wie beheert de infrastructuur?
- Zijn er al ervaringen met lokale AI-tools binnen Civon?

### 6.2 Aanpak

| Activiteit | Met wie | Doel |
|---|---|---|
| Verkennend gesprek | Klaas Reitsma | Organisatiestructuur en prioriteiten |
| Verkennend gesprek | Niels Schooneveldt | Technische infrastructuur en randvoorwaarden |
| Verkennend gesprek | Martin Stor | Draagvlak en verwachtingen vanuit de community |
| Korte enquête of workshop | 3–5 medewerkers Civon | Gebruikersverwachtingen en kennisvragen |
| Documentinventarisatie | Civon intern | Welke bronnen zijn er en in welk formaat |

### 6.3 Op te leveren na veldonderzoek

- Overzicht van kennisgroepen binnen Civon
- Lijst van beschikbare bronnen en formaten
- Beschrijving van technische randvoorwaarden
- Top 3 meest gestelde of waardevolle vragen die de chatbot moet kunnen beantwoorden
- Eerste voorstel voor technische stack (LLM-model, vectordatabase, hostingoplossing)

---

## 7. Rol en werkwijze Roelof

Roelof treedt op als **onderzoeker, productdefinieerder en ontwikkelleider**. De ontwikkeling van het PoC gebeurt met Claude als AI-assistent gedurende het schooljaar (1 dag per week).

Werkwijze:
- Roelof bepaalt richting en neemt alle beslissingen
- Claude stelt voor en motiveert, Roelof keurt goed
- Iteratief werken: kleine stappen, valideren, volgende stap
- Doel is een PoC — geen commercieel product

Persoonlijke leerdoelen van Roelof binnen dit project:
1. Hoe ontwikkelen lokale LLM's zich en hoe kunnen ze softwareontwikkeling beïnvloeden?
2. Hoe train, voed en implementeer je een lokale LLM in een softwareoplossing?

---

## 8. Volgende stappen

| Actie | Wanneer | Door wie |
|---|---|---|
| Gesprekken inplannen met Klaas, Niels en Martin | Voor zomervakantie of week 1 nieuw schooljaar | Roelof |
| Documentinventarisatie Civon opzetten | Eerste weken nieuw schooljaar | Roelof + Civon |
| Technische stack verkennen (Ollama, vectordb) | Zomervakantie of week 1–2 | Roelof + Claude |
| PoC-scope definitief vaststellen | Na veldonderzoek | Roelof |
| Start bouw eerste prototype | Na scope-vaststelling | Roelof + Claude |

---

*Dit document is een levend document. Na elk gesprek of beslissing wordt het bijgewerkt.*
