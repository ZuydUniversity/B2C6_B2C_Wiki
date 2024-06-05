---
title: Onderzoek - Database
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Database</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Infrastructuur](infra_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Code Monitor](code_monitor_onderzoek.md)</a>
</nav>

---

# Database onderzoek
## MariaDB
MariaDB is een open-source relationeel databasemanagementsysteem (RDBMS) dat is ontstaan als een afsplitsing (fork) van MySQL na de overname van MySQL door Oracle Corporation. Het doel van het ontwikkelen van MariaDB was om een vrij beschikbaar alternatief te bieden dat volledig compatibel is met MySQL, maar ook extra functies en prestatieverbeteringen bevat. MariaDB ondersteunt transacties en is ACID-compliant, wat staat voor Atomicity, Consistency, Isolation, en Durability, essentiële eigenschappen voor betrouwbare transactieverwerking. De database heeft een sterke gemeenschap van ontwikkelaars en gebruikers die actief bijdragen aan de continue ontwikkeling en ondersteuning van het platform.

### Voordelen van MariaDB
Open-source Flexibiliteit
MariaDB is volledig open-source, wat betekent dat het vrij gebruikt, aangepast en verspreid kan worden. Deze openheid maakt MariaDB bijzonder aantrekkelijk voor zowel individuele ontwikkelaars als grote organisaties, aangezien het geen licentiekosten met zich meebrengt en een grote mate van aanpasbaarheid biedt.

Compatibiliteit met MySQL
Een van de grootste voordelen van MariaDB is de hoge mate van compatibiliteit met MySQL. MariaDB is direct ontstaan als een afsplitsing van MySQL, waardoor bestaande MySQL-toepassingen en -gebruikers gemakkelijk kunnen overstappen zonder significante aanpassingen aan hun huidige systemen.

Actieve Gemeenschap en Ondersteuning
MariaDB wordt ondersteund door een actieve en groeiende gemeenschap van ontwikkelaars en gebruikers. Deze gemeenschap draagt voortdurend bij aan de verbetering van de software door nieuwe functies te ontwikkelen, bugs te verhelpen en ondersteuning te bieden. Dit netwerk van ondersteuning is een cruciale hulpbron voor zowel nieuwe als ervaren gebruikers.

Snelle Innovatie
Als een community-gedreven project zijn de ontwikkelingscycli van MariaDB vaak korter, waardoor nieuwe functies en verbeteringen snel worden doorgevoerd. Dit houdt het platform dynamisch en competitief binnen de snel evoluerende technologielandschap van databasemanagementsystemen.

### Nadelen van MariaDB
Minder Wijdverbreid dan MySQL
Hoewel MariaDB veel voordelen biedt, is het nog steeds niet zo bekend of wijdverbreid als MySQL. Dit kan resulteren in minder beschikbare bronnen, minder professionele ondersteuning en minder uitgebreide documentatie, wat een nadeel kan zijn voor organisaties die overwegen om naar MariaDB over te stappen.

Kleine Incompatibiliteiten
Ondanks de nauwe compatibiliteit met MySQL, kunnen er kleine verschillen tussen MariaDB en MySQL bestaan. Deze verschillen kunnen soms leiden tot incompatibiliteitsproblemen met specifieke toepassingen of tools die exclusief zijn ontworpen voor gebruik met MySQL.

Ondersteuning in Tools en Frameworks
Sommige ontwikkeltools, bibliotheken en frameworks bieden mogelijk betere of meer uitgebreide ondersteuning voor MySQL dan voor MariaDB. Dit kan een uitdaging vormen voor ontwikkelaars die specifieke functies of integraties nodig hebben, en kan resulteren in extra inspanningen om compatibele oplossingen te vinden of problemen op te lossen.

Bronnen
https://previder.nl/techblogs/wat-is-mariadb
https://www.purestorage.com/nl/knowledge/what-is-mariadb.html
https://kinsta.com/nl/blog/mariadb-vs-postgresql/
https://kinsta.com/nl/blog/mariadb-vs-mysql/
https://www.plesk.com/blog/various/mariadb-vs-mongodb-comparison/
https://www.astera.com/nl/type/blog/a-quick-overview-of-different-types-of-databases/


