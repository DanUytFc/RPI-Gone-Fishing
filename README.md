# Pi-Iot
## Beschrijving
Meten en opvolgen van het energieverbruik en opbrengst is gloeiend actueel. Dit geldt zowel voor thuis als op afstand zoals tweede verblijf. 

Dit project implementeerd een *framework* voor ***energy analyse*** gebaseerd op een Raspberry ***Pi-Iot*** oplossing. Het kreeg als bijnaam 'Pilot'.
## Bronnen
Eén van de economische gevolgen van de COVID-19-pandemie zijn de stijgende energieprijzen van elektriciteit en gas. Sinds enige tijd hou ik mijn meterstanden(elektriciteit, gas, zonnepanelen, water, auto) bij in de ***[EnergieID](https://app.energyid.eu)*** web/app.  

Binnen de scope van dit project moeten volgende doeleinden geimplementeerd worden: 
- [ ] Een notificatie op begin van de maand herinnert mij eraan om deze meters af te lezen op specifieke teller of app en manueel in te voeren. Voor meters op afstand zou dit geautomatiseerd moeten worden door de gegevens iedere 15min door te sturen. 
- [ ] Door het invoeren van een slimme thermostaat kan het gasverbruik voor de verwarming geoptimaliseerd worden. Dit moet verder verfijnt worden door de nachtstand van de verwarming te activeren om 22:00.
- [ ] De status van de Raspberry Pi(on/off-line, on/off-power) voor thuis en op afstand moet kunnen opgevolgd worden d.m.v. iOS app(Home Assistent, Tuya Smart Life). 
- [ ] Notificaties worden naar iOS IFTTT app en Smartwatch gestuurd. 
## Hardware
De implementatie vereist 2 Raspberry Pi boards: 
1. *Raspberry Pi 2 Model B Rev 1.1:* installatie thuis. 
2. *Raspberry Pi Zero 2 W:* installatie op afstand.

Aangezien hardware levering een probleem is in deze pandemie periode zal ik terugvallen op de beschikbare Raspberry Pi Model B Rev 1.1 voor zowel de installatie thuis als op afstand. Zodra de Raspberry Pi Zero 2W terug beschikbaar is zal de installatie op afstand hiernaar gemigreerd worden. 
## Software
Dit project zal geimplementeerd worden op de meest recente ***Bullseye Raspberry Pi OS***. 
1. Schakel scherm energiebesparende functies uit. Dit is noodzakelijk bij gebruik in de leslokalen. Anders blokkeerd het scherm en is een reboot noodzakelijk. 
```
pi@RPIDanUyt:~ $ mkdir .local/bin
pi@RPIDanUyt:~ $ cd .local/bin
pi@RPIDanUyt:~/.local/bin $ vi energiebesparend.sh
#!/bin/bash
xset s off
xset -dpms
xset s noblank
pi@RPIDanUyt:~/.local/bin $ chmod +x energiebesparend.sh
pi@RPIDanUyt:~/.local/bin $ cd
pi@RPIDanUyt:~ $ mkdir .config/autostart
pi@RPIDanUyt:~ $ cd .config/autostart
pi@RPIDanUyt:~/.config/autostart $ vi energiebesparend.desktop
[Desktop Entry]
Type=Application
Exec=/home/pi/.local/bin/energiebesparend.sh
pi@RPIDanUyt:~/.config/autostart $
```
2. Installatie [Home Assistant](https://www.home-assistant.io): 
   * Hierbij volg ik de instructies uit de cursus *RASPBERRY Pi - DEEL 1(5.c Domotica)*. Raadpleeg de [log file](Logs/Home_Assitant_logfile.txt) voor meer details. 

>Noteer eveneens welke aanpassingen je aan welke configuratiebestanden je hebt doorgevoerd.
## Eigen scripts en programma's
>Sla je aparte bestanden op in deze repository.

## Uitbreidingen
>Noteer hier uitbreidingen die na de implementatie van de initiële scope zullen behandeld worden. 
## Afbeeldingen
1.  Raspberry Pi 2 Model B Rev 1.1:

![Raspberry Pi 2 Model B Rev 1.1](Images/raspberry-pi-2-model-b-v11-1gb-ram.jpg)

2. Raspberry Pi Zero 2 W:

![Raspberry Pi Zero 2 W](Images/raspberry-pi-zero-2-w-hero-800x535.jpg)

## Nuttige commando's
| Command | Description |
| --- | --- |
| cat /proc/device-tree/model | Geef het PI model weer |
| ip addr | show addresses to network interfaces |
| man -k | manual page keyword |
| python -- | Python versie |
