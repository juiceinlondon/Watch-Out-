
11.01.2023

Wir hatten die Idee entweder ein Radar oder ein Infrarot-Gerät (wovon wir noch nicht wissen, was die Funktion sein soll) zu bauen. Dabei haben wir uns ein Sensor-Kit mit 37 verschiedenen Sensoren für den Arduino besorgt, um diesen zu programmieren und auf unser gewünschtes Projekt abzustimmen.

17.01
erste arbeit mit dem arduino, led programmiert mit morsecode

18.01
programmieren unseres motion sensors und verbindung mit der led

24.01 
verbindung von motion sensor und entfernungsmesser

25.01 
Anschluss LCD

31.01
Vollendung Anschluss LCD, LCD funktioniert nicht 

01.02
LC Display funktioniert, programmieren der Anzeige von Entfernung zu Objekten

08.02
neue bauteile da, neu sortierung kabel + umstecken 

schaltplan LCD:
1 e30
2 d14
3 b21 
4 anschluss 0 
5 e26
6 anschluss 1
11 anschluss 6
12 anschluss 9
13 anschluss 10
14 anschluss 11
15 h14
16 e23

10.02
probleme mit neuem anschluss des lcds, problemfindung und Lösung (falscher anschluss des 5V- kabels)

### 15.02 
## Test der Messgenauigkeit des Entfernungsmessers
| Entfernung | gemessene Entfernung|
| -------------------------- |-----------|
| 20 |20|
| 35 |35|
| 40 |40|
| 55 |55|
| 80 |80|

### 22.02 
Heute sind Joel und ich beide krank gewesen.

### 24.02 
Heute sind Joel und ich beide krank gewesen.

### 01.03
In dieser Stunde war Joel krank. Wie wir im Vorfeld bescprochen haben, recherchierte ich heute über die Funktion von Servomotoren. Diesen benötigen wir für unsere Idee des rotierenden Ultrasonic Sensors, welcher so als Radar fungieren soll. Dazu schaute ich mir bereits vorhandene Projekte an, welche ebenfalls ein Radar enthielten. Zum Ende der Stunde begann ich damit, mit dem Programm ["Tinkercad"](https://www.tinkercad.com/) zu arbeiten. Dieses Programm ermöglicht es uns, unsere Schaltung digital nachzubauen. Da ich allerdings selbst noch nicht wieder ganz gesund war, konnte ich dieses Vorhaben nicht in der Stunde abschließen.  

### 03.03
Diese Doppelstunde fand im Homeschooling statt. Um meine Arbeit an Tinkercad zu vollenden, nahm ich unser Projekt mit nach Hause. Schlussendlich sah unser Schaltplan, digital übertragen, wie folgt aus: ![Plan](https://user-images.githubusercontent.com/111385267/225247385-37b29fbc-df0d-4f87-98e4-60150b2d79e1.png)


### 08.03 
Joel war heute erneut krank. Nachdem wir uns am Wochende über Servomotoren abgesprochen haben, begann ich heute damit, unseren Servomotor einzubauen. Dazu erstellte ich einen separaten Sketch, um ihn erst einmal zu testen. Da es an diesem Tag an einigen Computern Probleme mit dem Upload auf den Arduino gab, konnte ich das Testprogramm leider nicht weiter testen. 

### 10.03 
In dieser Stunde war Joel wieder da. Zudem legte Herr Buhl die Abgabe des zweiten Projektes auf den Zeitraum vom 05.04.2023 bis 07.04.2023 fest. Anschließend machten wir uns an die Arbeit mit dem Servomotor. Diese mussten wir nach einiger Zeit allerdings abbrechen, da der Servomotor und die angeschlossenen Kabel überhitzten. Außerdem begann das Display, dauerhaft zu flackern. Damit war unsere Idee, ein Radar in unseren Aufabau zu integrieren, verworfen.  
Zum Ende hin schlossen wir unsere LED wieder an. Hier mussten wir allerdings auf die Farbe blau ausweichen, da grün gar nicht funktioniert und rot nur minimal leuchtet. Folglich leuchtet die blaue Lampe nun auf, wenn eine Gefahr erkannt wird. Schließlich überlegten wir, welches weitere Bauteil wir anstelle des Servomotors einbauen können. Wir haben uns schlussendlich für einen [Active Buzzer](https://www.roboter-bausatz.de/projekte/buzzer-mit-arduino-steuern) entschieden. Dieser erzeugt ein Audio-Signal, wenn unser Bewegungssensor eine Bewegung registriert. So nimmt der Benutzer die Information über eine sich nähernde Bewegung über drei verschiedene Ausgabegeräte war: in Schriftform über das LCD, in Farbform über die LED und akustisch über den Active Buzzer.


