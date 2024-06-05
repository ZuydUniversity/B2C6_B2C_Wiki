---
title: Installation Guides
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Installation guide</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[ReactTs](reactts.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[FastAPI](fastapi.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Docker](docker.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---

# Prerequisites {#prerequisites}

### Installatie

Om de backend die aanwezig is op de github te ebruiken moeten eerst enkele dingen geïnstalleerd worden.
Onderstaand is een lijst met de links en/of commands die nodig zijn om deze te installeren:

1. MariaDB: De database kun je hier installeren: https://mariadb.org/ (versie: 11.3.2) Zorg ervoor dat je het wachtwoord dat je ingesteld hebt
   onthoudt, omdat je deze later nog nodig hebt voor de backend.
2. DBeaver(GUI voor MariaDB): Als je al een andere GUI voor MariaDB geïnstalleerd hebt is DBeaver niet meer nodig. Anders
   Kun je DBeaver hier installeren: https://dbeaver.io/
3. Git: Om van github het project af te halen kun je git gebruiken. Git kan hier dan ook gedownload worden: https://git-scm.com/download/win.
4. Python: Als je python nog niet geïnstalleerd hebt kun je dit via de volgende link doen: https://www.python.org/downloads/
   Weet je niet zeker of je python geïnstalleerd hebt kun je dat via de volgende command checken `python --version` of `py --version`
   **NOTE: wanneer je python installeert vergeet niet aan het begin de box add python.exe to PATH aan te vinken.**
5. Pip: Je hebt pip nodig voor het installeren van packages voor python. Je kan het volgende script downloaden: https://bootstrap.pypa.io/get-pip.py
   Dit script moet je dan met python uitvoeren via `python get-pip.py`

---