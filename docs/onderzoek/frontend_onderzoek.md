---
title: Onderzoek - Frontend
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Frontend</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Backend](backend_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Database](database_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Infrastructuur](infra_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Code Monitor](code_monitor_onderzoek.md)</a>
</nav>

---

# Frontend onderzoek
## Javascript vs Typescript
Onderzoek de voor en nadelen van javascript en typescript. Kenmerken zijn ook belangrijk om mee te nemen in dit onderzoek. Als conclusie uit het onderzoek wordt bekend welke programmeertaal beter past in ons project.

### Voordelen
| Typescript voordelen | Javascript voordelen |
| :------------------: | :------------------: |
| Type safety door statische typen | Gebruiksvriendelijk |
| Fouten makkelijker op te sporen door de statische typen | Lagere 'learning curve' |
| Superset van js, dus js code of libraries is mogelijk | Geïnterpreteerde taal en niet gecompileerd |
| Biedt OOP mogelijkheden | Gebruik is mogelijk in combinatie met een groot scala aan platformen en technologieën |
| Overzichtelijker met grote projecten door code organisatie met namespaces | Grote community en veel libraries/frameworks |
| Ts is een superset van Js, hierdoor zijn de voordelen van Js ook grotendeels voordelen voor Ts | - |

### Nadelen
| Typescript nadelen | Javascript nadelen |
| :----------------: | :----------------: |
| Een steilere leercurve aangezien Ts meer mogelijkheden biedt ten opzichte van js | Zoekmachines vinden het lastig de inhoud van pagina's te ontdekken als het door js wordt opgebouwd |
| Niet alle Js libraries zijn mogelijk in combinatie met Ts | Cross-site scripting is een veel gebruikte aanval tegen js |
| Langere ontwikkelingstijd door de toevoeging van extra controles | Dynamische typen kunnen ervoor zorgen dat fouten lastiger zijn op te sporen |

### Kenmerken
#### Javascript
* Interactiviteit -> interactieve elementen toevoegen aan webpagina's
* Dynamische inhoud -> Een dynamische omgang met de inhoud van een webpagina
* Browsercompatibiliteit -> Wordt ondersteunt door alle moderne browsers
* Community & Libraries -> Een grote community en veel mogelijke libraries
* Dynamische typen -> Makkelijker programeren
* Bekend

#### Typescript
* Transcompilatie -> Moet omgezet worden naar Js, hierdoor is het ook heel compatibel met Js bestanden.
* OOP -> Mogelijkheden tot Object Oriënted Programming
* Optionele type safety / Statische typen -> De mogelijkheid om statische typen te gebruiken wat veiliger codeert
* Type-inferentie -> Automatisch typen kunnen afleiden op basis van de context
* Generics -> Mogelijkheid tot generics voor flexibele en herbruikbare constanten
* Code organisatie -> De mogelijkheid tot namespaces, modules en file organisation

### Conclusie
Aan de hand van bovenstaand onderzoek hebben wij een doordachte keuze gemaakt om verder te gaan met Typescript. We hebben hier een aantal redenen voor:
1. De typesafety -> Aangezien wij veel fouten maken is het erg fijn om sneller de fouten te kunnen opsporen en meer fouten te voorkomen. Dit zal ook de ontwikkeltijd versnellen
2. De object oriënted programming aspecten -> Aangezien wij met de casus veel met objecten en relaties zullen werken is het erg fijn dat dit ook het geval is in de frontend. We zijn ook al bekend met OOP dus de learningcurve zal extra hoog zijn hierdoor.
3. Js heeft geen grote voordelen ten opzichte van Ts -> Alles wat Js heeft, heeft Ts ook maar dan beter. Zo kan je alsnog dynamische typen gebruiken maar heb je nu ook de mogelijkheid tot het gebruiken van statische typen.
4. Code organisatie -> Aangezien het project verder zal groeien, hopen wij met de namespaces van typescript de organisatie in de code te verbeteren zodat het artefact goed leesbaar zal zijn voor iedereen. Ook als het project groeit.

> [!IMPORTANT]
> Met deze redenen maken wij de overwogen keuze om ons project verder uit te werken met React Typescript in plaats van Javascript.

#### Bronnen
1. [Phpbabu](https://www.phpbabu.com/nl/voordelen-en-nadelen-van-javascript/)
2. [Kinsta](https://kinsta.com/nl/kennisbank/wat-is-javascript/#:~:text=webpagina's%20en%20webtoepassingen.-,Is%20JavaScript%20veilig%3F,site%20scripting%20(XSS)%20aanval.)
3. [IO digital](https://www.iodigital.com/nl/history/orangedotcom/javascript-alles-wilt-en-moet-weten)
4. [Wikipedia](https://en.wikipedia.org/wiki/Java_(programming_language))
5. [Geeks 4 Geeks](https://www.geeksforgeeks.org/java/)
6. [App master](https://appmaster.io/nl/blog/javascript-versus-typoscript)
7. [netguru](https://www.netguru.com/blog/java-pros-and-cons#:~:text=Java%20is%20a%20versatile%20and,costs%2C%20and%20GUI%20development%20difficulties.)
8. [Human digital](https://humandigital.nl/nieuws-en-artikelen/javascript-vs-typescript-key-differences/)
9. [Youtube 1](https://www.youtube.com/watch?v=24G77lkNKPU)
10. [Youtube 2](https://www.youtube.com/watch?v=mAtkPQO1FcA)
11. [Kinsta - "Wat is Typescript? Een uitgebreide gids."](https://kinsta.com/nl/kennisbank/wat-is-typescript/)
12. [Human Digital - "Javascript vs Typescript"](https://humandigital.nl/nieuws-en-artikelen/javascript-typescript/)
13. [The server side - "Javascript vs Typescript: What's the difference?"](https://www.theserverside.com/tip/JavaScript-vs-TypeScript-Whats-the-difference)
14. [Medium - Typescript vs Javascript](https://medium.com/front-end-weekly/typescript-vs-javascript-a3c0beb8b6d9)
15. [Radix - "TypeScript vs JavaScript: Know The Difference"](https://radixweb.com/blog/typescript-vs-javascript)

---