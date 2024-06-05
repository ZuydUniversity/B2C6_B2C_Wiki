---
title: Onderzoek - Backend
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Backend</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Database](database_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Infrastructuur](infra_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Code Monitor](code_monitor_onderzoek.md)</a>
</nav>

---

# Backend onderzoek

## Hoofdstuk 1 Wat is FastAPI
FastAPI is een modern Python-webframework dat is opgericht door Sebastián Ramírez in 2018. Het is ontworpen om snellere API's te ontwikkelen met minimale code en maximale snelheid. Het onderscheidt zich door zijn focus op backend-specialisatie, wat betekent dat het zich voornamelijk richt op het bouwen van de logica en functionaliteit van de serverkant van een applicatie. Dit stelt ontwikkelaars in staat om snel en efficiënt RESTful API's te maken zonder afbreuk te doen aan prestaties of schaalbaarheid. Met zijn krachtige type-annotaties en automatische documentatiegeneratie maakt FastAPI het ontwikkelen van API's in Python niet alleen snel, maar ook veilig en gemakkelijk te onderhouden. (FastAPI, sd).

## Hoe is FastAPI opgebouwd?
Hieronder staat de file structuur weergegeven van een FastAPI project.
Dit project is nu nog relatief klein, maar wel al ingericht om heel snel uitgebreid te worden.  
Na deze filetree volgt een uitleg van elke file en alle namen zijn klikbaar om zo direct naar de daadwerkelijke bestanden toe te navigeren.

### Structuur

* [app/](https://github.com/ZuydUniversity/B2C6_B2C_Backend/tree/245aeafe66e82a23123dac21ab0d318a3a96e994/app)
  * [routers/](https://github.com/ZuydUniversity/B2C6_B2C_Backend/tree/245aeafe66e82a23123dac21ab0d318a3a96e994/app/routers)
    * [items.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/routers/items.py)
    * [__init__.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/routers/__init__.py)
  * [tests/](https://github.com/ZuydUniversity/B2C6_B2C_Backend/tree/245aeafe66e82a23123dac21ab0d318a3a96e994/app/tests)
    * [test_main.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/tests/test_main.py)
    * [__init__.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/tests/__init__.py)
  * [main.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/main.py)
  * [__init__.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/__init__.py)
* [requirements.txt](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/requirements.txt)

### Uitleg
#### init.py
Deze files bevinden zich in mappen, hierdoor kan je zorgen dat Python deze mappen kan herkennen in bijvoorbeeld `from .routers import items`.

#### app/
Deze folder bevat al je project bestanden.

#### routers/
In deze folder kan je zogenaamde `APIRouter` definiëren.
Door deze `APIRouter`s te gebruiken kan je snel over meerdere endpoints instellingen aanpassen.

#### items.py
In dit bestand staat de `APIRouter` voor alle `/items/*` endpoints.

```python
router = APIRouter(prefix="/items", tags=["items"],responses={404: {"description": "Not found"}})

@router.get("/{item_id}")
async def read_item(item_id: str):
    if item_id not in fake_db:
        return {"message": "Item not found"}
    return fake_db[item_id]
```

Hierboven is een voorbeeld te zien van een `APIRouter`. Hierin kan je zeggen dat voor elke eindpoint die je maakt met elke `@router.get()` binnen dit bestand, er al een bepaalde prefix geldt.  
Hierdoor hoef je jezelf niet te herhalen dus krijg je in plaats van deze herhalende code:

```python
@router.get("/items/")
async def iets()

@router.post("/items/")
async def iets2()

@router.get("/items/{item_id}")
async def iets3()

@router.post("/items/{item_id}")
async def iets4()
```

deze overzichtelijke code:

```python
@router.get("/")
async def iets()

@router.post("/")
async def iets2()

@router.get("/{item_id}")
async def iets3()

@router.post("/{item_id}")
async def iets4()
```

Ook kan je makkelijk standaard gedrag definiëren door de `responses` mee te geven in de constructor.

#### tests/
In deze folder staan de automatische tests die je FastAPI op zichzelf kan laten doen.

#### test_main.py
In dit testbestand worden de functies uit [main.py](https://github.com/ZuydUniversity/B2C6_B2C_Backend/blob/245aeafe66e82a23123dac21ab0d318a3a96e994/app/main.py) getest.  
Normaal gezien test je hierin alle endpoints, maar voor het voorbeeld heb ik 1 uitgewerkt.

```python
from fastapi.testclient import TestClient
from app.main  import app

client = TestClient(app)

def test_root():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {"Hello": "World"}
```

FastAPI heeft een eigen `TestClient` waarin je de bestaande `app` ingeeft.

Voor elke test roep je eerst het gewenste endpoint aan en vervolgens ga je de reactie `asserten`.

Hiermee geef je al van tevoren aan exact welke reactie de API moet geven. Tijdens deze `assert` vergelijkt de computer de daadwerkelijke reactie met de bedoelde reactie en indien dit hetzelfde is zal de test succesful doorloopt worden. Indien dit niet gebeurt zullen de testen falen en dit krijg je terug te zien.

#### main.py
```python
from fastapi import FastAPI
from .routers import items

app = FastAPI()

app.include_router(items.router)

@app.get("/")
async def read_root():
    return {"Hello": "World"}
```

Hierin maak je de app aan. Dankzij de routers hoef je alleen een `app` aan te maken en de routers stuk voor stuk mee te geven met `app.include_router(items.router)`.  
Hiermee zou de app al werken, maar voor de sier heb ik nog het root endpoint gemaakt.

#### requirements.txt
Hierin staat alles wat Python nodig heeft om FastAPI te kunnen runnen.

## Voor- en nadelen
|  |  |

| ----------- | ----------- |
| **Voordelen** | **Nadelen** |
| Ingebouwde dynamische documentatie van je eigen endpoints met extra testomgeving. | Het framework is relatief nieuw waardoor community support mogelijk minder is. |
| Lage complexiteit door minimale hoeveelheid bestanden. | Voor mensen zonder ervaring met asynchrone code kan het ingewikkelder zijn. (Persoonlijke mening van Cas: ik denk dat we hoe dan ook de API asynchroon zullen moeten maken dus dit is een klein minpunt) |
| [Uitgebreide documentatie](https://fastapi.tiangolo.com/) |  |
| [Hoge performance](https://fastapi.tiangolo.com/#performance) |  |
| Makkelijk te leren, veel wordt voor je gedaan |  |
| Centrale error handling is mogelijk op dezelfde manier als de `APIRouter` |  |

## BRONNEN:
1. https://fastapi.tiangolo.com/
2. https://www.stxnext.com/blog/fastapi-vs-flask-comparison/

---