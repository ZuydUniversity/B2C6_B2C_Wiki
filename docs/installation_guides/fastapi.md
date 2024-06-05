---
title: Installation Guides - FastAPI
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">FastAPI</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Docker](docker.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Azure VM](azurevm.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---

# FastAPI {#fastapi}

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

In de homerouter.py worden de urls/routes aangemaakt voor de home. In tegenstelling tot de templaterouter is deze file statisch, deze is gemaakt voor de initiële homepagina/request. Deze is dus niet om aangepast te worden!

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

---