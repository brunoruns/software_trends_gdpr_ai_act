# Oefenlabo GDPR en AI Act

> **Duur: 2 uur.** Werk de cases in volgorde. Case 5 en de examenvraag zijn bonusopdrachten voor wie klaar is. Gebruik de slides als naslagwerk.

| Case | Thema | Tijd |
|---|---|---|
| 1 | Bikefun: GDPR-audit | ± 50 min |
| 2 | Bikefun 2.0: AI Act | ± 40 min |
| 3 | Google: AI bij Big Tech | ± 15 min |
| 4 | Boetes GDPR en AI Act | ± 10 min |
| 5 | Ongeëncrypteerd internet | bonus |
| - | Voorbeeld examenvraag | bonus |

## Case 1: Bikefun

Bikefun is een (klein en fictief) bedrijf dat kinderkampen organiseert. De kinderen kunnen zich via de website of app inschrijven, en gaan dan met de bus op reis waar ze ter plekke rondfietsen.

Achterliggend heeft het bedrijf volgende systemen:

- Een app/website voor ouders om plaatsen voor hun kinderen te reserveren (de app is een skin rond de website)
- Een ERP-systeem voor boekhouden, en ook de lonen van het personeel
- Een interne databank waarbij onder meer volgende gegevens worden opgeslagen:
  - Toekomstig geplande kampen
    - Lijst van contacten ter plaatse, zoals lokale fietsenverhuur, logies, ...
    - Contracten, prijszettingen
  - Deelnemers
    - Naam, voornaam
    - Leeftijd, geslacht
    - Rijksregisternummer
    - Eventuele medicatie die het kind nodig heeft
    - Eventuele andere zorg die het kind nodig heeft
    - Gegevens ouders
      - telefoonnummer / noodnummer
      - thuisadres
      - bankgegevens voor de betaling

Deze databank is momenteel lokaal op het interne, goed beveiligde netwerk en versleuteld met een paswoord. De personeelsleden zetten manueel de inschrijvingen die ze van de app krijgen doorgestuurd per mail, over naar deze databank. De app zelf is niet rechtstreeks verbonden met de database, maar verstuurt haar data via een email naar het bedrijf.

Verder verzamelt het bedrijf op haar websites via cookies informatie over het profiel van de bezoekers om te kijken of het het aanbod beter op hen kan afstemmen.

De website ziet er in essentie als volgt uit:

- geen aparte cookies
- geen vermelding dat de data zal worden verwerkt door externe partijen, nl hotels en dergelijke
- akkoord met terms en condities niet apart van de andere voorwaarden

### GDPR-checkpoints (slides: "Software GDPR-proof maken", tips 1 tot 15)

Bekijk de slides van de les, met de 15 checkpoints voor een applicatie. Beoordeel voor elk van de checkpoints of er iets moet veranderen. Noteer per checkpoint: oké, verbeteren of n.v.t., met een korte motivatie.

### persoonlijke en sensitieve data (slides: "Persoonlijke data" en "Sensitieve data")

Beoordeel welke verzamelde data (van klanten zowel als van personeel) persoonlijke data is, en welke sensitief is.

### GDPR-audit van Bikefun (slides: "Datalekken: de 72-uursregel", en "Individuele GDPR-rechten")

Doorloop volgende vragen voor de Bikefun-case. Beantwoord ze schriftelijk met verwijzing naar de slide of het principe waarop je je antwoord baseert.

**Data in kaart brengen**

1. Welke persoonlijke gegevens verwerkt Bikefun van wie (kinderen, ouders, personeel, contacten ter plaatse)? Maak een overzichttabel: gegeven, categorie betrokkene, doel, grondslag, bewaartermijn, door wie verwerkt.
2. Welke systemen verwerken die gegevens (app, mail, databank, ERP)? Waar stromen de gegevens tussen door, en waar ontstaan er kopieën?

**Sensitieve data**

5. Welke gegevens zijn sensitief in de zin van de GDPR? Welke extra eisen gelden daarvoor?

**Toestemming**

6. Wordt op de correcte manier toestemming gevraagd? Controleer: is consent opt-in, granulair, apart van de terms and conditions, en kan ze worden ingetrokken?
7. Wordt de gebruiker geïnformeerd dat data wordt verwerkt door externe partijen (hotels, fietsenverhuur)?

