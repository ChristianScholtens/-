---
title: Kennen & Kunnen - Informatica (TP1)
aliases:
  - Informatica Kennen & Kunnen
  - Informatica Samenvatting
---

# 💻 Samenvatting Toetsstof TP1 Informatica

> [!INFO] Origineel PDF Document
> Wil je het originele PDF-document inzien of downloaden?  
> 👉 **[[Toetsweek 1/Informatica/Samenvatting PDF|Klik hier om de volledige PDF te bekijken (met viewer)]]** of **<a href="./Informatica-Samenvatting.pdf" target="_blank">download het bestand direct</a>**.

---

# Deel 1: Python

## 1.1 Variabelen, Geheugen en Datatypes
Het declareren van een variabele slaat een waarde op in het werkgeheugen (RAM). Python kent een intern referentie-adres toe en koppelt de variabelenaam daaraan. Wijs je een variabele een nieuwe waarde toe, dan verwijst de naam voortaan naar die nieuwe waarde.

### Rollen van variabelen
* **Vaste waarde (constante)**: Een waarde die na toewijzing ongewijzigd blijft gedurende het programma (in Python bij afspraak geschreven in HOOFDLETTERS, zoals `PI = 3.14159`).
* **Transformatie**: Een variabele waarvan de waarde ontstaat door een bewerking op een andere variabele.
  ```python
  lengte_m = 1.85
  lengte_cm = lengte_m * 100  # Transformatie van lengte_m
  ```
* **Flag**: Een boolean variabele die een programmastatus bijhoudt.
  ```python
  game_over = False
  ingelogd = True
  ```
* **Doelwaarde**: Een variabele die meeloopt in een lus om de beste match op te slaan (zoals het grootste getal, de kleinste waarde of een specifieke vondst).
  ```python
  scores = [12, 45, 78, 34]
  hoogste = scores[0]
  for score in scores:
      if score > hoogste:
          hoogste = score
  # Of direct in Python:
  hoogste = max(scores)
  ```
* **Counter**: Houdt bij hoe vaak een gebeurtenis plaatsvindt of hoe vaak een lus draait.
  ```python
  aantal_pogingen = 0
  while aantal_pogingen < 3:
      aantal_pogingen += 1
  ```
* **Iterator Index**: Loopt stap voor stap door een lijst, reeks of tekst heen.
  ```python
  for letter in "Python":
      print(letter)  # 'letter' is de stapper
  ```

### Regels en conventies voor variabelenamen
* Geen spaties toegestaan; gebruik underscores (`aantal_pogingen`).
* Moeten altijd beginnen met een letter of underscore (nooit met een cijfer).
* Mogen uitsluitend letters, cijfers en underscores bevatten.
* Grote getallen kun je leesbaar houden met underscores: `1_000_000`.
* Wetenschappelijke e-notatie werkt voor machten van 10: `5e9` staat voor $5 \times 10^9$ (resulteert in een `float`).

### Invoer, Uitvoer en Omgeving
* `print()`: Schrijft gegevens naar het scherm. Meerdere argumenten scheid je met een komma.
* `#`: Commentaarteken. De Python-interpreter negeert alles achter dit teken op dezelfde regel.
* `type()`: Geeft het datatype van een variabele of waarde terug.
* **Basisdatatypes**:
  * `str` (String): Tekst tussen enkele (`'...'`) of dubbele (`"..."`) aanhalingstekens.
  * `int` (Integer): Een geheel getal (positief, negatief of nul).
  * `float` (Float): Een kommagetal, geschreven met een decimaalpunt (`.`).
  * `bool` (Boolean): Waarheidswaarde, uitsluitend `True` of `False`.

---

## 1.2 Invoer, Typeconversie (Casting) en Stringbewerking
De functie `input()` leest tekst in via het toetsenbord.
> [!WARNING] Belangrijk
> `input()` levert **altijd** een `str` op, zelfs als de gebruiker een getal invoert.

