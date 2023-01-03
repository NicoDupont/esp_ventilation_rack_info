## Ventilation Automatique de mon rack Informatique

#### Quelques liens :
- Home Assistant : [HomeAssistant](https://www.home-assistant.io/) 
- Esphome : [Esphome](https://esphome.io/index.html) 
- Esphome-flasher : [Esphome-flasher](https://github.com/esphome/esphome-flasher/releases)

Ce petit montage est utilisé pour ventiler mon rack informatique si la température interne est trop élevée.    
Tout est configurable depuis l'interface de Home Assistant mais la logique se fait directement dans l'esp8266.   
Par defaut, le ventilateur est declenché.

### Fonctionnement :

On détermine un seuil X en température et on ventile si ce seuil est dépassé.   
Un test est réalisé toutes les 45 minutes si la ventilation doit continuer ou s'arreter. (Durée non paramétrable pour le moment)  
On peut forcer la ventilation et régler le seuil de temperature.

### Liste des composants :

- 1 ou 2 ventilateurs 12v/12cm de pc 3pins sans pwm (alimenté en 12v via le relai)
- 1x ftdi (1er flash)
- 1x esp8266 esp01 (pas un esp01s)
- 1x carte relai shield pour esp01-s (prendre une v4)
- 1x alimentation 12v dc suffisante pour alimenter le ou les ventilateurs
- 1x convertisseur 12v dc=>5v dc
- 1x convertisseur 5v dc=>3.3v dc (à revoir pas besoin normalement)
- 1x DHT22
- 1x resistance 4.7K ohm
- 1x boitier
- 1x interrupteur
- 1x fusible 20x5 1A + porte fusible

### Cablage :

Le data du dht22 doit etre directement soudé au GPIO2 sur la carte relai.  
Avec une resistance de 4.7kohm entre data et vcc (+3.3v).     

La sonde dht22 ne fonctionne pas correctement avec un esp01s sur le gpio2 (led bleu sur ce gpio) => à revoir.
J'ai du utiliser un esp01.   
Il y a un problème avec l'esp01. Sa mémoire est apparemment trop petite pour flasher en ota depuis esphome.  
Il faut donc le flasher a chaque modification du yaml avec esphome flasher ou via le navigateur.  

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/shema.png?raw=true)

### Montage :

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/boitier.png?raw=true)


### HomeAssistant :

#### Esphome :

1. créer un nouveau noeud dans esphome.  
2. le nommer 'esp_rack' ou comme vous le souhaitez... 
3. copier le code du fichier esp_rack.yaml  
4. Adapter le code (wifi, non des entités, etc...)
6. vérifier le code  
7. télécharger le binaire  
8. flasher votre esp avec esphome flasher  

#### DashBoard :

Rien de très spécial ici, 1 carte d'entités  + 2 mini graph

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/dashboardha.png?raw=true)
    






