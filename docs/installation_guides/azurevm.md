---
title: Installation Guides - Azure VM
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
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Installation guide](prerequisites.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[ReactTs](reactts.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[FastAPI](fastapi.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Docker](docker.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[DBeaver](dbeaver.md)</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">Azure VM</a>
  <a markdown="1" style="text-decoration:none; color:#333; font-weight:bold;">[Linter](linter.md)</a>
</nav>

---

# Azure Virtual Machines {#vm}

## Aanmaken Virtual Machine

Als je navigeert naar Azure, kijk eerst als je in de juiste map zit. De map waar je in moet zitten heet ZKOO. Als je hier niet in zit, klik rechtsboven in het scherm op je username, en dan op "**Schakelen tussen mappen**". Dan zie je Hogeschool Zuyd en ZKOO. Als je ZKOO niet hebt, dan moet je nog de invite e-mail accepteren dat je hebt gekregen op je school e-mail.

Eenmaal op de ZKOO, klik op de Resource Group knop en ga naar B2C6C. Dan open je de Azure CLI. Deze knop bevindt zich bovenaan in de blauwe balk. Klik op het terminal-icoontje (links van de notification bel) om de CLI open te maken. Je kunt kiezen tussen Powershell en Bash, ik heb Bash gebruikt want alle Microsoft guides doen dat ook als standaard gebruiken.

Om te beginnen moet je inloggen met de credentials die we gekregen hebben in Slack. Copy/Paste deze login commando. **REMINDER!** Copy/Pasting is een beetje anders. Je moet ctrl+shift+c/ctrl+shift+v gebruiken in de terminal.

**Het login commando staat gepint in het b2c6devops-b2c kanaal op Slack**

https://b2c6devops2023bp4.slack.com/archives/C0720SZMF7X/p1716892218018419?thread_ts=1716277065.656229&cid=C0720SZMF7X

Als je nu een VM wilt aanmaken dan gebruik je dit commando:

`az vm create --resource-group B2C6C --name [vm naam] --image Canonical:0001-com-ubuntu-minimal-jammy:minimal-22_04-lts-gen2:latest --admin-username b2c6c --assign-identity --generate-ssh-keys --public-ip-sku Standard --location westeurope --size Standard_B1s --storage-sku Standard_LRS --nic-delete-option delete --os-disk-delete-option delete `

Na een tijdje krijg je een melding met wat informatie erin. Als je nu de pagina van de resource group refresht dan zie je je nieuwe VM en alle bijbehorende dingen.

## Verwijderen van de VM en bijbehorende items.

Als je de VM wilt verwijderen voor wat voor reden dan ook, dan voer je deze commando's uit. Ze zijn ongeveer hetzelfde op het bestandsnaam en type bestand na.

Verwijderen van de VM: `az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Compute/virtualMachines" --verbose`

Verwijderen van het Network Interface: `az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/networkInterfaces" --verbose`

Verwijderen van de Network Security Group: `az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/networkSecurityGroups" --verbose`

Verwijderen van het Public IP: `az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/publicIPAddresses" --verbose`

Verwijderen van het Virtual Network: `az resource delete --resource-group B2C6C --name [VM naam] --resource-type "Microsoft.Network/virtualNetworks" --verbose`

## Inloggen naar de VM via Termius

1. Installeer Termius via de website: https://www.termius.com/free-ssh-client-for-windows
2. Eenmaal in Termius, voeg een nieuwe host toe.
3. Vul het IP-adres in van de VM. Die vind je op als je op de VM klikt waar je mee wilt verbinden, en dan klikt op "Verbinden"
4. Log in met het Admin Username wat je hebt gebruikt bij het aanmaken van de VM. (Standaard b2c6c van maken?)
5. Voeg een Key toe. Geef de key een naam. Hier moet je de private key invullen. Deze kan je vinden in Azure als je ingelogt bent. **Dus niet in je VM maar op de Azure pagina!**. Voer na het inloggen op de CLI.
6. In de CLI, bekijk de .ssh folder door `ls -l ~/.ssh` uit te voeren. Dan kijk je naar wat de filename is van de key zonder **.pub**.
7. Voer nu het volgende commando uit; `cat ~/.ssh/[keynaam]`. Je krijgt een muur van tekens, kopieer deze (inclusief de ---begin--- en ---end--- deel van de key)
8. Voer deze private key in bij de Key optie in Termius.
9. Probeer verbinding te maken met de VM. Als alles goed is gegaan heb je nu verbinding met de VM en zit je in de main directory!

## Docker installeren

We gaan docker insalleren met behulp van apt.

1. Log in je VM en voer als eerste een apt update uit met `sudo apt-get update`.
2. Als de update klaar is dan typ je `sudo apt-get install ca-certificates curl`. Hiermee krijgen we curl certificaten. Curl gebruik je om gegevens over te brengen via URL's

**Linux is heel leuk en geeft soms geen output of feedback als iets werkt. Als je niks terug krijgt kan je er van uit gaan dat het succesvol is uitgevoerd**

3. Nu maak je een nieuwe directory aan waar je de docker files in gaat installeren. Dit doe je met `sudo install -m 0755 -d /etc/apt/keyrings`. Voor wie het interesseert, de **-m 0775** zorgt ervoor dat de directory een "Read & Execute permission heeft" voor iedereen en een "Write permission" voor de eigenaar.
4. Als je wilt controleren als alles goed is gelukt, dan voer je dit commando uit: `ls -ld /etc/apt/keyrings`. Als je een output krijgt wat lijkt op dit: `drwxr-xr-x 2 root root 4096 May 30 12:34 /etc/apt/keyrings` dan is alles goed.
5. Nu gaan we een docker bestand downloaden van de website met het volgende commando: `sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`
6. Als laatste voeren de nog dit commando uit: `sudo chmod a+r /etc/apt/keyrings/docker.asc`
7. Voer dit commando uit (alles tegelijk in de terminal gooien):

`echo \   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \   $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`

8. eindig nu met een `sudo apt-get update`
9. Nu gaan we meest recente docker versie installeren met dit: `sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
10. Het kan zijn dat je moet kiezen tussen libraries, maar als je hier niet veel van weet tik je maar 15 in om het over te slaan.
11. Om te kijken als het is gelukt, voeren we dit commando uit: `sudo docker run hello-world` Hiermee haalt die de hello-world image uit de Docker Hub.

---