## MongoDB
Beschrijving 
MongoDB is een open-source NoSQL-database gebaseerd op een documentgeoriënteerd model, wat het geschikt maakt voor applicaties met ongestructureerde of snel veranderende gegevens. Dit houd in dat de Database van MongoDB niet relationeel is en alles in documents worden opgeslagen. (In SQL is dat een row.) 
MongoDB word door de industrie vaak gebruikt bij projecten waarbij grote aantallen data en "high performance" samen komen. Hierdoor kan er dus snel veel data in een database gezet worden. Naast dat MongoDB snel en veel aan kan is het ook instaat om makkelijk horizontaal te schalen. Iets wat bij een SQL DB lastiger gaat. Dit is omdat MongoDB dus geen gebruikt maakt van tabellen maar van collecties. Dit betekend dus dat dat soort taken van het schalen van de database op een geautomatiseerde manier kan verlopen. 

Kortom, MongoDB is een Database die snel veel data kan wegschrijven en geautomatiseerd kan up of down scalen.

### Voordelen
Snel veel data wegschrijven
MongoDB is uitzonderlijk efficiënt in het snel verwerken en wegschrijven van grote hoeveelheden data. Dit komt doordat MongoDB gebruikmaakt van een niet-relationele, documentgeoriënteerde database structuur die het mogelijk maakt om gegevens in een flexibeler formaat op te slaan dan traditionele relationele databases. Hierdoor kunnen data-operaties zoals invoegen, bijwerken en opzoeken sneller worden uitgevoerd omdat de structuur van de data minder rigide is en minder joins vereist.

Makkelijk te automatiseren
Automatisatie van databasetaken is eenvoudig met MongoDB, mede dankzij het rijke ecosysteem van tools en ondersteuning voor verschillende programmeertalen. Dit omvat drivers en bibliotheken voor populaire talen zoals Python, Java en Node.js, die het automatiseren van taken zoals datamigratie, back-upbeheer en monitoring vereenvoudigen.

Makkelijk horizontaal schaalbaar
Een van de krachtigste kenmerken van MongoDB is de eenvoud waarmee het horizontaal geschaald kan worden. Dit betekent dat je meer servers kunt toevoegen om de last te verdelen zonder significante wijzigingen aan de applicatiecode. MongoDB ondersteunt sharding, een methode om data over meerdere servers te verdelen, wat helpt om de lees- en schrijfcapaciteit van de database te verhogen naarmate de vraag groeit.

Werken met primary en secondary indexen op elk aangemaakt veld
MongoDB biedt flexibele indexatiemogelijkheden, waaronder de optie om primary en secondary indexen te creëren op elk veld binnen een document. Dit verbetert de prestaties van zoekopdrachten aanzienlijk, omdat gebruikers specifieke data snel kunnen vinden zonder de hele dataset te moeten doorzoeken. Indexen kunnen ook aangepast worden aan de specifieke querypatronen van een applicatie, wat de efficiëntie verder verhoogt.

Gebruikt een JavaScript manier van data opslaan
MongoDB gebruikt BSON (Binary JSON) voor het opslaan van data, een formaat dat nauw aansluit bij JSON, welke vaak gebruikt wordt in webtoepassingen en veelal bekend is bij ontwikkelaars die met JavaScript werken. Dit maakt MongoDB bijzonder toegankelijk voor ontwikkelaars, aangezien ze de structuur en syntaxis van de data opslag snel kunnen begrijpen en toepassen in hun projecten.

```json
{
   name: "sue",
   age: 26,
   blood_group: "A+",
   hobbys: ["Coderen", "Gamen"]
}
```

Door deze combinatie van snelle dataverwerking, eenvoudige automatisering, schaalbaarheid, geavanceerde indexering en een bekend datamodel, biedt MongoDB een krachtige en veelzijdige oplossing voor databeheer die goed past bij moderne, data-intensieve applicaties.

