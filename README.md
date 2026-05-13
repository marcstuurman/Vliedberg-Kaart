# Vliedberg – Interactieve Woningkaart

Interactieve kaart van alle woningen in de wijk **Vliedberg** (Vlijmen, gemeente Heusden), verrijkt met data uit drie bronnen: DEGO, VIVET en de PDOK BAG-geocoder.

🗺️ **[Bekijk de kaart](https://marcstuurman.github.io/vliedberg-kaart)**

---

## Inhoud

| Bestand | Beschrijving |
|---|---|
| `index.html` | Standalone interactieve kaart (Leaflet + OpenStreetMap) |

---

## Databronnen

| Bron | Inhoud | Peildatum |
|---|---|---|
| **DEGO** (eigen dataset) | Woningtype, oppervlakte, energieklasse, eigendomssituatie (pc6), WOZ-waarde | 2024 |
| **VIVET** – PBL/CBS ([dataportaal.pbl.nl](https://dataportaal.pbl.nl/VIVET)) | Energielabel (RVO EP-online), verwarmingsinstallatie, kookmethode, lokale praktijkfactor | 2025 |
| **PDOK Locatieserver** – Kadaster ([api.pdok.nl](https://api.pdok.nl)) | Exacte BAG-coördinaten per adres (live geocoding bij openen) | Actueel |

### Dekking
- **648 woningen** in scope (doelgebied Vliedberg)
- **623 woningen** gekoppeld DEGO × VIVET (94,3%)
- **25 woningen** Schoolmeesterstraat (postcodes 5251WP / 5251WR) via BasisDataset hersteld
- **Niet opgenomen:** ~39 adressen zonder VIVET-match (Jacob van Lennepstraat complex, Nassau Dwarsstraat deels)

---

## Functionaliteit

- **4 kleurmodi:** woningtype · eigendom · energielabel · verwarmingsinstallatie
- **Filterchips:** combineer filters op type, eigendom, label en verwarming
- **Popup per woning:** adres, woningtype, eigendom, energielabel, verwarming, koken, oppervlak, bouwjaar, WOZ-waarde, lokale praktijkfactor
- **Live statistieken:** zichtbaar aantal woningen, koop/huur/WP/geen-label teller past mee aan bij filters
- **BAG-geocoding:** exacte coördinaten worden eenmalig opgehaald via PDOK (~20–40 sec laadtijd)

---

## Techniek

De kaart is een **volledig standalone HTML-bestand** — geen server, geen database, geen build-stap nodig.

```
Leaflet 1.9.4          → kaartweergave
CartoDB Dark Matter    → achtergrondkaart (OpenStreetMap)
PDOK Locatieserver     → BAG-geocoding (live, geen API-sleutel nodig)
DM Sans + Playfair     → typografie (Google Fonts)
```

De woningdata (~110 KB JSON) is ingebakken in het HTML-bestand. Bij openen worden via de PDOK API de exacte coördinaten opgehaald in batches van 25 parallelle verzoeken.

---

## Gebruik

Open `index.html` in een browser met internetverbinding. Geen installatie nodig.

> **Let op:** de PDOK API is alleen bereikbaar met een actieve internetverbinding. De kaart werkt niet offline.

---

## Scope & methodologie

Het doelgebied omvat **26 straten** verdeeld in twee zones:

| Zone | Straten | Woningen (WV) |
|---|---|---|
| **Kern** (~550 scope) | 22 straten (Brederostraat, Vondelstraat, Jacob van Lennepstraat, e.a.) | ~538 |
| **Rand** (later toegevoegd) | Antoniestaringlaan, Jacques Perklaan, Zuiderpark, Heisteeg, Alberdingk Thijmstraat | ~155 |

Eigendomssituatie is op **individueel woningniveau** via VIVET (niet het pc6-gemiddelde uit DEGO).
Koop/huur-percentages in het Excel-rapport zijn pc6-gemiddelden en kunnen afwijken.

---

## Gerelateerde bestanden

Het bijbehorende **Excel-analyserapport** (`Vliedberg_Scope_Archtypen_Rapport.xlsx`) bevat 6 tabbladen:

1. **Scope Analyse** – alle straten met WV vs. DEGO tellingen
2. **Archtypen Overzicht** – 7 woningarchtypen met kenmerken
3. **Scope Verantwoording** – onderbouwing ~550 kern vs. 688 totaal
4. **VIVET Warmte Analyse** – energielabel, installaties, praktijkfactor per archtype
5. **Gekoppelde Dataset** – alle 688 woningen met DEGO + VIVET per rij
6. **Analyse per Archtype** – eigendom, label, verwarming, praktijkfactor (gekoppeld)

---

## Licentie & gebruik

De kaart is opgesteld ten behoeve van wijkanalyse voor **gemeente Heusden / Vliedberg-project**.

- DEGO-data: eigendom opdrachtgever — niet openbaar
- VIVET-data: © PBL/CBS, [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- BAG-coördinaten: © Kadaster, [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Kaartcode: vrij herbruikbaar voor niet-commerciële doeleinden

---

*Gegenereerd mei 2026 · Analyse: DEGO × VIVET × PDOK BAG*