**Rechten van betrokkenen**

8. Hoe kan een ouder of medewerker zijn rechten uitoefenen (inzage, correctie, verwijdering, portabiliteit, protest)? Welk proces ontbreekt er nog?
9. Hoe lang bewaart Bikefun gegevens van ex-deelnemers? Wat zegt het storage limits-principe hierover?

**Datalekken**

10. Het mailkanaal tussen app en databank: wat kan hier mislopen? Wanneer moet Bikefun een datalek melden, aan wie, en binnen welke termijn?
11. Wat zou een datalek met de interne databank betekenen? Welke gegevens zijn dan precies gelekt, en hoe zwaar is dat (denk aan rijksregisternummers en gezondheidsdata)?

**Slotvraag**

12. Welke extra informatie heb je van dit bedrijf nog nodig om deze audit af te ronden?

---

## Bikefun 2.0, AI-features toevoegen

Bikefun wil moderniseren en overweegt volgende AI-features:

- Een **AI-chatbot** op de website die vragen van ouders beantwoordt, deels op basis van hun accountgegevens
- Een **automatische inschrijvingsscreening**: een AI-model dat inschrijvingen scant op medicatie en zorgbehoeften en per kind een "zorgniveau" (laag/middel/hoog) bepaalt
- Een **risicoscore voor "probleemgedrag"**: op basis van historische kampdata. Kinderen met een hoge score worden op voorhand geweigerd
- **AI-gegenereerde kampfoto's** voor marketing: foto's van kinderen worden door een AI-model verwerkt tot promotiemateriaal
- Een **AI-instrument**: het AI-model wordt getraind op de rijksregisternummers van vorige deelnemers (die staan nog in de databank)

### AI Act risicoclassificatie (slides: "Vier risiconiveaus" en "Verboden AI-praktijken")

Beoordeel elke voorgestelde AI-feature:

- Op welk **risiconiveau** valt deze volgens de AI Act (onaanvaardbaar, hoog-risico, beperkt risico, minimaal risico)?
- Welke features zijn mogelijk **verboden**?
- Welke features vallen onder de **transparantieverplichtingen** (gebruiker moet weten dat er met AI wordt gecommuniceerd of dat content AI-gegenereerd is)?

> Tip: loop dezelfde tabel af als in de slides bij "Vier risiconiveaus": één rij per feature met risiconiveau en motivatie.

### provider-verplichtingen (slides: "Provider-verplichtingen bij hoog-risico" en "Transparantieverplichtingen")

Voor de features die als hoog-risico of beperkt risico gelden:

- Welke **verplichtingen** gelden voor Bikefun als provider/deployer (risicobeheer, datagovernance, documentatie, menselijk toezicht, bias-testen)?
- Wat betekent dit **concreet voor de developer**: welke technische maatregelen bouw je in? (slides: "Richtlijn 3" tot "Richtlijn 6" in het hoofdstuk "AI Act praktische richtlijnen")

### GDPR en AI Act combineren (slides: "Datalekken: de 72-uursregel" en "Richtlijn 7: combineer met GDPR")

- Welke data in het AI-verhaal valt onder de GDPR? Denk aan het dataminimalisatieprincipe en het doelbindingsprincipe: mag data die voor inschrijvingen werd verzameld zomaar voor AI-training worden hergebruikt?
- Rijksregisternummers in een trainingsdataset: wat gaat er fout, en hoe los je dit op (anonimisering, pseudonimisering, data minimalisation)?
- Mag het bedrijf een weigeringsbeslissing volledig aan het AI-model overlaten? Wat zegt de GDPR over **automated decision making**, wat zegt de AI Act over **menselijk toezicht**?

---

## Case 3: Google

Google is een grote speler die zich sterk heeft moeten aanpassen aan de GDPR-wetgeving. Kijk naar de instellingen van je Google account (of van een andere speler zoals Facebook) en link dit met je rechten als EU burger.

> Geen account? Zoek instellingen op via screenshots in de handleiding van Google, of werk samen met je buur.