### Nadelen

Compatibiliteitsproblemen
MongoDB kan compatibiliteitsproblemen hebben met Django vanwege de relationele aard van Django's ORM (Object-Relational Mapping) systeem. Django is voornamelijk ontworpen om te werken met SQL-gebaseerde databases zoals PostgreSQL, MySQL, SQLite, etc. Voor FastAPI zijn er echter geen samengaande beperkingen die het gebruik van MongoDB verhinderen, dus FastAPI kan flexibel worden geïntegreerd met vrijwel elk type database, inclusief MongoDB, via asynchrone database drivers.

Beperkte ondersteuning voor complexe transacties
MongoDB ondersteunt complexe transacties minder uitgebreid dan traditionele relationele databases zoals MySQL of PostgreSQL. Hoewel er sinds versie 4.0 ondersteuning is voor multi-stap transacties, blijven deze beperkter vergeleken met de ACID-eigenschappen van relationele systemen. Dit kan een probleem vormen in toepassingen waar strikte data-integriteit, zoals in financiële systemen, essentieel is.

Geen ingebouwde procedures of triggers
MongoDB mist ook ingebouwde procedures en triggers, functies die in relationele databases automatisch bepaalde acties uitvoeren als reactie op bepaalde gebeurtenissen. Dit ontbreken betekent dat ontwikkelaars afhankelijk zijn van applicatielogica of externe tools voor soortgelijke functionaliteit, wat de complexiteit van de applicatiearchitectuur kan verhogen.

Deze beperkingen maken MongoDB minder geschikt voor toepassingen waar complexe transacties en strikte dataconsistente belangrijk zijn. De keuze voor MongoDB moet dus gebaseerd zijn op de specifieke vereisten en de context van het project.

#### **Bron**
* https://www.scholarhat.com/tutorial/mongodb/what-is-mongodb-and-why-to-use-it#:~:text=MongoDB%20can%20be%20used%20as,size%20without%20effecting%20our%20stack
* https://www.ovhcloud.com/nl/learn/what-is-mongodb/

## MySQL

MySQL is een van de meest populaire open-source relationele databasemanagementsystemen (RDBMS). Het wordt vaak gebruikt voor webtoepassingen en staat bekend om zijn snelheid, betrouwbaarheid en gebruiksgemak. Als een relationele database ondersteunt MySQL transacties en is het ACID-compliant, wat essentieel is voor applicaties waar data-integriteit van cruciaal belang is.

MySQL biedt brede ondersteuning in de ontwikkelgemeenschap, waardoor het een veelgebruikte keuze is voor zowel kleine als grote toepassingen. Het is bijzonder goed toepasbaar in situaties waar complexe query’s moeten worden uitgevoerd of waar de gegevens sterk genormaliseerd zijn. Dit maakt het een sterke keuze voor applicaties met veel leesbewerkingen.

Traditioneel is MySQL gekoppeld aan applicaties waarbij de gegevensstructuur relatief stabiel is en er regelmatig updates naar de database worden geschreven. Dit is een belangrijke onderscheiding tussen MySQL en niet-relationele databases zoals MongoDB, die beter geschikt zijn voor applicaties met ongestructureerde gegevens of gegevens die snel veranderen zonder dat dit leidt tot frequente en complexe updates van het gegevensmodel.

### Voordelen

Voordelen
Reliability
MySQL, een van de meest populaire open-source relationele databasemanagementsystemen, staat bekend om zijn veelzijdigheid, betrouwbaarheid en gebruiksgemak. Door de open-source aard heeft MySQL een sterke gemeenschap van ontwikkelaars die voortdurend bijdragen aan de verbetering en ondersteuning van het systeem. Deze gemeenschap voorziet in uitgebreide documentatie, tutorials, en forums die essentieel zijn voor zowel beginners als gevorderden.