### Typeconversie (Casting)
Wil je met ingevoerde getallen rekenen, dan moet je de string expliciet omzetten:
* `int()`: Verandert een tekst of kommagetal naar een geheel getal (decimalen worden afgekapt).
* `float()`: Verandert tekst of geheel getal naar een kommagetal.
* `str()`: Zet getallen of booleans om naar tekst.

### Tekstbewerking en f-strings
* `.upper()`: Zet alle letters om naar hoofdletters.
* `.lower()`: Zet alle letters om naar kleine letters.
* `.split()`: Splitst een tekst op in een lijst van woorden.
* `.replace("oud", "nieuw")`: Vervangt een stuk tekst door iets anders.
* **f-strings (formatted strings)**: Voeg variabelen en berekeningen direct in tekst in door een `f` voor het eerste aanhalingsteken te plaatsen en variabelen tussen `{...}` te zetten.

---

## 1.3 Operatoren en Booleaanse Logica

### Rekenkundige operatoren
| Operator | Betekenis | Voorbeeld (`a = 10`, `b = 3`) | Resultaat |
| :--- | :--- | :--- | :--- |
| `+` | Optellen (of strings samenvoegen) | `a + b` | `13` |
| `-` | Aftrekken | `a - b` | `7` |
| `*` | Vermenigvuldigen | `a * b` | `30` |
| `/` | Normale deling (levert altijd `float`) | `a / b` | `3.3333...` |
| `//` | Gehele deling (rondt omlaag af, levert `int`) | `a // b` | `3` |
| `**` | Tot de macht | `a ** b` ($10^3$) | `1000` |
| `%` | Modulo (restwaarde na deling) | `a % b` | `1` |

### Vergelijkings- en Logische operatoren
* `==` (gelijk aan) en `!=` (niet gelijk aan)
* `>` (groter dan) en `<` (kleiner dan)
* `>=` (groter dan of gelijk aan) en `<=` (kleiner dan of gelijk aan)
* `and`: `True` zodra beide voorwaarden waar zijn.
* `or`: `True` zodra minstens één voorwaarde waar is.
* `not`: Draait de waarheidswaarde om (`not True` $\rightarrow$ `False`).

### Waarheidstabel
| P | Q | P and Q | P or Q | not P |
| :--- | :--- | :--- | :--- | :--- |
| True | True | True | True | False |
| True | False | False | True | False |
| False | True | False | True | True |
| False | False | False | False | True |

---

## 1.4 Selecties: if, elif en else
Met een selectie bepaal je welke regels code uitgevoerd worden op basis van voorwaarden.
* **Indentatie**: Python gebruikt 4 spaties om codeblokken te groeperen.
* **Volgorde**: Python doorloopt de takken van boven naar beneden. Zodra een voorwaarde `True` oplevert, voert Python uitsluitend dat blok uit en slaat de rest over.

---

## 1.5 Datastructuren: Lists
Een list is een geordende verzameling waarden die je na het aanmaken kunt wijzigen (muteerbaar).
* **Indexering vanaf 0**: Het eerste element staat op index 0 (`lijst[0]`), het laatste op index `-1`.
* `len(lijst)`: Geeft het totale aantal elementen in de lijst terug.
* `.append(item)`: Voegt een element toe aan het einde van de lijst.
* `.insert(index, item)`: Voegt een element in op positie index.
* `.pop(index)`: Verwijdert en retourneert het element op de index.
* `.remove(waarde)`: Zoekt en verwijdert de eerste instantie van de waarde.
* **Slicing** (`lijst[start:stop]`): Selecteert een deel vanaf start tot stop (exclusief).
* `in`: Controleert of een waarde in de lijst voorkomt.
* `min(lijst)`, `max(lijst)` en `sum(lijst)`: Wiskundige bewerkingen.

---

## 1.6 Datastructuren: Dictionaries
Een dictionary bewaart gegevens in sleutel-waardeparen (`key-value`).
* Gemaakt met accolades `{}` of `dict()`.
* Waarden opvragen via `woordenboek[sleutel]`.
* `.get(sleutel, standaardwaarde)` voorkomt een `KeyError` als de sleutel niet bestaat.

