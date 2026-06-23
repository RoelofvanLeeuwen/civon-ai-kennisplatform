# Civon AI Kennisplatform — Startdocument
**Versie:** 0.2 — Aangescherpt op basis van mail Klaas Reitsma  
**Datum:** Juni 2025  
**Auteur:** Roelof van Leeuwen  
**Status:** Concept — ter voorbereiding op schooljaar 2025–2026

---

## 1. Aanleiding en context

De **AIC4NL Learning Community** is een samenwerking tussen een community van bedrijven uit de maakindustrie, HAN, Graafschap College en Civon in Ulft. Deelnemende organisaties doen ieder op eigen vlak kennis op rondom AI-toepassingen.

De centrale uitdaging: kennis zit versnipperd bij mensen en in systemen — e-mails, gedeelde documenten, SharePoint, rapporten, en in de hoofden van medewerkers. Die kennis wordt onvoldoende gedeeld en benut.

Roelof van Leeuwen treedt op als onderzoeker en pioneer voor dit project (1 dag per week gedurende het schooljaar 2025–2026). Hij ontwikkelt het PoC en deelt de opgedane kennis en methodiek tijdens community-sessies en in lesmateriaal voor MBO-onderwijs en MKB.

---

## 2. Use cases

### 2.1 Primaire use case — VB Airsuspension

> *"Hoe kunnen gebruikers en collega's snel, correct en controleerbaar antwoord krijgen op technische vragen, met bronnen uit bestaande systemen?"*

VB Airsuspension brengt deze use case in als centraal leervraagstuk voor de community. De vraag speelt breed in het bedrijfsleven en is representatief voor de bredere uitdaging.

### 2.2 Secundaire use case — Civon

Civon wil een vergelijkbaar systeem opzetten voor het beheren en ontsluiten van kennis uit de verschillende lopende projecten binnen de organisatie. Binnen Civon zijn meerdere groepen actief met eigen kennisdomeinen die onderling beter gedeeld moeten worden.

Het PoC wordt als eerste ontwikkeld voor Civon. Als dit werkt, is het de basis voor uitrol naar de bredere community en uiteindelijk de VB Airsuspension-casus.

---

## 3. Doelstelling

Bouwen van een **Proof of Concept (PoC)** van een AI-gestuurd kennisplatform waarmee medewerkers interne kennis kunnen ontsluiten via een chatbot-interface.

Het PoC moet aantonen:

> *"Als een medewerker een vraag stelt over een onderwerp waarover de organisatie interne kennis heeft, geeft het systeem een relevant, correct en controleerbaar antwoord op basis van bronnen die de organisatie zelf heeft ingebracht — inclusief verwijzing naar die bronnen."*

### Dubbele output

| Output | Beschrijving |
|---|---|
| Werkend PoC | Functionerend systeem bij Civon als proof of concept |
| Lesmateriaal | Vastgelegd als leermateriaal bruikbaar in MBO-onderwijs en MKB, ontstaan vanuit Roelofs professionele visie op AI-gedreven ontwikkeling |

---

## 4. Kernprincipes en randvoorwaarden

### 4.1 Lokale infrastructuur — harde eis

Het systeem draait volledig op eigen infrastructuur. Er wordt geen gebruik gemaakt van externe AI-diensten zoals OpenAI, Anthropic of Google.

Redenen:
- **Gegevensbescherming** — bedrijfsgevoelige informatie van deelnemers mag niet buiten de eigen omgeving komen
- **Onafhankelijkheid** — geen afhankelijkheid van commerciële partijen en geopolitieke ontwikkelingen

Technische implicaties:
- Lokaal draaiend LLM (bijv. via Ollama met Llama 3.1, Mistral of Phi-4)
- Lokale vectordatabase (bijv. Chroma, Qdrant of Weaviate)
- Lokale embeddingmodellen (geen externe API-calls)
- Hosting op eigen server of contractueel geborgde EU-infrastructuur

### 4.2 Architectuurpatroon: RAG

Het systeem is gebaseerd op het **Retrieval Augmented Generation (RAG)** patroon:

```
[Bronnen: documenten, rapporten, SharePoint, etc.]
        ↓
[Verwerking: tekst extractie, chunken, embedden]
        ↓
[Vectordatabase: doorzoekbare kennisbank]
        ↓
[Chatbot: vraag → zoek relevante chunks → genereer antwoord + bronverwijzing]
        ↓
[Gebruiker krijgt correct en controleerbaar antwoord]
```

### 4.3 Drie typen kennisbronnen

Een kernuitdaging van dit project is het omgaan met drie fundamenteel verschillende typen kennisbronnen:

| Type | Beschrijving | Voorbeelden | Complexiteit |
|---|---|---|---|
| Gestructureerd | Georganiseerde data met vaste structuur | Databases, spreadsheets, ERP-exports | Laag |
| Ongestructureerd | Vrije tekst en documenten | Rapporten, e-mails, Word-bestanden, SharePoint | Middel |
| Ongedocumenteerd | Kennis in hoofden van mensen | Ervaringen, werkwijzen, vakmanschap | Hoog |

Het omgaan met ongedocumenteerde kennis is de moeilijkste uitdaging en onderscheidt dit project van een standaard RAG-implementatie. Hoe tacit knowledge ontsloten en vastgelegd kan worden is een expliciet leervraagstuk binnen dit project.

### 4.4 Fasering

