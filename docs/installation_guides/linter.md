---
title: Installation Guides - Linter
---

<div style="display:flex; justify-content:space-between; align-items:left; padding:20px; background-color:#f8f9fa; border-bottom:1px solid #e0e0e0;">
  <nav style="display:flex; gap:15px; height:30px;">
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation Guides](../installation_guides/prerequisites.md)</a>
    <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Meetings](../meetings/iteratie_1.md)</a>
  </nav>
</div>

---

<nav style="display:flex; gap:15px; height:30px;">
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation guide](prerequisites.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[ReactTs](reactts.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[FastAPI](fastapi.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Docker](docker.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Linter</a>
</nav>

---

# Linter {#linter}

## Backend Linter

De backend linter zorgt ervoor dat de code die niet aan de stijl regels voldoet niet naar de main branch gepulled kan worden. Om te weten waar precies de fouten zitten is het handig om een lokale linter op te zetten die aangeeft welke delen van de code niet de juiste stijl aanhouden. Dit kan gedaan worden door pylint op visual studio code te installeren. Om deze op te zetten moet je het volgende doen:

1. Open visual studio code en gaa naar Extensions
2. Voer "Pylint" in de zoekbalk in
3. Selecteer pylint en klik op install
4. Restart visual studio code

Na de instalatie gedaan te hebben zou je in de output tab van visual studio code alle linter problemen moet zien. Als je in een python file bezig bent worden ook hier de linter problemen zichtbaar doormiddel van een blauwe lijn onder de code met de foute stijl. Als er geen problemen meer in de output tab staan zou alles goed moeten zijn om naar de main te sturen.

## Frontend Linter

De frontend linter zorgt ervoor dat de code die niet aan de stijl regels voldoet niet naar de main branch gepulled kan worden. Om makkelijk de code stijl toe te passen kun je in visual studio code de prettier extension downloaden. Met deze extension kun je makkelijk de code stijl toepassen op de code die je geschreven hebt. Om prettier te installeren moet je de volgende stappen volgen:

1. Open visual studio code en gaa naar Extensions
2. Voer "Prettier" in de zoekbalk in
3. Selecteer Prettier en klik op install
4. Restart visual studio code

Na de installatie gedaan te hebben kun je prettier gebruiken om je code te formateren. Eerst open je de file waar je de code stijl op wilt toepassen. Daarna doe je een rechtermuisklik in het bestand en klik je op "Format Document" om het document te formateren met prettier.


---