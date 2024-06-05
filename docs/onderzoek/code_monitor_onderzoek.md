---
title: Onderzoek - Code Monitor
---

<div style="display:flex; justify-content:space-between; align-items:left; padding:20px; background-color:#f8f9fa; border-bottom:1px solid #e0e0e0;">
  <nav style="display:flex; gap:15px; height:30px;">
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation Guides](../installation_guides/prerequisites.md)</a>
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Meetings](../meetings/iteratie_1.md)</a>
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Onderzoek](../onderzoek/main_onderzoek.md)</a>
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Retrospectives](../retrospectives/home_retrospectives.md)</a>
  </nav>
</div>

---

<nav style="display:flex; gap:15px; height:30px;">
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Home Onderzoek](main_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Frontend](frontend_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Backend](backend_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Database](database_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Infrastructuur](infra_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Code Monitor</a>
</nav>

---

# Code Monitor onderzoek
In dit project wordt er onderzoek gedaan naar verschillende monitoring tools voor code en servers. Het doel is om uitgebreide kennis te vergaren over verschillende soorten monitoring tools om de beste keuze te kunnen maken voor de casus. Deze wiki bevat een analyse van Prometheus, Cabot, Monika, Zabbix, Sensu, Nagios Core, Monitoshi, PHP Server Monitor, Uptime Kuma en UptimeRobot waarbij de kenmerken, voordelen en nadelen van elke tool worden belicht en we een aanbevolen keuze en een tweetal alternatieve keuzes voorleggen.

## Prometheus
### Pluspunten:
- Prometheus is Open-source en heeft een grote en actieve community.
- Het heeft een sterke ondersteuning voor de mogelijkheid tot het monitoren van tijdreeksgegevens en metrics.
- Het is eenvoudig te integreren met grafische tools zoals Grafana.
- Het kent hoge prestaties en schaalbaarheid, dus is goed te gebruiken voor grotere projecten.
- Integratie met Alertmanager voor meldingen is mogelijk, inclusief Slack integratie.
### Minpunten:
- Steile leercurve, dus lastig onder de knie te krijgen voor beginners.
- Ingebouwde visualisatie ontbreekt, integratie is met tools zoals Grafana vereist.
- Kan lastig zijn voor log monitoring zonder extra tools (zoals Loki).


## Cabot
### Pluspunten:
- Cabot is Open-source.
- Het is eenvoudig te gebruiken en te configureren.
- Het is mogelijkheid om verschillende checks (HTTP, TCP, ICMP, etc.) uit te voeren.
- Het heeft ondersteuning voor meldingen via e-mail, Slack, en SMS.
### Minpunten:
- Het heeft een beperkte community en minder actieve ontwikkeling.
- Het is niet zo schaalbaar als sommige andere tools.
- Functionaliteit zijn beperk in vergelijking met uitgebreidere monitoring tools.

## Monika
### Pluspunten:
- Monika is Open-source.
- Het is eenvoudig in te stellen en te gebruiken.
- Ontworpen om HTTP-endpoints te monitoren met eenvoudige configuratie.
- Het heeft ondersteuning voor meldingen naar Slack.
### Minpunten:
- Het heeft beperkte functionaliteit, vooral wat uptime monitoring betreft.
- Het heeft weinig integraties en uitbreidingen beschikbaar.

## Zabbix
### Pluspunten:
- Zabbix is Open-source met een grote community en actieve ontwikkeling.
- Het heeft zeer veel en uitgebreide functionaliteiten voor server en netwerk monitoring.
- Het is schaalbaar en geschikt voor grotere projecten.
- Het heeft een webinterface voor makkelijke configuratie en beheer.
- Heeft ondersteuning voor meldingen via verschillende kanalen, inclusief Slack.
### Minpunten:
- Het kan ingewikkeld zijn om in te stellen.
- Het heeft een steilere leercurve voor beginners.

## Sensu
### Pluspunten:
- Sensu is Open-source met uitgebreide functionaliteiten.
- Het heeft een flexibele en schaalbare monitoring oplossing.
- Het ondersteunt zowel traditionele server monitoring als cloud-native monitoring.
- Heeft ondersteuning voor meldingssystemen zoals Slack via Sensu Go.
### Minpunten:
- De basisversie is gratis, maar vele geavanceerde functies zijn alleen beschikbaar in de betaalde versie (Sensu Go).
- Het heeft een complexere configuratie en setup.
- Het heeft een minder gebruiksvriendelijke interface in vergelijking met sommige andere tools.

## Nagios Core
### Pluspunten:
- Nagios Core is Open-source en een zeer lang bestaande tool met een grote community.
- Het heeft veel flexibiliteit en is uitbreidbaar met vele plugins.
- Het is geschikt voor het monitoren van vele uiteenlopende systemen en applicaties.
- Het heeft ondersteuning voor meldingen naar Slack via plugins.
### Minpunten:
- Heeft een verouderde webinterface.
- Het heeft een steile leercurve en het configureren kan erg tijdrovend zijn.
- De basisfunctionaliteiten zijn enigszins beperkt zonder add-ons (Nagios XI).

## Monitoshi
### Pluspunten:
- Monitoshi is open-source.
- Het is een eenvoudige tool en geschikt voor beginners.
- Het is gericht op monitoring van websites en endpoints.
- Het heeft ondersteuning voor meldingen naar Slack.
### Minpunten:
- Het heeft beperkte functionaliteit in vergelijking met andere tools.
- Het heeft een relatief kleine community en minder actieve ontwikkeling.
- Het is minder geschikt voor ingewikkelde monitoring vereisten.

## PHP Server Monitor
### Pluspunten:
- PHP Server Monitor is open-source.
- Het heeft ondersteuning voor HTTP en ICMP-monitoring.
- Het heeft ondersteuning voor meldingen naar Slack via plugins of custom scripts.
### Minpunten:
- Het heeft beperkte functionaliteit in vergelijking met andere tools.
- Het is minder schaalbaar en dus minder geschikt voor grote projecten.
- Het heeft een minder actieve community en ontwikkeling.

## Uptime Kuma
### Pluspunten:
- Uptime Kuma is open-source.
- Het heeft een moderne en gebruiksvriendelijke interface.
- Het heeft ondersteuning voor meerdere soorten checks (HTTP, TCP, DNS, etc.).
- Het heeft goede integratie met meldingssystemen zoals Slack.
- Het is specifiek ontworpen om gemakkelijk meldingen te sturen naar Slack.
### Minpunten:
- Het is nog relatief nieuw en minder ver ontwikkeld dan sommige andere tools.
- Het heeft een beperkte hoeveelheid functies vergeleken met andere oplossingen.
- Het heeft een kleinere community.

## UptimeRobot
### Pluspunten:
- Het heeft een eenvoudige setup en gebruik.
- Het heeft een goede uptime monitoring met verschillende checks (HTTP, PING, etc.).
- Het heeft ondersteuning voor meldingen naar Slack.
### Minpunten:
- UptimeRobot is niet open-source
- Het heeft een beperkte open-source mogelijkheden, voornamelijk een commerciële dienst.
- Het is minder geschikt voor diepgaande server monitoring.
- De gratis versie heeft beperkingen in functionaliteit en aantal checks.


## Aanbeveling
Gezien de vereiste voor open-source, Slack-integratie, en flexibiliteit om gemakkelijk van tool te kunnen wisselen, bevelen we de volgende tools aan.

**Aanbevolen keuze:** Prometheus met Alertmanager.

Prometheus biedt krachtige monitoring en metrics, en Alertmanager zorgt voor meldingen, inclusief Slack-integratie. Dit biedt een toekomstbestendige oplossing met veel flexibiliteit en schaalbaarheid.

**Alternatieve keuze:** Uptime Kuma

Uptime Kuma biedt een gebruiksvriendelijke setup en specifieke ondersteuning voor meldingen naar Slack. Het is ideaal voor een snelle implementatie en eenvoudig gebruik, vooral als de primaire focus ligt op uptime monitoring met directe meldingen in Slack.

**Tweede alternatieve keuze:** Zabbix

Zabbix biedt uitgebreide monitoring mogelijkheden en integratie met Slack, hoewel het complexer is om op te zetten en te beheren. Het is zeer schaalbaar en geschikt voor grotere omgevingen.

#### Bronnen
* https://uptimerobot.com/blog/open-source-monitoring-tools/
* https://prometheus.io/
* https://cabotapp.com/
* https://monika.hyperjump.tech/
* https://www.zabbix.com/
* https://en.wikipedia.org/wiki/Zabbix
* https://sensu.io/
* https://nl.wikipedia.org/wiki/Nagios
* https://www.nagios.org/projects/nagios-core/
* https://monitoshi.com/
* https://www.phpservermonitor.org/
* https://medium.com/@williamdonze/uptime-kuma-self-hosted-monitoring-tool-5b97fc0c360d
* https://youtu.be/Wu1t5tmxZl4?si=cZjd4OIANf5_4Q9Z
* https://uptimerobot.com/website-monitoring/


---