| Fase | Inhoud | Scope |
|---|---|---|
| PoC | Kennisopslag + chatbot voor Civon intern | In scope |
| Fase 2 | Uitrol naar VB Airsuspension use case | Buiten scope PoC |
| Fase 3 | Genereren van cursussen, FAQ's, modules | Buiten scope PoC |
| Fase 4 | Uitrol naar bredere AIC4NL community | Buiten scope PoC |

---

## 5. Gebruikers en gebruik

### Primaire gebruiker (PoC)
Medewerkers van Civon die via een chatbot vragen kunnen stellen over intern beschikbare kennis uit lopende en afgeronde projecten.

### Kennisleveranciers
Medewerkers of projectgroepen binnen Civon die documenten, rapporten of andere bronnen aanleveren.

> **Nog te verhelderen:** Hoe worden documenten aangeleverd? Handmatig uploaden, of automatisch ophalen uit bestaande systemen?

---

## 6. Openstaande vragen

1. Welke projectgroepen zijn er binnen Civon en wat zijn hun kennisdomeinen?
2. Welke informatiesystemen zijn al in gebruik binnen Civon?
3. Wat voor type documenten hebben de groepen — formele rapporten of ook informele notities?
4. Wie bewaakt de kwaliteit van ingebrachte kennis?
5. Wat is de beschikbare hardware/infrastructuur voor het draaien van een lokale LLM?
6. Hoe wordt ongedocumenteerde kennis (in hoofden van mensen) ontsloten en vastgelegd?
7. Wat zijn acceptabele antwoordtijden voor de gebruikers?
8. Wat zijn de concrete technische vragen die VB Airsuspension nu niet snel genoeg beantwoord krijgt?

---

## 7. Veldonderzoek — eerste opzet

### 7.1 Onderzoeksvragen

**Over de organisatie en kennisstructuur**
- Hoe is Civon intern georganiseerd? Welke projectgroepen zijn er?
- Welke kennis heeft elke groep en in welke vorm bestaat die kennis?
- Welke kennis wordt nu het minst gedeeld maar zou het meest waardevol zijn?
- Hoe wordt nu omgegaan met kennis die alleen in hoofden zit?

**Over informatiesystemen**
- Welke systemen gebruikt Civon al voor documentbeheer en kennisdeling?
- Zijn er al pogingen gedaan om kennis centraal te ontsluiten?

**Over gebruikersverwachtingen**
- Wat voor vragen zou een medewerker willen stellen aan een kennischatbot?
- Wat maakt een antwoord bruikbaar — en wat maakt het controleerbaar?
- Welke drempel is er voor adoptie van een nieuw systeem?

**Over VB Airsuspension (voor latere fase)**
- Welke technische vragen komen het meest voor?
- In welke systemen zitten de antwoorden nu?
- Wat maakt een antwoord "controleerbaar" in hun context?

**Over technische randvoorwaarden**
- Welke hardware is beschikbaar of kan beschikbaar worden gesteld?
- Wie beheert de infrastructuur?

### 7.2 Aanpak

| Activiteit | Met wie | Doel |
|---|---|---|
| Verkennend gesprek | Klaas Reitsma | Organisatiestructuur Civon en prioriteiten |
| Verkennend gesprek | Niels Schooneveldt | Technische infrastructuur en randvoorwaarden |
| Verkennend gesprek | Martin Stor | Draagvlak en verwachtingen vanuit de community |
| Korte enquête of workshop | 3–5 medewerkers Civon | Gebruikersverwachtingen en kennisvragen |
| Documentinventarisatie | Civon intern | Welke bronnen zijn er en in welk formaat |

### 7.3 Op te leveren na veldonderzoek

- Overzicht van projectgroepen en kennisdomeinen binnen Civon
- Lijst van beschikbare bronnen en formaten
- Beschrijving van technische randvoorwaarden
- Top 3 meest waardevolle vragen die de chatbot moet kunnen beantwoorden
- Eerste voorstel voor technische stack
- Aanpak voor ontsluiting van ongedocumenteerde kennis

---

## 8. Rol en werkwijze Roelof

Roelof treedt op als **onderzoeker, productdefinieerder en ontwikkelleider**. De ontwikkeling van het PoC gebeurt met Claude als AI-assistent gedurende het schooljaar (1 dag per week).

Werkwijze:
- Roelof bepaalt richting en neemt alle beslissingen
- Claude stelt voor en motiveert, Roelof keurt goed
- Iteratief werken: kleine stappen, valideren, volgende stap
- Doel is een PoC — geen commercieel product
- Kennis en methodiek worden gedeeld tijdens AIC4NL community-sessies
- Uitkomsten worden vastgelegd als lesmateriaal voor MBO en MKB

Persoonlijke leerdoelen van Roelof:
1. Hoe ontwikkelen lokale LLM's zich en hoe kunnen ze softwareontwikkeling beïnvloeden?
2. Hoe train, voed en implementeer je een lokale LLM in een softwareoplossing?

---

## 9. Volgende stappen

| Actie | Wanneer | Door wie |
|---|---|---|
| Gesprekken inplannen met Klaas, Niels en Martin | Voor zomervakantie of week 1 nieuw schooljaar | Roelof |
| Documentinventarisatie Civon opzetten | Eerste weken nieuw schooljaar | Roelof + Civon |
| Technische stack verkennen (Ollama, vectordb) | Zomervakantie of week 1–2 | Roelof + Claude |
| PoC-scope definitief vaststellen | Na veldonderzoek | Roelof |
| Start bouw eerste prototype | Na scope-vaststelling | Roelof + Claude |

---

*Dit document is een levend document. Na elk gesprek of beslissing wordt het bijgewerkt.*
