---
title: Installation Guides - React TS
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation guide](prerequisites.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">ReactTs</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[FastAPI](fastapi.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Docker](docker.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---
# ReactTS {#reactts}

Hieronder zul je vinden hoe je een React app aanmaakt voor Typescript

Benodigdheden:

- Je moet node.js gedownload hebben voor het lokaal draaien van de React app: [Download Node.js](https://nodejs.org/en/download)

In de terminal moet je doormiddel van "cd" commands naar de file gaan waar het project in zal moeten zitten. Vervolgens moet je het volgende command intypen: `npx create-react-app my-app --template typescript`

Er zal nu een react app gemaakt worden voor typescript met de aangegeven naam en op de aangegeven locatie.
Om verdere commands te kunnen uitvoeren op het aangemaakte project zal je doormiddel van de cd commands naar de project folder moeten navigeren.
Je kan de react app nu starten met `npm start`. Andere commands zijn terug te vinden bij de documentatie van node.

> [!NOTE]
> Indien je gebruikt maakt van Docker zal nmp start alleen lokaal draaien en de docker container dus niet gebruiken. Indien je de app wilt draaien met docker zal je de docker container moeten draaien en hoef je zelf geen `npm start` te gebruiken.

Opzetten github project
Om de frontend op de lokale machine te krijgen kun je het volgende command uit te voeren git clone -b MVP-Team-5 https://github.com/ZuydUniversity/B2C6_B2C_Frontend.git. Om de frontend werkend te krijgen moet je eerst de backend opzetten. De frontend kun je nadat je de backend hebt aangezet met het volgende commande opstarten npm start.

Opzetten eigen ReactTS project
Om een eigen project te maken in ReactTS moet je het volgende command uitvoeren npx create-react-app my-react-app. Door nmp start uit te voeren kun je het project starten.

Hoe werkt de code?
De code bevat meerdere comments om duidelijk te maken wat elke lijn doet. De bestanden waar je naar moet kijken zijn:

App.js
PersonForm.js

---