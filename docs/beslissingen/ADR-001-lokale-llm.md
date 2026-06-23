# ADR-001 — Lokale LLM als harde eis

**Datum:** Juni 2025  
**Status:** Geaccepteerd  
**Besloten door:** Roelof van Leeuwen

---

## Context

Het platform verwerkt bedrijfsgevoelige informatie van deelnemende organisaties uit de maakindustrie. Daarnaast is er een bewuste keuze om niet afhankelijk te zijn van commerciële AI-aanbieders.

## Beslissing

Het systeem draait volledig op lokale infrastructuur. Er worden geen externe AI-diensten gebruikt (OpenAI, Anthropic, Google, etc.). Dit geldt voor zowel het taalmodel als de embeddingmodellen.

## Redenen

1. **Gegevensbescherming** — bedrijfsgevoelige informatie mag niet buiten de eigen omgeving komen
2. **Onafhankelijkheid** — geen afhankelijkheid van commerciële partijen en geopolitieke ontwikkelingen

## Consequenties

- Lokaal LLM via Ollama (kandidaten: Llama 3.1, Mistral, Phi-4)
- Lokale vectordatabase (kandidaten: Chroma, Qdrant, Weaviate)
- Lokale embeddingmodellen (geen externe API-calls)
- Hosting op eigen server of contractueel geborgde EU-infrastructuur
- Kwaliteit van het model is lager dan cloud-modellen — voor RAG op interne documenten acceptabel
- Onderhoud van de stack is eigen verantwoordelijkheid
