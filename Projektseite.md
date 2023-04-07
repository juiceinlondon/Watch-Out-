# "Watch Out!"- Projektseite

Schule: Stormarnschule  
Fach: Informatik  
Lehrer: Herr Buhl   
Zeitraum: 01.2023-04.2023  

## Inhaltsverzeichnis  
1. [Der Beginn](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#der-beginn)    
   - [Die Teammitglieder](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#die-teammitglieder)   
   - [Unsere bisherigen Erfahrungen im Physical Computing](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#unsere-bisherigen-erfahrungen-im-physical-computing)  
   - [Die Ideenfindung](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#die-ideenfindung)   
   - [Benutzte Programme und Programmiersprachen](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#benutzte-programme-und-programmiersprachen)  
2. [Das Projekt](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#das-projekt)  
   - [Was ist "Watch Out!"?](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#was-ist-watch-out)  
   - [Bestandteile des Projektes](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#bestandteile-des-projektes)  
3. [Eigene abschließende Bewertung](https://github.com/juiceinlondon/Projekt-2/blob/main/Projektseite.md#eigene-abschlie%C3%9Fende-bewertung)  

## Der Beginn  

### Die Teammitglieder  
Auch für dieses Projekt haben wir, Joel Rosenberg und Lasse Prühs, erneut zusammengearbeitet. Unsere Partnerarbeit im letzten Halbjahr hat so gut funktioniert, dass einer erneuten Zusammenarbeit nichts im Weg stand.  

### Unsere bisherigen Erfahrungen im Physical Computing  
Wie bereits im letzten Projektbericht erwähnt, waren unsere Erfahrungen im Physical Computing zu Anfang eher begrenzt. Joel hatte in dem Bereich noch keine Erfahrungen und Lasse bisher nur LED-Lichtmuster programmiert. Folglich mussten wir uns, wie viele andere des Kurses auch, dieses Themenfeld erst einmal selbst erschließen.

### Die Ideenfindung  
Als Inspiration für das Projekt "Watch Out!" nahmen wir auch dieses Mal wieder ein Spiel, welches wir beide oft gemeinsam in unserer Freizeit spielen. In diesem Spiel gibt es verschiedene Gadgets, welche dem Spieler zur Verfügung stehen. Eines davon ist der "Herzschlagsensor". Dieser erkennt den Herzschlag anderer Spieler in der Nähe und gibt die Richtung, sowie die Entfernung zu diesem an. Dieses Gadget konnten wir aufgrund unserer technischen Möglichkeiten leider nicht nachbauen. Deshalb entschieden wir uns dafür, ein Gerät zu programmieren, welches bewegte Objekte in der Nähe erkennt und anschließend die Entfernung misst. Außerdem wollten wir ein Display so programmieren, dass dort die gemessene Entfernung angezeigt werden soll.  

### Benutzte Programme und Programmiersprachen  
Das Programm, welches wir in den drei Monaten benutzt haben, war [Arduino IDE](https://downloads.arduino.cc/arduino-ide/arduino-ide_2.0.4_Windows_64bit.exe), da nur damit der Arduino programmiert werden kann. Die für den Arduino verwendete Programmiersprache ist C/C++, welche weit verbreitet ist. In Arduino IDE kann der Benutzer verschiedene, sogenannte Sketches erstellen. Diese können über ein USB-Kabel einzeln auf den Arduino hochgeladen werden. So hat man die Möglichkeit, schnell die Funktionsweisen zu ändern und verschiedene Dinge auszuprobieren, ohne den Ursprungssketch verändern zu müssen. Zudem bleibt der Sketch auf dem Arduino vorhanden, wenn dieser vom Computer wieder entfernt wird. Mit einer externen Stromquelle kann der Arduino also mobil eingesetzt werden.  
Außerdem verwendeten wir [Tinkercad](https://www.tinkercad.com/), um unseren Aufbau digital nachzubauen.


## Das Projekt  

### Was ist "Watch Out!"?  
Unser Projekt "Watch Out!" ist ein Überwachungssystem, welches sich aktiviert, sobald eine Bewegung in der nahen Umgebung erkannt wird. Dadurch wird ein Entfernungsmesser angeschaltet, welcher anschließend die Enfernung misst. Währenddessen wird der Benutzer über drei verschiedene Ausgabegeräte über eine sich nähernde "Gefahr" informiert. Diese sind ein Liquid Crystal Display, ein Active Buzzer und eine RGB-LED.  
Bis zur letzten Iformatikstunde war unser Überwachungssystem noch direkt mobil einsetzbar. In dieser Stunde ist leider die Batteriebox in Brand geraten, sodass wir nun keine externe Stromquelle mehr haben.  
Der optimale Einsatzbereich von "Watch Out!" ist die Überwachung von Eingängen zu Räumen oder Häusern.  

### Bestandteile des Projektes  

Die Basis unseres Projkektes ist logischerweise der Arduino UNO selbst.  
An diesem haben wir ersteinmal einen Motion Sensor angeschlossen. Dieser hat für unser Projekt die wichtigste Funktion, da er die Entfernungsmessung des Ultrasonic Sensors erst aktiviert.  
Der Sensor ist an Pin 8 Arduino angeschlossen. Diesen mussten wir als "Input" definieren, da der Arduino über diesen Pin Informationen über erkannte Bewegungen erhält. Wir legten eine Variable "pirStat" fest. Diese liest die, über Pin 8 ankommenden, Werte des Motion Sensors aus. Wird eine Bewegung erkannt, dann wird "pirStat" auf "HIGH" gesetzt. Ist dies der Fall, dann wird der Rest unserer Schaltung in den Modus versetzt, in dem eine "Gefahr"/Bewegung erkannt ist und die Entfernung zu dieser gemessen werden muss. Andernfalls ist die Schaltung im Ruhemodus/sicheren Modus. Im Folgenden sind die Codezeilen, welche den Motion-Sensor bereffen, nachzulesen. 

```  
   int pirPin = 8;  
   int pirStat = 0;  
   
   void setup ()  
   {  
   pinMode(pirPin, INPUT);   
   }   
   
   void loop()  
   {  
   pirStat = digitalRead(pirPin);   
    if(pirStat == HIGH)     
    {
    ...
    } 
   else
    {
    ...
    }
   }
``` 


## Eigene abschließende Bewertung 