---

## 1.7 Loops: for-loops en while-loops
* **Begrensde herhaling (`for`-loop)**: Gebruik als het aantal herhalingen vooraf bekend is of om door een lijst/tekst te lopen.
  * `range(stop)`: 0 tot stop (exclusief).
  * `range(start, stop[, stap])`: Vanaf start tot stop met vaste stapgrootte.
* **Voorwaardelijke herhaling (`while`-loop)**: Blijft draaien zolang de voorwaarde `True` oplevert.

---

# Deel 2: Cybersecurity

## 2.1 De CIA-Triade
De CIA-triade is het fundament van informatiebeveiliging:
* **Vertrouwelijkheid (Confidentiality)**: Alleen geautoriseerde personen kunnen data inzien. *(Maatregelen: encryptie in transit via TLS/HTTPS en at rest, Least Privilege, MFA).*
* **Integriteit (Integrity)**: Gegevens blijven aantoonbaar juist, volledig en beschermd tegen ongeoorloofde wijziging. *(Maatregelen: cryptografische hashing zoals SHA-256, digitale handtekeningen, audit logs).*
* **Beschikbaarheid (Availability)**: Geautoriseerde gebruikers hebben op elk vereist moment toegang. *(Maatregelen: redundantie, failover, 3-2-1 back-up regel, DDoS-mitigatie).*

---

## 2.2 Cryptografie en Versleuteling

| Eigenschap | Symmetrische Encryptie | Asymmetrische Encryptie |
| :--- | :--- | :--- |
| **Sleutels** | Eén identieke geheime sleutel voor zowel ver- als ontsleuteling. | Een gekoppeld paar: publieke sleutel (openbaar, versleutelt) en private sleutel (geheim, ontsleutelt). |
| **Voorbeelden** | Caesarcijfer, AES. | RSA, TLS/HTTPS-certificaten. |
| **Sleuteluitwisseling** | Kwetsbaar: sleutel moet vooraf veilig gedeeld worden. | Veilig: publieke sleutel mag openbaar rondgaan. |
| **Kraaktechnieken** | Brute-force, frequentieanalyse van letters. | Wiskundige ontbinding van zeer grote priemfactoren. |

---

## 2.3 De Drie Kwetsbaarheden
1. **De menselijke factor (gebruikers)**: Zwakke/hergebruikte wachtwoorden, social engineering (phishing).
2. **Communicatie (netwerk)**: Onversleutelde verbindingen (open wifi), Man-in-the-Middle (MitM).
3. **Het systeem (hard- en software)**: Programmeerfouten, buffer overflows, ontbrekende security patches.

---

## 2.4 Dreigingsactoren en Attributie
* **Script kiddies**: Onervaren aanvallers die kant-en-klare tools draaien zonder diep inzicht.
* **Cybercriminelen**: Georganiseerde groepen met financieel gewin als doel (ransomware, bankfraude).
* **APT's (Advanced Persistent Threats) & Staatsactoren**: Professionele teams van inlichtingendiensten voor spionage en sabotage.
* **Attributie**: Het bewijzen wie achter een aanval zit (zeer complex door proxy's, VPN's, Tor, false flags en het wissen van logs).

---

## 2.5 Overzicht Malwaretypen
* **Worm**: Verspreidt zich geheel zelfstandig over computernetwerken zonder gebruikersinteractie.
* **Trojan**: Vermomt zich als legitieme software om de gebruiker te verleiden tot installatie.
* **Ransomware**: Gijzelsoftware die bestanden versleutelt en losgeld eist.
* **Rootkit**: Nestelt zich diep in het besturingssysteem met root-rechten en verbergt zich voor virusscanners.
* **Spyware**: Verzamelt stiekem privégegevens, surfgedrag en bestanden.
* **Keylogger**: Registreert elke toetsaanslag om wachtwoorden en privéchats af te luisteren.
* **Adware**: Toont ongevraagd advertenties en pop-ups.

