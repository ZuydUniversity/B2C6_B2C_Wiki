---
title: Onderzoek - Infrastructuur
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Database](database_onderzoek.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Infrastructuur</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Code Monitor](code_monitor_onderzoek.md)</a>
</nav>

---

# Infrastructuur onderzoek
## Wat is Ansible?
Ansible is een open-source automatiseringstool voor IT-taken, zoals configuratiebeheer, applicatiedeployment en taakautomatisering. Het werkt via infrastructuur als code, wat betekent dat infrastructuur en configuraties worden beheerd en gedocumenteerd met behulp van code, meestal in YAML-formaat.

### Voordelen van Ansible
1. **Agentloos**: Ansible werkt via SSH, wat betekent dat er geen extra software of agents op de beheerde nodes/servers hoeft te worden geïnstalleerd.
2. **Idempotentie**: Ansible zorgt ervoor dat dezelfde taak meerdere keren kan worden uitgevoerd zonder onbedoelde gevolgen, waardoor consistentie en betrouwbaarheid worden gewaarborgd.
3. **Flexibiliteit**: Ansible kan worden gebruikt om een breed scala aan taken te automatiseren, van eenvoudige systeemupdates tot complexe applicatie deployments.
4. **Community en Modules**: Grote set aan [modules](https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html) voor vrijwel elke taak en een actieve community die bijdraagt aan de ontwikkeling en ondersteuning.

## Deployen van een Docker-applicatie naar Azure
### Ansible
#### Voordelen
1. **Diepe Controle over Infrastructuur**:
   - Ansible biedt controle over de gehele infrastructuur, inclusief de hostsystemen waarop Docker-containers draaien. Dit kan handig zijn voor complexe infrastructuurconfiguraties en voor het toepassen van specifieke instellingen op de Docker-hosts zelf.
2. **Complexe Deployment Scenario's**:
   - Ansible is uitstekend geschikt voor complexe deployment scenario's waarbij meerdere stappen nodig zijn, zoals het provisioneren van servers, het instellen van netwerken, het installeren van afhankelijkheden en het uiteindelijk deployen van applicaties in Docker-containers.
3. **Herbruikbaarheid en Modulariteit**:
   - Ansible-rollen en -playbooks zijn zeer herbruikbaar en modulair. Dit betekent dat configuraties en deployment-logica eenvoudig kunnen worden hergebruikt en gedeeld tussen verschillende projecten.

#### Nadelen
1. **Complexiteit en Leercurve**:
   - Voor teams die niet bekend zijn met Ansible kan de leercurve erg steil zijn. Het vereist kennis van YAML, Ansible-specifieke syntaxis en best practices voor infrastructuur als code.
2. **Onderhoud van Playbooks**:
   - Naarmate het aantal playbooks en rollen groeit, kan het beheer en onderhoud van deze scripts complex en onoverzichtelijk worden. Dit vereist goed versiebeheer en documentatie.

## Conclusie
Ansible is een krachtige tool voor het automatiseren van deployments en het beheren van infrastructuur, vooral wanneer diepgaande controle en configuratie van complexe infrastructuuromgevingen vereist zijn.
Ansible kan een steile leercurve hebben voor teams die er nog niet mee bekend zijn, en het beheer van playbooks en rollen kan complex worden naarmate het aantal toeneemt.
Goed versiebeheer en documentatie zijn cruciaal om deze complexiteit te beheersen.

Verder heeft Ansible handige mogelijkheden om een server snel op te bouwen, dit kan handig zijn zodra een server of infrastructuur uitvalt.
Aangezien met Ansible deze infrastructuur snel opnieuw opgebouwd en opgezet kan worden.

---