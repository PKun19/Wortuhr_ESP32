# Wortuhr_ESP32
ESP32 Wortuhr mit Sound, Wetter, Spiele, Transitions, Webzugriff  
-----------------------------------------------------------------
## Hinweis:
Dies ist eine fortführung des ESP32 Wortuhr Projektes, die MP3 funktion werde ich auf Dauer entfernen und als reine Uhr weiter führen
- Enfällt: MP3, Temperatur- und Luftfeuchtesensor.

## Sonstiges:  
* Automatischer W-Lan Reconnect.  
* Mondphase wird in Abwechslung der Temp. und Datumsanzeige angezeigt.  
* Die Minuten LED können nun eine eigene Farbe haben.  
* Silvester CountDown.  
* Zwei Eingabe Taster sind möglich: On/Off und Mode. 
  Diese sind per Touch oder als physikalischer Taster in configuration.h einstellbar.  


## Temperatur und Luftdruck:  
* Als Temp. Sensor hatte ich einen BME280.  
* Aufzeichnen der Temperatur und Anzeige im Webfrontend.  
* Aufzeichnen des Luftdrucks und Anzeige im Webfrontend.   
* Wetterlage wird als Animation angezeigt.  


## Transitions:  
* 15 Transitions (Spirale, Matrix, Zur Mitte, u.s.w.) und diese einzeln oder per Zufall angewählt.   
* Alle Transitions sind jetzt 2 farbig.  
  D.h. z.B. Übergang 'nach links': die Buchstaben der 'alten' Zeit verschwinden mit der 'alten' Farbe nach links,  
  während rechts die Buchstaben der 'neuen' Zeit mit der 'neuen' Farbe reinkommen.  
  (sichtbar natürlich nur wenn die neue Farbe unterschiedlich zur alten Farbe ist. z.B. neue Farbe alle 5 Minuten)  


