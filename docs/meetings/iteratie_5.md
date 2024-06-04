---
Titel: iteratie_5
---

<div style="display:flex; justify-content:space-between; align-items:left; padding:20px; background-color:#f8f9fa; border-bottom:1px solid #e0e0e0;">
  <nav style="display:flex; gap:15px; height:30px;">
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation Guides](../installation_guides/prerequisites.md)</a>
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Meetings](../meetings/iteratie_1.md)</a>
  </nav>
</div>

---

<nav style="display:flex; gap:15px; height:30px;">
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 1](iteratie_1.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 2](iteratie_2.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 3](iteratie_3.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 4](iteratie_4.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 5](iteratie_5.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 6](iteratie_6.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 7](iteratie_7.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 8](iteratie_8.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 9](iteratie_9.md)</a>
</nav>

---

# Meeting
## Code coverage threshhold 
Beginnen met 80% omdat de applicatie kritische informatie bevat, dit kan wellicht nog verhoogd worden. Tijdens iteratie 5 laten we de code coverage uit en zorgen we dat het percentage omhoog gaat naar x%. Na iteratie 5 zetten we de coverage aan op dit percentage en werken we verder naar een hoger percentage. 

We testen alleen wat geschreven is door iemand, niet wat gegenereerd wordt door node.ts etc. 

## Naam voor de app
We maken een thread in Slack voor de naam van de app, hier kunnen mensen namen inzetten en hier maken we een poll van eind deze week.

## Domeinnaam
denaamvandeapp.portal.com

## Definition of done 
- Het moet gedocumenteerd zijn
- Testen moeten geschreven zijn totdat je de hele functie getest hebt
- Het moet gereviewed zijn door iemand die er niet aan gewerkt heeft, het liefst iemand die niet in je team zit
- Gebruikersdocumentatie moet geschreven zijn (niet gepubliceerd). Dit gaan we doen in de Github Wiki. Gebruikersdocumentatie blijft high level (niet gedetailleerd).

## Containernamen
Eerst docker image tags onderzoeken.

## Releasemoment 
Onderzoek doen naar releasemomenten en automatiseren van release. 

---

# Functionaliteiten
## Stakeholders
* Artsen
* Fysio therapeuten
* Onderzoekers
* Anderen

## Pagina's
### Inlogscherm
### Dashboard
* Kalender
* Profiel
* Notities

#### Navigatiemenu
* Kalender pagina
* Resultaten pagina
* Patientenoverzicht pagina
* Afspraak toevoegen
* Instellingen

### Resultaten pagina (Hoe gaan we hiermee om????)
* Lijst met patienten die uitslagen hebben -> Naam, type, datum van uitslag, bekijk uitslag, verwijder uitslag, download uitslag
* Sorteer op datum

### Gedetailleerde resultaten per soort???
* Patientgegevens
* Uitslag
* Bloedchemie
* Foto's & Notities

### Patientenoverzicht
* Een overzicht van alle patienten -> Leidt vervolgens naar een gedetailleerde patient overzicht (met persoonsgegevens)

### Patient sessie verslag
* Patient informatie
* Medicatie informatie

### Instellingen
* Meldingen -> Resultaten
* Light/dark mode
* Logboek
* Resultaten
* Dashboard

---

## CRUD
* Artsen/Fysio/Onderzoeker/Admin
* Notities
* Verslagen
* Patienten
* Instellingen
* Afspraken
* Medicatie
* Resultaten

---

## Opdeling
### Groep 1
* Agenda/Kalender
  - Afspraken, sessies & patienten
* Afspraken
  - CRUD

### Groep 2
* Patient
  - Medicatie
  - CRUD
  - Overzicht

### Groep 3
* Dashboard
  - Geplande afspraken
  - Agenda/kalender
  - Notities
* Resultaten
* Sessies

### Groep 4
* NOTITIES!!!!!!!!!!!!!!!!!
  - Per patient
* Instellingen
* Beheerschermen

### Groep 5
* Login & Aanmelden
  - Credentials
* Navbar/menu aan de zijkant  
* Conceptueel klasse diagram

---

## NOTE
Maak zoveel mogelijk als een component, zodat je zo veel mogelijk kan hergebruiken

## Productowner
* Notities alleen per patient
* Geen download
* 3 rollen
  - Arts -> 1 patient per keer
  - Fysio -> Bewegingsdata
  - Onderzoeker -> Meerdere patienten per keer (totaal plaatje)
  - Beheerder
  -> Zelfde dashboard andere focus/rechten
* Alleen volledige kalender
* Arts/fysio maakt patient aan
* Beheerder ziet de patient gegevens niet in!
* Dummy data is goed
* Medicatie voldoende voor alleen string -> Extra zou selectieveldt zijn
* Meerdere specialisten kunnen gekoppeld worden aan een patient