---
title: Installation Guides - Docker
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Docker</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---

# Docker {#docker}

### Docker with FastAPI

1. Download docker desktop -> https://docs.docker.com/desktop/install/windows-install/
2. Install Docker extension for VScode -> Extension ID: ms-azuretools.vscode-docker
3. Search for vscode commands (ctrl + shift + p) for "Docker: add docker files to workspace" and walk thru the wizzard

Je hebt nu een docker file aangemaakt in je project. Nu moet het nog een docker image worden en vervolgens een container.

Hiervoor moet je in de cli naar de project file gaan van het project waar je de dockerfile voor hebt aangemaakt.
Vervolgens gebruik je het volgende command: `docker build -t nameofdockerimage .`. Dit command gaat een docker image aanmaken van het project.
Deze image kan je vervolgens laten draaien als een container doormiddel van de docker desktop applicatie die docker lokaal regelt.
Dit kan je ook in de cli doen door het volgende command: `docker run -d --name nameofdockercontainer -p hostport:givendockerport nameofdockerimage` In dit command geldt het volgende:

- nameofdockercontainer = de naam die je aan de docker container wilt geven
- hostport = de poort die jij gebruikt om vanuit localhost de site te bezoeken
- givendockerport = de poort die jij hebt aangegeven bij het maken van een dockerfile
- nameofdockerimage = de naam van de docker image waarvan jij de container wilt laten draaien

Nu dat de container draait kan je doormiddel van de hostport de site bezoeken.

### Docker Compose

Maak eerst een root directory waar je Docker file(s) in komen te staan.
Maak in deze map een Docker compose file aan. Dit is een .yml file. Met deze docker compose file zet je tegelijkertijd meerdere services op om je applicatie te laten werken (Front-end, back-end etc.)

```yml
# docker-compose.yml
version: "3.1" # Specificeert de versie van Docker Compose
name: voorbeeld # Naam van de Docker Compose configuratie
services: # Definieert de services die deel uitmaken van de applicatie
  frontend: # Naam van de eerste service
    build: /frontend/. # Pad naar de Dockerfile voor het bouwen van de image voor deze service
    restart: always # Beleid voor het opnieuw starten van de service als deze stopt
    ports: # Poorten die worden geopend naar de buitenwereld
      - 80:80 # Poortmapping: hostpoort:containerpoort
    extra_hosts: # Extra hosts die aan de /etc/hosts van de container worden toegevoegd
      - "backend:host.docker.internal" # Hostnaam:IP adres

  backend: # Naam van de tweede service
    build: /backend/. # Pad naar de Dockerfile voor het bouwen van de image voor deze service
    restart: always # Beleid voor het opnieuw starten van de service als deze stopt
    ports:
      - 8080:8080 # Poortmapping: hostpoort:containerpoort
    links: # Verbindingen met andere services
      - db # Verbindt de backend service met de db service
    environment: # Omgevingsvariabelen voor de service
      DB_USER: root # Gebruikersnaam voor de database
      DB_PASSWORD_FILE: /run/secrets/db_password # Pad naar het bestand met het wachtwoord voor de database
      DB_HOST: db # Hostnaam van de database
      DB_NAME: mama # Naam van de database
    secrets: # Geheimen die aan de service worden doorgegeven
      - db_password # Naam van het geheim

  db:
    image: mariadb:latest # De image die voor deze service wordt gebruikt, dit kan vanaf Docker hub of een Azure registry komen
    restart: always # Beleid voor het opnieuw starten van de service als deze stopt
    environment:
      MYSQL_ROOT_PASSWORD_FILE: /run/secrets/db_password # Dit is de locatie van de secret file binnen de container
    volumes:
      - db_data:/var/lib/mysql # Dit is de data folder van de database binnen de db container
    secrets:
      - db_password
    # Deze port is voor communicatie BUITEN het docker netwerk
    # Haal je deze weg kan alleen het backend verbinding maken met de database
    # Externe tools zoals DBeaver werken dan niet meer
    ports:
      - 3306:3306

# Dit is de door Docker aanbevolen manier om gevoelige data mee te geven aan containers
secrets:
  db_password:
    file: ./secrets/db_password.txt # pad naar de secret file in je project

volumes:
  # Dit volume wordt door Docker ergens op je systeem gezet
  # Docker beheert de plek ervan voor je
  # Het enige wat je zelf nodig hebt is de naam ervan
  db_data:
```

Dit is een voorbeeld van een Docker compose file. Hier kan je services in definiëren zoals Front-end. Voor deze services kun je verschillende opties meegeven. Door deze opties mee te geven zorg je dat de service goed kan draaien in een Docker container. Met het commando `docker-compose up` start je deze service.

---