---

## 2.6 Aanvalstechnieken en Stuxnet
* **Social Engineering**: Phishing, Spearphishing (gericht), Whaling (gericht op directeuren), Deepfakes, Fysiek binnendringen, Brute-force & Dictionary attacks.
* **Netwerkaanvallen**: Man-in-the-Middle (MitM), Evil Twin (valse hotspot), DNS-spoofing, DDoS via botnet, Stingray, Typosquatting (bijv. `gogle.com`).
* **Systeemexploitatie**:
  * **RCE (Remote Code Execution)**: Op afstand code uitvoeren op een ander systeem.
  * **Root Access**: Hoogste beheerdersrechten overnemen.
  * **SQL-injectie (SQLi)**: Databasecommando's via invoervelden forceren (`' OR '1'='1`).
  * **Zero-day exploit**: Misbruik maken van een bug waar nog geen patch voor bestaat.
* **Stuxnet (2010)**: Eerste grootschalige cyberwapen. Saboteerde het Iraanse kernprogramma (Natanz) door PLC-controllers van uraniumcentrifuges kapot te draaien via 4 zero-days, terwijl sensoren normale waarden rapporteerden.

---

## 2.7 Beveiligingsmaatregelen
* **Toegangsbeheer**: Wachtwoordmanagers, Passphrases (`kat-fiets-maan-koffie`), MFA (minstens 2 van: *wat je weet*, *wat je hebt*, *wat je bent*).
* **Netwerk**: Firewalls, OSINT (Open Source Intelligence), VirusTotal (70+ scanners).
* **Beleid**: Meldplicht Datalekken (AVG: melden binnen 72 uur bij de Autoriteit Persoonsgegevens), Responsible Disclosure.
* **Teams**: **Red Team** (aanvallers simuleren) vs. **Blue Team** (actief monitoren en verdedigen).

---

# Deel 3: Digitale Privacy en Maatschappij

## 3.1 Tracking en Profilering
* **Cookies**: First-party (eigen domein, bijv. winkelmandje) vs. Third-party (advertentienetwerken over meerdere websites).
* **Browser Fingerprinting**: Identificatie via tientallen systeemkenmerken (resolutie, lettertypen, GPU, plugins) zonder afhankelijk te zijn van cookies.
* **Digitale profilering**: Gedragsdata analyseren om toekomstig koop- of stemgedrag te voorspellen.
* **Dark Patterns**: Misleidende interfaces die gebruikers naar privacy-onvriendelijke keuzes sturen.

## 3.2 Maatschappelijke Casussen
* **De Toeslagenaffaire**: Geautomatiseerde risico-algoritmes met vooringenomenheid (*algorithmic bias*) bestempelden tienduizenden onterecht als fraudeur, met de val van het kabinet als gevolg.
* **Cambridge Analytica**: Ongeoorloofde data van miljoenen Facebook-gebruikers werd gekoppeld aan psychografische profielen voor gerichte politieke manipulatie (Amerikaanse verkiezingen 2016, Brexit).

## 3.3 Wet- en Regelgeving
* **AVG / GDPR**: Europese privacywetgeving met rechten op inzage, correctie en vergetelheid.
* **Autoriteit Persoonsgegevens (AP)**: Toezichthouder met bevoegdheid tot boetes (tot €20 miljoen of 4% van de wereldwijde jaaromzet).
* **DSA & DMA**: Europese wetten die grote platforms (*gatekeepers*) dwingen tot transparantie en eerlijke concurrentie.

## 3.4 Privacy Enhancing Technologies (PETs)
* **VPN**: Versleutelde tunnel die het lokale netwerk afschermt en je IP-adres maskeert.
* **End-to-End Encryptie (E2EE)**: Berichten worden alleen op de apparaten van zender en ontvanger ontsleuteld; servers kunnen de inhoud niet inzien.