Gegevensmodellering en Query Vermogen 
De gestructureerde manier waarop gegevens worden opgeslagen binnen MySQL, met duidelijk gedefinieerde relaties tussen tabellen, maakt het gemakkelijk om complexe gegevens te modelleren en te manipuleren. Dit wordt verder versterkt door SQL, een krachtige en gestandaardiseerde query-taal die het mogelijk maakt om complexe zoekopdrachten, analyses, en rapporten uit te voeren, waardoor gebruikers gemakkelijk gegevens kunnen extraheren en manipuleren.

Platformondersteuning en Schaalbaarheid 
MySQL onderscheidt zich ook door zijn brede platformondersteuning en flexibiliteit in verschillende ontwikkelomgevingen, aangezien het ondersteund wordt op Windows, Linux, en macOS. Dit, samen met de mogelijkheid om gemakkelijk te schalen van kleine tot grote systemen, maakt het geschikt voor zowel kleine webapplicaties als grote bedrijfstoepassingen.

Prestaties en Beveiliging 
De databank biedt geavanceerde optimalisaties voor het verwerken van grote hoeveelheden gegevens, inclusief indexen, caching en query-optimalisaties die zorgen voor snelle toegang tot gegevens. Daarnaast waarborgen functies voor transactiebeheer de databetrouwbaarheid, terwijl ingebouwde beveiligingsfuncties zoals gebruikersbeheer en toegangscontroles de veiligheid van de gegevens garanderen.


Geavanceerde Functies en Kostenbesparing
MySQL is niet alleen flexibel in de ondersteuning van verschillende datamodellen, waaronder relationele en niet-relationele datamodellen, maar biedt ook geavanceerde functies zoals replicatie, sharding, partitionering en clustering. Deze functies dragen bij aan de schaalbaarheid en bieden hoge beschikbaarheid, wat cruciaal is voor bedrijven die afhankelijk zijn van constante toegankelijkheid en efficiëntie.

Kosten
Tot slot, de lage kosten voor licenties van MySQL, vergeleken met sommige commerciële databases, maken het een aantrekkelijke optie voor veel organisaties. Dit economische voordeel, gecombineerd met de uitgebreide tooling en GUI's beschikbaar voor databasebeheer en -ontwikkeling, versterkt waarom MySQL een voorkeursoptie blijft in diverse toepassingsgebieden.

### Nadelen

Beperkte Opschaling voor Schrijfintensieve Workloads
MySQL kan uitdagingen ondervinden bij het opschalen van zeer schrijfintensieve workloads, vooral bij het gebruik van bepaalde opslagengines. Dit kan leiden tot verminderde prestaties bij hoge schrijfbelastingen, wat vooral merkbaar is in grote, transactionele systemen.

Beperkte Ondersteuning voor Complexe Query's
Voor complexe query's en geavanceerde data-analyses biedt MySQL mogelijk niet dezelfde mate van geavanceerde optimalisaties en functionaliteiten als sommige andere gespecialiseerde databases. Dit kan een beperking zijn voor toepassingen die diepgaande data-analyse vereisen.

Opslaglimieten
Afhankelijk van de configuratie en de gebruikte opslagengine kan MySQL beperkingen hebben wat betreft de grootte van individuele tabellen of de totale omvang van de database. Dit kan een probleem vormen voor zeer grote databases of data-intensieve toepassingen.

Beperkte Functionaliteit voor Geavanceerde Toepassingen
Voor specifieke geavanceerde toepassingen zoals full-text zoeken, geografische data-verwerking of bepaalde dataminingalgoritmen, kunnen andere databases of gespecialiseerde analytics-databases beter geschikt zijn dan MySQL.

Complexiteit van Configuratie
Het optimaliseren en afstemmen van MySQL voor maximale prestaties kan complex zijn en vereist diepgaande technische kennis van databasebeheer. Deze complexiteit kan een drempel vormen voor organisaties zonder gespecialiseerd IT-personeel.

Beperkingen in Monitoring en Beheertools
Hoewel er diverse tools beschikbaar zijn voor het beheer van MySQL, kunnen deze minder geavanceerd of robuust zijn in vergelijking met de beheertools die beschikbaar zijn voor sommige andere databaseplatforms. Dit kan het moeilijker maken om diepgaand inzicht te krijgen in de prestaties en gezondheid van de database.

