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
Wie bereits im letzten Projektbericht erwähnt, waren unsere Erfahrungen im Physical Computing zu Anfang eher begrenzt. Joel hatte in dem Bereich noch keine Erfahrungen und Lasse hat bisher nur LED-Lichtmuster programmiert. Folglich mussten wir uns, wie viele andere des Kurses auch, dieses Themenfeld erst einmal selbst erschließen.

### Die Ideenfindung  
Als Inspiration für das Projekt "Watch Out!" nahmen wir auch dieses Mal wieder ein Spiel, welches wir beide oft gemeinsam in unserer Freizeit spielen. In diesem Spiel gibt es verschiedene Gadgets, welche dem Spieler zur Verfügung stehen. Eines davon ist der "Herzschlagsensor". Dieser erkennt den Herzschlag anderer Spieler in der Nähe und gibt die Richtung, sowie die Entfernung zu diesem an. Dieses Gadget konnten wir aufgrund unserer technischen Möglichkeiten leider nicht nachbauen. Deshalb entschieden wir uns dafür, ein Gerät zu programmieren, welches bewegte Objekte in der Nähe erkennt und anschließend die Entfernung misst. Außerdem wollten wir ein Display so programmieren, dass dort die gemessene Entfernung angezeigt werden soll.  

### Benutzte Programme und Programmiersprachen  
Das Programm, welches wir in den drei Monaten benutzt haben, war [Arduino IDE](https://downloads.arduino.cc/arduino-ide/arduino-ide_2.0.4_Windows_64bit.exe), da nur damit der Arduino programmiert werden kann. Die für den Arduino verwendete Programmiersprache ist C/C++, welche weit verbreitet ist. In Arduino IDE kann der Benutzer verschiedene, sogenannte Sketches erstellen. Diese können über ein USB-Kabel einzeln auf den Arduino hochgeladen werden. So hat man die Möglichkeit, schnell die Funktionsweisen zu ändern und verschiedene Dinge auszuprobieren, ohne den Ursprungssketch verändern zu müssen. Zudem bleibt der Sketch auf dem Arduino vorhanden, wenn dieser vom Computer wieder entfernt wird. Mit einer externen Stromquelle kann der Arduino also mobil eingesetzt werden.  
Außerdem verwendeten wir [Tinkercad](https://www.tinkercad.com/), um unseren Aufbau digital nachzubauen.


## Das Projekt  

### Was ist "Watch Out!"?  
Unser Projekt "Watch Out!" ist ein Überwachungssystem, welches sich aktiviert, sobald eine Bewegung in der nahen Umgebung erkannt wird. Dadurch wird ein Entfernungsmesser angeschaltet, welcher anschließend die Entfernung misst. Währenddessen wird der Benutzer über drei verschiedene Ausgabegeräte über eine sich nähernde "Gefahr" informiert. Diese sind ein Liquid Crystal Display, ein Active Buzzer und eine RGB-LED.  
Bis zur letzten Informatikstunde war unser Überwachungssystem noch direkt mobil einsetzbar. In dieser Stunde ist leider die Batteriebox in Brand geraten, sodass wir nun keine externe Stromquelle mehr haben.  
Der optimale Einsatzbereich von "Watch Out!" ist die Überwachung von Eingängen zu Räumen oder Häusern.  

### Bestandteile des Projektes  

Die Basis unseres Projektes ist logischerweise der Arduino UNO selbst.  
An diesem haben wir erst einmal einen Motion Sensor angeschlossen. Dieser hat für unser Projekt die wichtigste Funktion, da er die Entfernungsmessung des Ultrasonic Sensors erst aktiviert.  
Der Sensor ist an Pin 8 Arduino angeschlossen. Diesen mussten wir als "Input" definieren, da der Arduino über diesen Pin Informationen über erkannte Bewegungen erhält. Wir legten eine Variable "pirStat" fest. Diese liest die, über Pin 8 ankommenden, Werte des Motion Sensors aus. Wird eine Bewegung erkannt, dann wird "pirStat" auf "HIGH" gesetzt. Ist dies der Fall, dann wird der Rest unserer Schaltung in den Modus versetzt, in dem eine "Gefahr"/Bewegung erkannt ist und die Entfernung zu dieser gemessen werden muss. Andernfalls ist die Schaltung im Ruhemodus/sicheren Modus. Im Folgenden sind die Codezeilen, welche den Motion-Sensor betreffen, nachzulesen. 

```C  
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
Wird nun eine Bewegung erkannt, dann wird zunächst unsere RGB-LED angeschaltet. Diese leuchtet blau auf und ist am Arduino an Pin 2 angeschlossen, welcher folglich als "Output" definiert werden musste. Wird keine Bewegung erkannt, dann bleibt die LED ausgeschaltet.  
Außerdem erzeugt der Active Buzzer bei einer Bewegung ein akustisches Signal und bleibt ansonsten ebenfalls ausgeschaltet. Der Buzzer ist an Pin 3 angeschlossen.    
```C
int ledPinBlue = 2;  
int buzzerPin = 3; 
int pirPin = 8;  
int pirStat = 0;  
void setup ()  
   {  
     pinMode(pirPin, INPUT);  
     pinMode(2, OUTPUT);  
     pinMode (buzzerPin, OUTPUT);  
   }  
   void loop()  
   {  
   pirStat = digitalRead(pirPin);   
    if(pirStat == HIGH)     
    {
    digitalWrite(ledPinBlue, HIGH); 
    digitalWrite(buzzerPin, HIGH); 
    } 
    else
    {
    digitalWrite(ledPinBlue, LOW);  
    digitalWrite(buzzerPin, LOW);  
    }
   } 
```  
Zudem nimmt der Ultrasonic Sensor seine Arbeit auf. Dieser funktioniert über die Aussendung von Schallwellen und das Messen der Zeit, welche die Wellen benötigen, um zurück zum Sensor zu gelangen. Der Sensor ist an Pin 12 und 7 angeschlossen, wobei der Arduino über Pin 12 die Signale zum Aussenden der Wellen gibt und über Pin 7 die Informationen über die Dauer aufnimmt. Dafür legten wir die Konstanten "trigPin" für Pin 12 (Output) und "echoPin" für Pin 7 (INPUT) fest.  
Wird eine Bewegung erkannt, dann wird "trigPin" auf "HIGH" geschaltet, sodass Wellen ausgesendet werden. Nach einem kurzen Delay von 10 Microsekunden wird die Konstante wieder auf "LOW" gesetzt. 
Nun muss die Entfernung zur Bewegung ermittelt werden. Dazu legten wir zwei Variablen fest:"distance" und "duration". Die Zeit wird durch "pulseIn" angegeben. Diese Komponente misst die Dauer, zwischen dem Aussenden und Empfangen der Wellen. Die Entfernung wird schließlich durch diese Formel berechnet:   
```C
distance = duration * 0.034 / 2;  
``` 
Die Formel erhielten wir durch die Seite [Funduino](https://funduino.de/nr-10-entfernung-messen). Hier wird die Zeit mit der Schallgeschwindigkeit in Zentimeter pro Mikrosekunde multipliziert und durch 2 dividiert, da man nicht die insgesamt zurückgelegte Strecke der Wellen berechnen möchte, sondern nur den Hinweg. Das Ganze wird  mit einem Delay von 600 Millisekunden durchgeführt, um nicht zu schnell zu viele Werte zu erhalten. Im Folgenden ist nun der Code vom Ultrasonic Sensor in Verbindung mit LED, Buzzer und Motion Sensor zu sehen.

```C   
  int buzzerPin = 3;  
  int ledPinBlue = 2;  
  int pirPin = 8;  
  int pirStat = 0;  
  int distance;  
  const int trigPin = 12;  
  const int echoPin = 7;  
  long duration;  
  
  void setup ()  
 {
  pinMode (buzzerPin, OUTPUT);  
  pinMode(trigPin, OUTPUT);   
  pinMode(echoPin, INPUT);  
  pinMode(2, OUTPUT);  
  pinMode(pirPin, INPUT); 
 }  
 
 void loop()  
 { 
 
    pirStat = digitalRead(pirPin);   
    if(pirStat == HIGH)   
  {  
    
    digitalWrite(ledPinBlue, HIGH);  
    digitalWrite(buzzerPin, HIGH);  
    digitalWrite(trigPin, HIGH);  
    delayMicroseconds(10);  
    digitalWrite(trigPin, LOW);  

    duration = pulseIn(echoPin, HIGH);   
    distance = duration * 0.034 / 2;   
    
    delay(600);  
  }  
  
  else   
  {  
    digitalWrite(ledPinBlue, LOW);  
    digitalWrite(buzzerPin, LOW);  
   
    delay(600);  
  }  
 }  
``` 
Das letzte Bauteil ist das Liquid Crystal Display. Es ist das einzige Bauteil, neben dem Motion Sensor, welches dauerhaft aktiviert ist.
Um das Display zu verwenden, mussten wir zunächst die Funktion "LiquidCrystal.h" aus der Bibliothek einfügen. Außerdem mussten wir die Anschlüsse des Displays an den Arduino als Konstanten definieren. Wird der Arduino angeschaltet, dann wird das Display zunächst im Setup angeschaltet.  
Im Falle einer erkannten Bewegung wird der Cursor des Displays in die obere linke Ecke gesetzt. In der oberen Zeile wird dann "Abstand:" angezeigt. Anschließend wird der Cursor in die untere linke Ecke gesetzt. Dort wird die berechnete Entfernung angezeigt. Hinter der Entfernung wir außerdem die Einheit Zentimeter angegeben.  
Wird hingegen keine Bewegung erkannt, dann steht in der oberen Zeile "Keine Gefahr" und in der unteren Zeile "erkannt!".  
![20230407_125526](https://user-images.githubusercontent.com/111385267/230597620-06129828-ccb7-4794-af4f-beffc81164ee.jpg)

Im Folgenden ist nun der vollständige Code, der digitale Schaltplan und ein Video unseres Endproduktes zu sehen. 
```C 
#include <LiquidCrystal.h>  
   
  int buzzerPin = 3;  
  int ledPinBlue = 2;  
  int pirPin = 8;  
  int pirStat = 0;  
  int distance;  
  const int trigPin = 12;  
  const int echoPin = 7;  
  const int rs = 0, en = 1, d4 = 6, d5 = 9, d6 = 10, d7 = 11;  
  LiquidCrystal lcd(rs, en, d4, d5, d6, d7);  
  long duration;  
  
 
   
void setup ()  
 {  
  lcd.begin(16, 2);  

  pinMode (buzzerPin, OUTPUT);  
  pinMode(trigPin, OUTPUT);   
  pinMode(echoPin, INPUT);  
  pinMode(2, OUTPUT);  
  pinMode(pirPin, INPUT);   
 }  
  
 void loop()  
 { 
 
    pirStat = digitalRead(pirPin);   
    if(pirStat == HIGH)   
  {  
    
    digitalWrite(ledPinBlue, HIGH);  
    digitalWrite(buzzerPin, HIGH);  
    digitalWrite(trigPin, HIGH);  
    delayMicroseconds(10);  
    digitalWrite(trigPin, LOW);  

    duration = pulseIn(echoPin, HIGH);   
    distance = duration * 0.034 / 2;   

    lcd.clear();  
    lcd.setCursor(0, 0);   
    lcd.print("Abstand: ");  
    lcd.setCursor(0, 1);   
    lcd.print(distance);  
    lcd.print(" cm");  

    delay(600);  
  }  
  
  else   
  {  
    
    digitalWrite(ledPinBlue, LOW);  
    digitalWrite(buzzerPin, LOW);  
    
    lcd.clear();  
    lcd.setCursor(0, 0);   
    lcd.print("Keine Gefahr");  
    lcd.setCursor(0, 1);  
    lcd.print("erkannt!");  
   
    delay(600);  
  }  
 }  
```  

![229095857-246795b1-63eb-4af6-a477-c1b4e36be633](https://user-images.githubusercontent.com/111385267/230602996-689653e0-1d67-4eb5-85f2-5dada3cb3482.png)


https://user-images.githubusercontent.com/111385267/230602756-bf60fb6e-8ea2-425f-b99f-1d58ebaf45bd.mp4


## Eigene abschließende Bewertung 
Zusammenfassend sind wir beide der Meinung, dass uns die Arbeit mit dem Arduino sehr gut gelungen ist, trotz dessen, dass wir beide leider wieder oft krank waren. Zudem hat uns dieses Projekt nochmal deutlich mehr Spaß gemacht, als das vorherige. Der wesentliche Vorteil am Physical Computing ist aus unserer Sicht, dass man die programmierten Sketche nicht bloß in 2D auf dem Computer sieht, sondern die Resultate in 3D direkt vor sich stehen hat und anfassen kann. Dadurch ergaben sich für uns auch viel mehr Möglichkeiten im Bezug auf die Kreativität, da man nicht so stark durch die Gegebenheiten eines Programmes wie Greenfoot eingeschränkt war.  
Auch in diesem Halbjahr konnten wir unsere Fähigkeiten und unser Wissen im Bereich des Programmierens nochmal weiter fördern und ausbauen. Außerdem konnten wir auch in diesem Projekt wieder unsere außerschulischen Interessen einbringen, wodurch wir stets motiviert weitergearbeitet haben und uns immer auf den Informatikunterricht gefreut haben. Gerne hätten wir diesen schon in der zehnten und elften Klasse gehabt, da er immer wieder eine willkommene Abwechslung zum restlichen Schultag geboten hat.  
Was uns nun im Nachhinein aufgefallen ist, ist, dass in unserem auf Isurf hochgeladenen Sketch immernoch Elemente vorhanden sind, welche im Laufe des Arbeitsprozesses eigentlich hätten entfernt werden sollen, da sie für unser Endprodukt keine Rolle mehr spielen. 
