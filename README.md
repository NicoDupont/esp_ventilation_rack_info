## Ventilation Automatique de mon rack Informatique

#### Quelques liens :
- Home Assistant : [HomeAssistant](https://www.home-assistant.io/) 
- Esphome : [Esphome](https://esphome.io/index.html) 
- Esphome-flasher : [Esphome-flasher](https://github.com/esphome/esphome-flasher/releases)

Ce petit montage est utilisé pour ventiler mon rack informatique si la température interne est trop élevée.    
Tout est configurable depuis l'interface de Home Assistant mais la logique se fait directement dans l'esp8266.   
Par defaut, le ventilateur est declenché.

V2 : remplacement du dht22 par un sht31d (fonctionne bien mieux avec l'esp01s)

### Fonctionnement :

On détermine un seuil X en température et on ventile si ce seuil est dépassé.   
Un test est réalisé toutes les 45 minutes si la ventilation doit continuer ou s'arreter. (Durée non paramétrable pour le moment)  
On peut forcer la ventilation et régler le seuil de temperature.

### Liste des composants :

- 1 ou 2 ventilateurs 12v/12cm de pc 3pins sans pwm (alimenté en 12v via le relai)
- 1x ftdi (1er flash)
- 1x esp8266 esp01s
- 1x carte relai shield pour esp01-s (prendre une v4)
- 1x alimentation 12v dc suffisante pour alimenter le ou les ventilateurs
- 1x convertisseur 12v dc=>5v dc (lm2596 step down)
- 1x SHT31D (i2c pin 1 et 3)
- 1x boitier
- 1x interrupteur
- 1x fusible 20x5 1A + porte fusible

### Cablage :

v1 : dht22
Gros probleme avec le dht22 et l'esp01s... fonctionne bien sur un esp01
mais l'esp01 a une memoire trop petit pour les flash ota.

v2 : remplacement du dht22 par un sht31d et de l'esp01 par un esp01s

i2c sur les gpio 1 et 3
le relais sur le gpio 0

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/shema.png?raw=true)

### Montage :

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/boitier.jpg?raw=true)


### HomeAssistant :

#### DashBoard :

Rien de très spécial ici, 1 carte d'entités  + 2 mini graph

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/dashboardha.png?raw=true)
    