## SQL vs NoSQL

### SQL
SQL-databases, zoals MySQL, gebruiken een relationeel model dat data structureert in tabellen met rijen en kolommen, waarbij elke rij een unieke sleutel heeft. Deze structuur maakt het gemakkelijker om complexe data te modelleren en te manipuleren met een krachtige en gestandaardiseerde query-taal. Dit maakt SQL-databases ideaal voor toepassingen die complexe zoekopdrachten en data-analyses vereisen. SQL-databases staan ook bekend om hun sterke ondersteuning door ontwikkelgemeenschappen, wat de ontwikkeling en probleemoplossing vergemakkelijkt. Echter, ze kunnen beperkingen hebben met betrekking tot schaalbaarheid, vooral in horizontale uitbreiding, vanwege de complexiteit van datareplicatie en consistentiebehoud. Bovendien kan het rigide schema van SQL-databases beperkend zijn voor applicaties die te maken hebben met ongestructureerde of snel veranderende data.


### NoSQL
NoSQL-databases, zoals MongoDB, bieden meer flexibiliteit door hun ondersteuning voor diverse datamodellen zoals documenten, grafieken, en sleutel-waardeparen. Deze databases zijn ontworpen om gemakkelijk horizontaal te schalen en zijn daarom goed geschikt voor applicaties die grote hoeveelheden data verwerken of waarbij de datastructuren frequent kunnen veranderen. NoSQL-databases maken snelle ontwikkeling mogelijk door minder strikte schema-vereisten, wat ontwikkelaars in staat stelt om gemakkelijker aanpassingen te maken zonder bestaande gegevens te beïnvloeden. Echter, de flexibiliteit van NoSQL kan leiden tot inconsistenties, afhankelijk van het gekozen consistentieniveau, wat een uitdaging kan vormen bij het waarborgen van data-integriteit.

### Voordelen van SQL Databases
Gebruiksgemak
SQL-databases zijn vanwege hun gestructureerde opzet eenvoudig te gebruiken. Zelfs mensen zonder voorgaande ervaring kunnen na een korte training efficiënt met deze databases werken.

Gestructureerde Dataopslag
SQL-databases bieden een georganiseerde structuur voor het opslaan van gegevens met duidelijk gedefinieerde relaties tussen de tabellen. Dit faciliteert het modelleren en manipuleren van complexe gegevenssets, wat cruciaal is voor veel zakelijke toepassingen.

Krachtige Querytaal
De gestandaardiseerde querytaal van SQL maakt het mogelijk om complexe zoekopdrachten, analyses en rapportages uit te voeren, waardoor gebruikers gemakkelijk en efficiënt gegevens kunnen extraheren en manipuleren.

Sterke Ontwikkelaarsgemeenschap
Een robuuste gemeenschap van ontwikkelaars ondersteunt SQL-databases, waardoor bedrijven en individuele gebruikers toegang hebben tot een rijke bron van hulpbronnen en ondersteuning.

Nadelen van SQL Databases
Beperkte Schaalbaarheid
Traditionele SQL-databases kunnen problemen ondervinden bij het schalen naar grote datavolumes, vooral wanneer dit horizontale schaalbaarheid vereist, zoals het toevoegen van meer servers om de belasting te verdelen. Dit komt door de complexiteit van datareplicatie en het behoud van consistentie.

Rigide Schema's
Het relationele model van SQL-databases vereist een vaste, vooraf gedefinieerde structuur, wat beperkingen kan opleggen aan toepassingen die te maken hebben met variabele of ongestructureerde gegevens. Aanpassingen in het schema kunnen moeilijk zijn zonder bestaande gegevens te beïnvloeden.

### Voordelen van NoSQL
Flexibiliteit in Ontwikkeling
NoSQL-databases staan bekend om hun flexibiliteit, wat ontwikkelaars helpt bij het omgaan met ongeplande situaties en de ontwikkeling van applicaties versnelt.

