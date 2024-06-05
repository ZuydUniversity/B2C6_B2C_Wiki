---
Titel: iteratie_3
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 1](iteratie_1.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 2](iteratie_2.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Iteratie 3</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 4](iteratie_4.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 5](iteratie_5.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 6](iteratie_6.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 7](iteratie_7.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 8](iteratie_8.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Iteratie 9](iteratie_9.md)</a>
</nav>

---

# Iteratie 3

### Database
#### **MySQL**
-	Nadeel: Draait als Azure service  we willen geen vendor lockin
-	Voordeel: Support mogelijk

#### **MariaDB**
-	Voordeel: Community
-	Voordeel: Documentatie
-	Voordeel: Open-source
-	Voordeel: Performance enhancements 
-	Voordeel: Meer functies 

#### **MongoDB**
-	Nadeel: Geen relaties
-	Nadeel: Niet compatibel

### Backend 
#### **Django**
-	Voordeel: Rapid development
-	Voordeel: Meer out of the box
-	Nadeel: Backend + frontend 
-	Test mogelijkheden zijn aanwezig 
-	‘Nadeel’: gebruikt WSGI 
-	Voordeel: Strikter, waardoor iedereen meer op dezelfde manier codeert 
-	Voordeel: standaard ORM 

#### **FastAPI**
-	Voordeel: Rapid development 
-	Voordeel: Minder file generation
-	Alleen backend
-	Testen integreren in code (unit testen) 
-	Voordeel: gebruikt ASGI
-	Authenticatie aanwezig 
-	Nieuwer framework
-	Async 

### Frontend
#### **Javascript**
-	Nadeel: fouten zie je bij runtime

#### **Typescript**
-	Voordeel: type safety 
-	Voordeel: fouten zie je bij compile 
-	Makkelijker debuggen 
-	OOP 

Keuze: Typescript 


### **Deployment**

VM(Ubuntu) of Docker?


# Keuzes
- Frontend: Typescript
- Backend: FastAPI
- Database: MariaDb
- Deployment: Docker compose

---