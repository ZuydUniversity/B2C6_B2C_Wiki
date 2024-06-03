# Prerequisites
### Installatie
Om de backend die aanwezig is op de github te gebruiken moeten eerst enkele dingen geïnstalleerd worden.
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

***

# Introductie
Op deze pagina komen allerlei guides die aangeven hoe iets geïnstalleerd of opgezet moet worden.

***

# ReactTS
Hieronder zul je vinden hoe je een React app aanmaakt voor Typescript

Benodigdheden:
* Je moet node.js gedownload hebben voor het lokaal draaien van de React app: [Download Node.js](https://nodejs.org/en/download)

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

***
# MariaDB

***

# FastAPI
## Installaties
Om een fastapi project te kunnen maken en te kunnen draaien moet je een aantal dingen installeren. De installaties zijn allemaal pip installs die in de cmd moeten worden uitgevoerd.
1. pip install fastapi
2. pip install uvicorn
3. pip install gunicorn
4. pip install requests
5. pip install pytest

Als alle installs gedaan zijn kan je een fastapi project draaien.

## Project aanmaken
### Filestructuur
In tegenstelling tot ReactTS is er niet een command dat een FastAPI project voor je aanmaakt. Het is dus belangrijk dat je zelf zorgt dat alle benodigde files aangemaakt worden met de juiste filestructuur.
De standaard opzet van een project is als volgt:
```
my-fastapi-project/
|-- backend/
|   |-- unittest/
|   |   |-- __init__.py
|   |   |-- helloworldtest.py
|   |   |-- starttests.py
|   |-- models/
|   |   |-- __init__.py
|   |   |-- templatemodel.py
|   |-- routers/
|   |   |-- __init__.py
|   |   |-- templaterouter.py
|   |   |-- homerouter.py
|   |-- database.py
|   |-- main.py
|-- .gitignore
|-- README.md
```
### Main.py file
De main.py is de start file van het project, zoals de naam al zegt -> de main.
```py
from fastapi import FastAPI # imports the fastapi package
from fastapi.middleware.cors import CORSMiddleware

from .Routers import HomeRouter, TemplateRouter # imports the routes of the different models

routers = [HomeRouter, TemplateRouter] # adds the routes to a list

app = FastAPI() # creates the API

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# Adds all the routers from the list to the API
for i in routers:
    app.include_router(i.router)

app.debug = True
```
Bovenstaand is een algemene opzet van een main.py, dit verschilt natuurlijk per project.

### Database.py file
Deze file bezit alle basis informatie van de database die aan de FastAPI gekoppeld wordt. Momenteel blijft hij leeg aangezien wij momenteel nog geen Database connectie erbij plaatsen.

### routers folder
De routes om alle http requests te doen voor een get, post of delete worden in deze folder behandeld. Er is gekozen om elke model een aparte route file te geven om zo makkelijk overzicht te houden tussen de models en hun routes.

De routers folder bezit 3 files:
1. `__init__.py`
2. templaterouter.py
3. homerouter.py

De `__init__.py` file is aanwezig aangezien dit erg handig is met een mappenstructuur die gebruik maakt van imports, deze file geeft namelijk aan dat directories/folders als een python package gebruikt kunnen worden. Deze kan je leeglaten.

De templaterouter.py is de file waar alle urls/routes aangemaakt en behandeld worden voor de template model:
```py
from fastapi import APIRouter

## Make sure to import your model, otherwise you will get an error that your model is not found.
from ..models.templatemodel import TemplateModel

## Prefix is to make the path, make sure API is always at the beginning of this.
## The responses are premade for you to use. I recommend to don't toutch when you don't know what you are doing.
router = APIRouter(prefix="/api/template", tags=["template"],responses={404: {"description": "Not found"}, 200: {"description": "OK"}, 400: {"description": "Bad Request"}, 500: {"description": "Internal Server Error"}})


## Basic get request.
@router.get("/")
async def get_template():
    models = {1, "Homoerectus", "USA"}
    return models
```

In de homerouter.py  worden de urls/routes aangemaakt voor de home. In tegenstelling tot de templaterouter is deze file statisch, deze is gemaakt voor de initiële homepagina/request. Deze is dus niet om aangepast te worden!
```py
from fastapi import APIRouter

## DONT TOUTCH
router = APIRouter(prefix="/api", tags=["API"],responses={404: {"description": "Not found"}, 200: {"description": "OK"}, 400: {"description": "Bad Request"}, 500: {"description": "Internal Server Error"}})

## DONT TOUTCH
@router.get("/")
async def homeurl():
    return { True : "API is working!"}
```

### De models folder
In de models folder komen, naast de `__init__.py`, alle modellen voor de 'objecten' die gebruikt worden in de database en de frontend.
De folder bezit de volgende bestanden:
1. `__init__.py`
2. templatemodel.py

Zoals eerder besproken is de `__init__.py` aanwezig aangezien dit erg handig is met een mappenstructuur die gebruik maakt van imports, deze file geeft namelijk aan dat directories/folders als een python package gebruikt kunnen worden. Deze kan je leeglaten.

templatemodel.py bezit het model van het template object. 
```py
## Template model, this is just an basic model 
class TemplateModel():
    def __init__(self, id, name, address):
        self.id = id
        self.name = name
        self.address = address
    
    def getmodel(self):
        return {self.id, self.name, self.address}
```

### De unittest folder
Deze folder bezit, naast een `__init__.py`, de python files voor het runnen van testen.
De files zijn:
1. `__init__.py`
2. starttests.py
3. helloworldtest.py


De starttest.py file is de file die gerund wordt indien de testen doorlopen moeten worden. Deze file zorgt dat alle files voor de testen worden doorlopen. Deze file mag je **NIET** aanpassen!
```py
#########################################################################
#########################################################################
#### THIS FILE HAS TO RUN IN A CMD PROMPT OTHERWISE IT WILL NOT WORK ####
#########################################################################
#########################################################################
import pytest
import os

## DONT TOUTCH
## This junk here is to get the path for all of the tests so that you guys don't have to manualy add them every time we run the tests.
path = str(os.getcwd())
tests = os.listdir(path)
remove = []
for i in tests:
    if i.title() == 'Starttests.Py' or i.title() == '__Pycache__' or i.title() == '.Pytest_Cache':
        remove.append(i)
for i in remove:
    tests.remove(i)

## DONT TOUTCH
## This code runs all the tests that are in de UnitTest folder.
def run_tests():
    for i in tests:
        test = str(path + "\\" + i)
        if pytest.main([test]) == 1:
            print(f"{i.title()} Tests failed.")
        else:
            print(f"{i.title()} Tests passed.")

if __name__ == '__main__':
    run_tests()
    print("Ran tests for ", tests)
```

De helloworldtest.py is een file waar testen worden doorlopen, voor nu is dit dus alleen het testen of de API online staat.
```py
import requests as rq

## This is a basic test to make sure the API is working.
def test_read_item():
    response = rq.get("http://127.0.0.1:8000/api/") ## Makes the request to the API url.
    assert response.status_code == 200 ## Checks if the status code is 200.
    assert response.json() == {"true": "API is working!"} ## Checks if the reponse from the url is correct.

## A test should go outside our API and go back via the internet to check if it works.
## Then with multiple checks and verifications you can make sure your api request or methode is working.
```

***

# Docker

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

***
### Docker Compose

Maak eerst een root directory waar je Docker file(s) in komen te staan. 
Maak in deze map een Docker compose file aan. Dit is een .yml file. Met deze docker compose file zet je tegelijkertijd meerdere services op om je applicatie te laten werken (Front-end, back-end etc.)

```yml 
# docker-compose.yml
version: '3.1' # Specificeert de versie van Docker Compose
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
    file: ./secrets/db_password.txt  # pad naar de secret file in je project

volumes:
  # Dit volume wordt door Docker ergens op je systeem gezet
  # Docker beheert de plek ervan voor je
  # Het enige wat je zelf nodig hebt is de naam ervan
  db_data:
```

Dit is een voorbeeld van een Docker compose file. Hier kan je services in definiëren zoals Front-end. Voor deze services kun je verschillende opties meegeven. Door deze opties mee te geven zorg je dat de service goed kan draaien in een Docker container. Met het commando `docker-compose up` start je deze service.
# DBeaver

## Inleiding
Voor het beheren van een MariaDB-database gebruiken we DBeaver als GUI-tool. Voordat we verbinding kunnen maken met de database, moet er een dockerized MariaDB-instance aanwezig zijn. Hoe je deze opzet, wordt behandeld in de gids "Docker".

## Stappen om verbinding te maken met de MariaDB Database
### 1. Zorg dat de database draait
 Voordat je DBeaver opent, moet je ervoor zorgen dat je MariaDB-instance actief is:
* Lokaal: Als je Docker-instance lokaal draait, zorg ervoor dat deze actief is.
* Azure: Als je Docker-instance op Azure draait, zorg dan dat de Azure Ubuntu-server en de Docker-instance actief zijn.
### 2. Start DBeaver en Klik op "New Database Connection".
### 3. In het databasekeuzevenster, selecteer MariaDB.
### 4. Configureer de verbinding.
Vul de volgende verbindingsinstellingen in:
   * Server Host:
       * Lokaal: Voer "localhost" in.
       * Azure: Voer het IP-adres in van de Ubuntu-server waarop de Docker-instance draait.
   * Username: Voer de gebruikersnaam in die je hebt aangemaakt voor de MariaDB-database.
   * Password: Voer het bijbehorende wachtwoord in.
   * Port: Laat de waarde op 3306 staan, dit is de standaardpoort voor MariaDB.
### 5. Verbind met de database
Klik op "Test Connection" om te controleren of de instellingen correct zijn en DBeaver verbinding kan maken met de database. Als de test slaagt, klik je op "Finish" om de verbinding op te slaan en toegang te krijgen tot je MariaDB-database.


***
# Azure Virtual Machines
## Aanmaken Virtual Machine

Als je navigeert naar Azure, kijk eerst als je in de juiste map zit. De map waar je in moet zitten heet ZKOO. Als je hier niet in zit, klik rechtsboven in het scherm op je username, en dan op "**Schakelen tussen mappen**". Dan zie je Hogeschool Zuyd en ZKOO. Als je ZKOO niet hebt, dan moet je nog de invite e-mail accepteren dat je hebt gekregen op je school e-mail. 

Eenmaal op de ZKOO, klik op de Resource Group knop en ga naar B2C6C. Dan open je de Azure CLI. Deze knop bevindt zich bovenaan in de blauwe balk. Klik op het terminal-icoontje (links van de notification bel) om de CLI open te maken. Je kunt kiezen tussen Powershell en Bash, ik heb Bash gebruikt want alle Microsoft guides doen dat ook als standaard gebruiken.

Om te beginnen moet je inloggen met de credentials die we gekregen hebben in Slack. Copy/Paste deze login commando. **REMINDER!** Copy/Pasting is een beetje anders. Je moet ctrl+shift+c/ctrl+shift+v gebruiken in de terminal.

**Het login commando staat gepint in het b2c6devops-b2c kanaal op Slack**

https://b2c6devops2023bp4.slack.com/archives/C0720SZMF7X/p1716892218018419?thread_ts=1716277065.656229&cid=C0720SZMF7X


Als je nu een VM wilt aanmaken dan gebruik je dit commando:

``az vm create --resource-group B2C6C --name [vm naam] --image Canonical:0001-com-ubuntu-minimal-jammy:minimal-22_04-lts-gen2:latest --admin-username b2c6c --assign-identity --generate-ssh-keys --public-ip-sku Standard --location westeurope --size Standard_B1s --storage-sku Standard_LRS --nic-delete-option delete --os-disk-delete-option delete ``

Na een tijdje krijg je een melding met wat informatie erin. Als je nu de pagina van de resource group refresht dan zie je je nieuwe VM en alle bijbehorende dingen.


## Verwijderen van de VM en bijbehorende items.

Als je de VM wilt verwijderen voor wat voor reden dan ook, dan voer je deze commando's uit. Ze zijn ongeveer hetzelfde op het bestandsnaam en type bestand na.

Verwijderen van de VM: ``az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Compute/virtualMachines" --verbose``

Verwijderen van het Network Interface: ``az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/networkInterfaces" --verbose``

Verwijderen van de Network Security Group: ``az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/networkSecurityGroups" --verbose``

Verwijderen van het Public IP: ``az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/publicIPAddresses" --verbose``

Verwijderen van het Virtual Network: ``az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/virtualNetworks" --verbose``


## Inloggen naar de VM via Termius

1. Installeer Termius via de website: https://www.termius.com/free-ssh-client-for-windows

2. Eenmaal in Termius, voeg een nieuwe host toe.

3. Vul het IP-adres in van de VM. Die vind je op als je op de VM klikt waar je mee wilt verbinden, en dan klikt op "Verbinden"

4. Log in met het Admin Username wat je hebt gebruikt bij het aanmaken van de VM. (Standaard b2c6c van maken?)

5. Voeg een Key toe. Geef de key een naam. Hier moet je de private key invullen. Deze kan je vinden in Azure als je ingelogt bent. **Dus niet in je VM maar op de Azure pagina!**. Voer na het inloggen op de CLI. 

6. In de CLI, bekijk de .ssh folder door ``ls -l ~/.ssh`` uit te voeren. Dan kijk je naar wat de filename is van de key zonder **.pub**.

7. Voer nu het volgende commando uit; ``cat ~/.ssh/[keynaam]``. Je krijgt een muur van tekens, kopieer deze (inclusief de ---begin--- en ---end--- deel van de key)

8. Voer deze private key in bij de Key optie in Termius.

9. Probeer verbinding te maken met de VM. Als alles goed is gegaan heb je nu verbinding met de VM en zit je in de main directory!


## Docker installeren
We gaan docker insalleren met behulp van apt.

1. Log in je VM en voer als eerste een apt update uit met ``sudo apt-get update``.

2. Als de update klaar is dan typ je ``sudo apt-get install ca-certificates curl``. Hiermee krijgen we curl certificaten. Curl gebruik je om gegevens over te brengen via URL's

**Linux is heel leuk en geeft soms geen output of feedback als iets werkt. Als je niks terug krijgt kan je er van uit gaan dat het succesvol is uitgevoerd**

3. Nu maak je een nieuwe directory aan waar je de docker files in gaat installeren. Dit doe je met ``sudo install -m 0755 -d /etc/apt/keyrings``. Voor wie het interesseert, de **-m 0775** zorgt ervoor dat de directory een "Read & Execute permission heeft" voor iedereen en een "Write permission" voor de eigenaar.

4. Als je wilt controleren als alles goed is gelukt, dan voer je dit commando uit: ``ls -ld /etc/apt/keyrings``. Als je een output krijgt wat lijkt op dit: ``drwxr-xr-x 2 root root 4096 May 30 12:34 /etc/apt/keyrings`` dan is alles goed.

5. Nu gaan we een docker bestand downloaden van de website met het volgende commando: ``sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc``

6. Als laatste voeren de nog dit commando uit: ``sudo chmod a+r /etc/apt/keyrings/docker.asc``

7. Voer dit commando uit (alles tegelijk in de terminal gooien): 

  ``echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null``

8. eindig nu met een ``sudo apt-get update``

9. Nu gaan we meest recente docker versie installeren met dit: ``sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin``

10. Het kan zijn dat je moet kiezen tussen libraries, maar als je hier niet veel van weet tik je maar 15 in om het over te slaan.

11. Om te kijken als het is gelukt, voeren we dit commando uit: ``sudo docker run hello-world`` Hiermee haalt die de hello-world image uit de Docker Hub.

# Installatie Linter
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