Aanpasbaarheid van Schema's en Queries
NoSQL biedt ontwikkelaars de vrijheid om schema's en queries snel aan te passen aan veranderende gegevensvereisten, wat een voordeel is bij het doorvoeren van verbeteringen zonder de noodzaak van een vooraf ontworpen schema.

Horizontale Schaalbaarheid
NoSQL-databases kunnen gemakkelijk horizontaal schalen door extra servers toe te voegen, wat helpt om grotere datavolumes te verwerken zonder de noodzaak voor kostbare upgrades.

Nadelen van NoSQL
Variabele Consistentieniveaus
NoSQL-databases bieden verschillende niveaus van dataconsistentie, van sterke tot eventuele consistentie. Het kiezen van het juiste niveau kan uitdagend zijn en vereist zorgvuldige overweging van de applicatievereisten.

Uitdagingen in Cloud Migratie
Hoewel NoSQL goed past bij cloud computing, kan het migreren van bestaande workloads naar de cloud complex zijn. Dit proces vereist overweging van factoren zoals gegevensmodellen, consistentieniveaus en de geografische locatie van datacenters.

### Bronnen:
* https://appmaster.io/nl/blog/sql-vs-nosql-databases-nl
* https://azure.microsoft.com/nl-nl/resources/cloud-computing-dictionary/what-is-nosql-database
* https://www.almabetter.com/bytes/articles/advantages-and-disadvantages-of-sql


## Conclusie

Gezien de behoefte van ons project om gebruik te maken van FastAPI en de inzet van Docker voor deployment, is MariaDB de meest geschikte keuze als database-oplossing. Hier zijn enkele cruciale redenen die deze keuze ondersteunen:

Uitstekende Compatibiliteit met Moderne Web Frameworks
MariaDB's uitstekende compatibiliteit met MySQL zorgt ervoor dat het naadloos kan werken met hedendaagse web frameworks zoals FastAPI. Dit is essentieel, aangezien FastAPI is ontworpen om te opereren met SQL databases via ORMs zoals SQLAlchemy die perfect samenwerken met MariaDB. Dit stelt ontwikkelaars in staat om de krachtige en moderne functies van FastAPI volledig te benutten zonder zorgen over database compatibiliteit.

Robuuste Ondersteuning voor Docker
MariaDB biedt robuuste ondersteuning voor Docker, wat het beheer van containers waarin de database draait vereenvoudigt. Met Docker kunnen MariaDB instances gemakkelijk worden opgezet en geschaald, wat perfect aansluit bij de dynamische en container-georiënteerde architectuur die wordt gebruikt in moderne software-ontwikkelingsomgevingen. Deze naadloze integratie vermindert de complexiteit en verbetert de betrouwbaarheid van het hele systeem.

Actieve Gemeenschap en Open-source Voordelen
MariaDB, met zijn sterke gemeenschap en open-source model, biedt toegang tot uitgebreide bronnen en gemeenschapsondersteuning die van cruciaal belang zijn tijdens ontwikkeling en productie. Deze ondersteuning is vooral waardevol in snel evoluerende projecten waar snelle toegang tot hulp en nieuwe updates essentieel zijn. Bovendien stellen de open-source licentievoorwaarden van MariaDB teams in staat om de database aan te passen aan hun specifieke behoeften zonder extra kosten.

Geavanceerde Functies en Prestatieverbeteringen
De voortdurende ontwikkeling en verbetering van MariaDB door de gemeenschap zorgen ervoor dat het systeem niet alleen compatibel blijft met MySQL, maar ook nieuwe geavanceerde functies en prestatieverbeteringen biedt. Deze innovaties zijn van groot belang om te voldoen aan de eisen van hedendaagse applicaties, die vaak om hoge prestaties en uitgebreide functionaliteiten vragen.

In conclusie, MariaDB is de beste keuze voor ons project gezien zijn naadloze integratie met FastAPI en Docker, zijn krachtige gemeenschapsondersteuning, en de continue innovaties die het biedt. Deze factoren maken MariaDB niet alleen een technisch haalbare maar ook een toekomstbestendige optie voor onze databasebehoeften.


---