### AI Act bij Big Tech (slides: "Transparantieverplichtingen" en "General purpose AI (GPAI)")

Bestudeer nu de AI-aspecten van je account (bv. AI-suggesties in Gmail, Gemini in Search, AI-gegenereerde samenvattingen):

- Waar zie je **transparantie** over AI (labels, meldingen)?
- Kan je AI-functies **afzetten** of beperken? Wat zegt dit over consent en de GDPR?
- Worden jouw data gebruikt voor **modeltraining**? Kan je dit weigeren? Welk recht uit de GDPR en welke AI Act-verplichting voor GPAI-providers speelt hier?

---

## Case 4: GDPR-boetes

### GDPR Act-boetes

Volgende bedrijven hebben allemaal een (fikse) boete gekregen. Ze komen van de Britse ICO, die de gegevens van burgers beschermt. In België is dit de gegevensbeschermingsautoriteit.

- In november 2018 bracht Marriot International de Information Commissioner's Office (ICO) op de hoogte van een cyberaanval, waarbij ongeveer 339 miljoen gastenrecords werden aangetast. Persoonlijke gegevens, waaronder betalingsgegevens en paspoortnummers, van ongeveer 30 miljoen records met betrekking tot inwoners van de Europese Economische Ruimte (EER) en 7 miljoen met betrekking tot inwoners van het VK werden openbaar gemaakt. De aanval begon in 2014 in de archieven van Starwood Hotels, die later in 2016 door Marriot werden overgenomen. Marriot ontdekte de hack in september 2018, en gaf in november een melding. Toch kregen ze hier een fikse boete voor. Waarom?
- In oktober 2018 legde ICO Facebook (FB) een boete van £ 500.000 op, de hoogste op dat moment, voor zijn rol in het Cambridge Analytica-schandaal. Cambridge Analytica, een Brits politiek adviesbureau, heeft zonder hun toestemming miljoenen mensen uit hun FB-profielen gehaald en gebruikt voor de Amerikaanse verkiezingscampagne van 2016. ICO startte het onderzoek in 2017.

De boete van slechts 500 000 pond is een peulenschil, want GDPR-boetes kunnen oplopen tot 4% van de omzet van een bedrijf. Waarom heeft Facebook geen hogere boete gekregen?

### AI Act-boetes

- Wat zijn de maximale boetes onder de AI Act, en voor welke overtredingen?
- Denk terug aan case 2: als het "probleemgedrag"-model was geïmplementeerd en het bleek een verboden praktijk, welke boete zou dan mogelijk zijn voor een klein bedrijf als Bikefun?
- Zoek één voorbeeld van een boete of juridische actie over AI (bv. AI-gezichtsherkenning door politie in Nederland). Bespreek kort. Gebruik hiervoor maximaal 5 minuten: één bron volstaat.

---

## Voorbeeld examenvraag

Beschouw volgende case:

Een willekeurige (grote!) stad in Vlaanderen wordt gehacked, waarbij een hoop gegevens worden gestolen. Het gaat onder andere om adresgegevens, identiteitsgegevens, vingerafdrukken van sommige inwoners, bouwaanvragen, schoolgegevens, ...

We gaan er in dit fictieve voorbeeld van uit dat het 100% zeker is welke data gestolen is na het vaststellen van de hack.

### Vraag 1

Welke actie moet deze stad zeker nemen volgens de GDPR-wetgeving?

### Vraag 2: AI Act

De stad gebruikt bovendien een AI-systeem dat bouwaanvragen automatisch prioriteert en een AI-chatbot voor burgers die vragen over schoolinschrijvingen beantwoordt.

- Onder welk risiconiveau valt elk systeem volgens de AI Act?
- Wat moet de stad doen na de hack, ook met betrekking tot deze AI-systemen?

---

## Bronnen

- www.unizo.be/privacy
- https://www.gegevensbeschermingsautoriteit.be/burger/startpagina
- https://whynohttps.com/
- https://www.cookielawinfo.com/gdpr-fines-biggest-gdpr-violation-examples/
- https://artificialintelligenceact.eu/
- https://artificialintelligenceact.eu/the-act/
- https://artificialintelligenceact.eu/assessment/
- https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai

