# Oplossingen oefenlabo GDPR en AI Act

> Summiere modeloplossing, bedoeld voor de lesgever bij een sessie van 2 uur. Alternatieve motiveringen met juiste redenering zijn ook goed. Tijdsplanning: case 1 ± 50 min, case 2 ± 40 min, case 3 ± 15 min, case 4 ± 10 min; case 5 en de examenvraag zijn bonus.

---

## Case 1: Bikefun

### de 15 GDPR-checkpoints

| # | Checkpoint | Beoordeling |
|---|---|---|
| 1 | Data echt nodig | Medicatie en zorg: ja, operationeel nodig. Bankgegevens en rijksregisternummer: twijfelachtig, lijken niet strikt noodzakelijk |
| 2 | Encryptie | NEEN: data verloopt via (onbeveiligde) mail |
| 3 | HTTPS | Website/app waar data wordt ingevoerd moet https gebruiken; bovendien heeft niet elk personeelslid toegang tot de databank nodig |
| 4 | Open consent | Consent wordt niet expliciet gegeven. Voor de operationele afwerking van het kamp is toestemming niet nodig (overeenkomst); wil het bedrijf data langer bijhouden, dan is expliciete toestemming vereist |
| 5 | Granulaire opt-in | Ontbreekt: functionele cookies en marketing/profiling-cookies moeten apart kunnen worden aangevinkt |
| 6 | 3rd parties | Niet vermeld: verwerking door hotels, fietsenverhuur, ... moet worden aangegeven |
| 7 | T&C apart | Akkoord met T&C zit ingebakken in de andere voorwaarden: moet apart |
| 8 | T&C zichtbaar | Controleer plaats en leesbaarheid op de site |
| 9 | Consent intrekken | Geen systeem om data te laten wissen of consent in te trekken; moet worden voorzien (vooral relevant na het kamp) |
| 10 | Cookiebeleid | Profiling-cookies zonder consent: niet toegelaten; zie 5 |
| 11 | Securityvragen | n.v.t. |
| 12 | IP-logs | n.v.t. |
| 13 | Pay-gateway | n.v.t.: data is nodig voor identificatie en uitvoering van het kamp |
| 14 | BI-tracking weigeren | Gebruikers moeten de analytics/profiling kunnen weigeren |
| 15 | Ongevraagde tracking | Altijd verboden, ongeacht de casus |

### persoonlijke en sensitieve data

| Data | Persoonlijk | Sensitief |
|---|---|---|
| Naam, voornaam, leeftijd, geslacht | x | |
| Rijksregisternummer | x | x (uniek identificatienummer) |
| Medicatie en zorgbehoeften | x | x (gezondheidsdata) |
| Gegevens ouders (telefoon, adres, bank) | x | |
| Personeelsdata ERP (lonen, ziektegegevens) | x | eventueel x |
| Cookie/profiling-data | x (kan) | |
| Kampdata (contracten, contacten) | contactpersonen wel persoonlijk | |

### GDPR-audit (samenvatting per thema)

- **Data in kaart**: verwerkingsregister met gegeven, betrokkene, doel, grondslag, bewaartermijn, verwerker. Datastromen: app → mail → manuele invoer → databank; ERP; cookies. Elke mail en kopiëerbewerking is een extra verwerking en risico.
- **Sensitieve data**: rijksregisternummer, medicatie/zorg, eventueel personeelsgegevens. Extra eisen: expliciete grondslag, verhoogde beveiliging, data minimalisation.
- **Toestemming**: niet opt-in, niet granulair, niet apart van T&C, niet intrekbaar: verbeteren. Externe verwerkers worden niet gecommuniceerd: verbeteren.
- **Rechten**: geen proces voor inzage, correctie, verwijdering, portabiliteit of protest. Bewaartermijn voor ex-deelnemers niet gedefinieerd: storage limits schrijft verwijdering voor.
- **Datalekken**: mailkanaal is onbeveiligd. Bij een lek: melden aan de Gegevensbeschermingsautoriteit binnen 72 uur (art. 33); bij hoog risico ook betrokkenen verwittigen (art. 34), behalve als data versleuteld was. Lek met rijksregisternummers en gezondheidsdata = hoog risico (identiteitsfraude).
- **Extra info nodig**: bewaartermijnen, wie heeft databanktoegang, is de mail versleuteld, zijn er verwerkersovereenkomsten, moet er een DPO worden aangesteld.

---

## Case 2: Bikefun 2.0, AI Act

### risicoclassificatie

| Feature | Risiconiveau | Motivatie |
|---|---|---|
| AI-chatbot | beperkt risico | transparantie: gebruiker moet weten dat het AI is |
| Inschrijvingsscreening (zorgniveau) | hoog-risico | beslissingen met impact op fundamentele rechten, gebruik van gezondheidsdata |
| Risicoscore "probleemgedrag" + weigering | onaanvaardbaar | sociale scoring van individuen: verboden praktijk |
| AI-gegenereerde kampfoto's | beperkt risico | AI-content moet gelabeld worden; GDPR: toestemming ouders voor beelden van minderjarigen |
| Training op rijksregisternummers | geen zinvol AI-systeem | wel een GDPR-schending: doelbinding geschonden, sensitieve data |

### provider-verplichtingen

- **Inschrijvingsscreening (hoog-risico)**: risicobeheersysteem, datagovernance, technische documentatie en logging, menselijk toezicht, testen op bias en nauwkeurigheid, CE-markering en registratie.
- **Concreet voor de developer**: documentatie en logging in de pipeline; human-in-the-loop bij elke beslissing; bias- en rechtvaardigheidstests; geen rijksregisternummers als input; feedback-loop voor foute voorspellingen; modelversies en trainingsdata registreren.
- **Chatbot en foto's (beperkt risico)**: "je chat met AI"-melding, AI-labels op gegenereerde foto's, detecteerbaarheid van synthetische content.

### GDPR en AI Act combineren

- AI-training is een **nieuwe verwerking met een nieuw doel**: doelbindingsprincipe verbiedt zomaar hergebruik van data die voor inschrijvingen werd verzameld; er is geen nieuwe geldige grondslag.
- Rijksregisternummers in training: combinatie van sensitieve data en uniek identificatienummer. Oplossing: helemaal niet gebruiken (data minimalisation); pseudonimisering/anonimisering is hier vrijwel onmogelijk; alternatief: dataset opschonen of synthetische data.
- Weigering volledig door het model: GDPR art. 22 geeft recht om niet aan uitsluitend geautomatiseerde besluitvorming met verstrekkende gevolgen te worden onderworpen; AI Act vereist menselijk toezicht bij hoog-risico. Dus: menselijke beoordeling vóór weigering, met redenen en bezwaarmogelijkheid.

---

## Case 3: Google

### AI Act bij Big Tech

- **Transparantie**: labels bij AI-antwoorden (Gemini), watermerken op AI-content, melding dat je met AI chat.
- **Afzetten**: deels mogelijk (AI-functies uit in instellingen). Voor functionele AI is geen toestemming nodig (overeenkomst); voor training op jouw data wel: opt-out moet bestaan.
- **Modeltraining**: GDPR-recht op bezwaar (art. 21) en verwijdering. GPAI-providers moeten documentatie en copyrightbeleid hebben, trainingsdata samenvatten en systeemrisico's melden.

---

## Case 4: GDPR-boetes en AI-act boetes

- **Marriot**: inbreuk duurde jaren (sinds 2014) zonder detectie; inadequate beveiliging en controles bij de overname. Boete voor het tekort aan passende technische en organisatorische maatregelen (art. 32), niet voor de melding zelf.
- **Facebook**: de feiten (2016) speelden vóór 25 mei 2018, dus GDPR was nog niet van toepassing; de oude Britse Data Protection Act had lagere maximumboetes (500k pond).
- **AI Act-boetes**: tot 35 miljoen euro of 7% van de wereldwijde omzet voor verboden praktijken; 15 miljoen euro of 3% voor de meeste andere overtredingen; 7,5 miljoen euro of 1% voor foutieve informatie. Voor Bikefun met het "probleemgedrag"-model: tot 7% van de omzet of 35 miljoen euro, mét stopzetting en reputatieschade; rekening houden met proportioneeliteit voor kmo's.
- **Voorbeeld AI-juridische actie**: verbod op emotionele herkenning door politie (rechtbank Den Haag, 2020), Griekse DPA verbood een onderwijssurveillance-app (2020), Italiaanse garante-boete voor OpenAI/ChatGPT (2024).

---

## Voorbeeld examenvraag

### Vraag 1 (GDPR)

- **Melden binnen 72 uur** aan de gegevensbeschermingsautoriteit (art. 33), zodra vastgesteld.
- Vingerafdrukken en identiteitsgegevens = hoog risico (identiteitsfraude): **betrokkenen onverwijld informeren** (art. 34).
- Datalek **documenteren** (inbreukregister), risico-inschatting, en passende maatregelen nemen. Was de data versleuteld geweest, dan valt de informatieverplichting richting burgers mogelijk weg.

### Vraag 2 (AI Act)

- **Bouwaanvragen-prioritering**: hoog-risico (beslissingen over burgers in publieke dienstverlening): menselijk toezicht, documentatie, datagovernance.
- **AI-chatbot voor burgers**: beperkt risico: transparantie, burger moet weten dat het AI is.
- **Na de hack**: trainings- en logdata met persoonsgegevens zijn mee gelekt: valt onder de meldplicht (art. 33/34); controleer of de chatbot geleakte gegevens kan lekken of geïnjecteerd kan worden; update de risicoclassificatie en technische documentatie van beide systemen.

