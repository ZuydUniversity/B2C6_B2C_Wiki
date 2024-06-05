---
title: Installation Guides - Dbeaver
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">DBeaver</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---

# DBeaver {#dbeaver}

## Inleiding

Voor het beheren van een MariaDB-database gebruiken we DBeaver als GUI-tool. Voordat we verbinding kunnen maken met de database, moet er een dockerized MariaDB-instance aanwezig zijn. Hoe je deze opzet, wordt behandeld in de gids "Docker".

## Stappen om verbinding te maken met de MariaDB Database

### 1. Zorg dat de database draait

Voordat je DBeaver opent, moet je ervoor zorgen dat je MariaDB-instance actief is:

- Lokaal: Als je Docker-instance lokaal draait, zorg ervoor dat deze actief is.
- Azure: Als je Docker-instance op Azure draait, zorg dan dat de Azure Ubuntu-server en de Docker-instance actief zijn.

### 2. Start DBeaver en Klik op "New Database Connection".

### 3. In het databasekeuzevenster, selecteer MariaDB.

### 4. Configureer de verbinding.

Vul de volgende verbindingsinstellingen in:

- Server Host:
  - Lokaal: Voer "localhost" in.
  - Azure: Voer het IP-adres in van de Ubuntu-server waarop de Docker-instance draait.
- Username: Voer de gebruikersnaam in die je hebt aangemaakt voor de MariaDB-database.
- Password: Voer het bijbehorende wachtwoord in.
- Port: Laat de waarde op 3306 staan, dit is de standaardpoort voor MariaDB.

### 5. Verbind met de database

Klik op "Test Connection" om te controleren of de instellingen correct zijn en DBeaver verbinding kan maken met de database. Als de test slaagt, klik je op "Finish" om de verbinding op te slaan en toegang te krijgen tot je MariaDB-database.

---