## Sound:   
* Anschluss eines MP3 Moduls (https://www.az-delivery.de/products/mp3-player-modul?_pos=1&_sid=9812a53bb&_ss=r) um der Uhr das Sprechen und verschiedene Sound zu entlocken. (Sounds werden einfach auf einer SD Karte nummeriert abgespeichert)  
* Verschiedene Stunden Sounds (Gong, Kuckuck, Vicki sagt die Uhrzeit , Hans sagt die Uhrzeit, usw.) per Settings einstellbar oder pro Tag ein anderer Sound.  
* Soundlautstärke in abh. der Tages/Nachtzeit.  
* Uhr erklärt nun im AP Mode was zu tun ist.  
* zusätzliche Stundensound (Westminster, alte Uhr, Kirche, usw.)  


## Webfrontend:   
* Webserver ohne das externe CSS File. (Denn die URL kann ja mal in Zukunft nicht mehr funktionieren). Alle CSS Files sind im SPIFFS des ESP abgelegt.  
* Eigenes Wortuhr Favicon eingefügt.  
* Werte auf Info Seite zur Einsicht aller wichtigen Parameter   
* Sonnenaufgangs- und Sonnenuntergangszeiten  
* Wettersymbole  


## Animationen:  
* Es können eigene Animationen für Deine Events erstellt werden.  
![Herz](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/HERZ.gif "Herz")  
* Über den eingebauten Animationseditor können Animationen erstellt werden  
![Animationsmenue](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/Animationsmenue.jpg "Animationsmenue")  
![Animationsmenue2](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/Animationsmenue2.jpg "Animationsmenue2")  
* Animationen mit bis zu 25 Frames möglich  
* Dadurch der gif2animation Konverter von kollabierer (https://www.kollabierer.de/farbe) direkt nutzbar.   
* Animationen mit Namen ZHHMM werden zur jeweiligen Stunde und Minute angezeigt (z.B. Z1200 startet eine Animation um 12 Uhr)  
* Animation mit Name ALARM wird während des Alarms angezeigt.  
![Alarm](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/ALARM.gif "Alarm")   
* Alle Animationen werden im SPIFFS unter dem Name ani_ANINAME.json gespeichert und können über den Dateimanager gesichert/kopiert werden.  


## Events:   
* Verschiedene Melodien werden passend zu den Events abgespielt.  
* Events werden über die Weboberfläche gepflegt.  
![Events](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/Events.jpg "Events") 
* Es können eigene Animationen für Deine Events erstellt werden.  
* Alle Events werden im SPIFFS unter dem Namen events.json abgelegt und können über den Dateimanager gesichert/kopiert werden.  


## Spiele:  
* 3 Wortuhrspiele integriert: 
Snake   
![Snake](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/snake.gif "Snake")  
Tetris  
![Tetris](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/tetris.gif "Tetris")  
Bricks  
![Bricks](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/bricks.gif "Bricks")  
* Sichern der Highscores im NVS  


## Settings:  
* Eingabe des Zeitservers über die Settings.  
* Systemname,WLan Parameter in Settings.  
* Soundtest in Settings  
* Dateimanager für den SPIFFS.  
* Angabe der Location und Höhe über 0 in Settings (wird für die WetterAPI und Berechnung des Luftdrucks auf Meereshöhe benötigt).  
* Es wird kein API-Key benötigt!  
* Eingabe des Automodeintervall in Settings  ( Intervall wie oft verschiedene Modes Wetter, Temperatur, Mondphase... angezeigt werden)  
* Highscores können hier gelöscht werden.  
* Stundensound pro Wochentag einstellbar und Testmöglichkeit der Sounds.  
* "Wochenend Lautstärke Erhöhung" wählbar. Am Wochenende zwischen 5 und 11 Uhr 2 h später lauter.  
* Sprecher Vicki oder Hans.  
* Stundenansage Vicki/Hans 12h oder 24h Format  
* und vieles mehr  


## System:  
* Neustart mit <UHR-IP>/reboot  
* compilierbar auch ohne mp3 Player (#define AUDIO_SOUND in der Configuration kommentieren)    
* WLAN Empfangsstärke wird auf der Infoseite angezeigt  

## Schaltplan:
https://github.com/manfred-hofmann/Wortuhr_ESP32_mp3/blob/main/Schaltplan_ESP32_wortuhr_mp3.pdf  

## LED-Layout: 
Es können verschiedene LED Layouts verwendet werden.  
In der configuration.h sind 4 voreingestellte Layouts zu finden:  

// Das LED Layout (Siehe in LedDriver.cpp):  
#define LED_LAYOUT_HORIZONTAL_2  
//#define LED_LAYOUT_VERTICAL_1  
//#define LED_LAYOUT_VERTICAL_2  
//#define LED_LAYOUT_VERTICAL_3  

Die Layouts sind in LedDriver.cpp  definiert.
Hier können nach belieben auch eigene angelegt werden.
Hierbei ist zu beachten:  
die ersten 10 Zeilen in ledMap sind die LEDs für die Wörter.
die letzte Zeile sind die Minuten LEDs angefangen links oben, rechts oben, rechts unten, links unten und die Alarm LED.  
Die Zahlen entsprechen der LED-Nummer in der LED-Kette:   
```
#ifdef LED_LAYOUT_VERTICAL_2
    uint8_t ledMap[] = {
          9,  10,  29,  30,  49,  50,  69,  70,  89,  90, 109,
          8,  11,  28,  31,  48,  51,  68,  71,  88,  91, 108,
          7,  12,  27,  32,  47,  52,  67,  72,  87,  92, 107,
          6,  13,  26,  33,  46,  53,  66,  73,  86,  93, 106,
          5,  14,  25,  34,  45,  54,  65,  74,  85,  94, 105,
          4,  15,  24,  35,  44,  55,  64,  75,  84,  95, 104,
          3,  16,  23,  36,  43,  56,  63,  76,  83,  96, 103,
          2,  17,  22,  37,  42,  57,  62,  77,  82,  97, 102,
          1,  18,  21,  38,  41,  58,  61,  78,  81,  98, 101,
          0,  19,  20,  39,  40,  59,  60,  79,  80,  99, 100,
      112,110,114,113,111
    };
#endif
```

Hier ein Beispiel Layout:  
![LED-Layout](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/LED-Beispiel-Layout.jpg "LED-Layout")   

Möchte man auf die "Alarm LED" verzichten, so muss in der configuration.h die Anzahl der LEDs angepasst werden:  
#define NUMPIXELS 114 -> ohne eigen Alarm LED  
#define NUMPIXELS 115 -> mit Alarm LED  


## Inbetriebnahme:  
* folgende Libraries werden benötigt (min. Versionen) (alle zu finden unter Bibliotheken verwalten):  
    * ESP32 Board Version 1.0.6  
	* MP3-Player - DFRobotDFPlayer Version 1.0.5  
	* BME280 - Adafruit BME280 Version 2.1.4  
	* Adafruit Unified Sensor Version 1.1.4  
	* Adafruit Neopixel: Version 1.8.0  
	* SunRise: Version 2.0.1  
	* Evt. EspSoftwareSerial Version 6.12.6 wenn die Fehlermeldung "gpio.h fehlt" erscheint.
* Die mp3 Files (Sound) in den Ordner "mp3" auf die SD-Karte kopieren welche in den mp3-Player kommt. Es reicht eine 4GB Karte.
* Software mit Arduino IDE (min. Version 1.8.12) auf den ESP32 laden.  
* ESP32 starten und mit dem Handy das WLAN der Wortuhr (WU_ESP32) suchen und anmelden.  
* Dann sollte automatisch der Browser starten. Hier die WLAN Zugangsdaten eingeben.  
(Falls der Browser nicht startet die Default IP des AP ist 172.20.2.1)  
(Falls es damit auch Probleme gibt können die WLAN Parameter auch direkt in configuration.h gepflegt werden.)  
* Danach startet der ESP32 neu. Jetzt mit dem Laptop auf die spiffs.html Webseite der ESP-Adresse gehen:  
    http://ESP32-IP/spiffs.html  
![Spiffs1](https://github.com/PKun19/Wortuhr_ESP32/main/pic/spiffs1.JPG "Spiffs1")
* Hier das komplette data Verzeichniss hochladen.  
![Spiffs2](https://github.com/PKun19/Wortuhr_ESP32/blob/main/pic/spiffs2.JPG "Spiffs2")
* __Evtl. nochmal die configuration.h durchgehen und die Einstellungen den eigenen Gegebenheiten anpassen!__   
* restliche Einstellungen sind auf der Settings Seite zu finden  

-----

Alles weiter findet sich auf http://diskussion.christians-bastel-laden.de/viewforum.php?f=23   
  
Ein Beispielvideo ist hier zu sehen:   
https://www.youtube.com/watch?v=rQZoOGkao-w
  

