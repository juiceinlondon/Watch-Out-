#include <LiquidCrystal.h>  
  

  int taster=7;   
  int tasterstatus=0;  
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
  pinMode(4, OUTPUT);  
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
    Serial.print("Distance: ");  
    Serial.print(distance);  
    Serial.println(" cm");  

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
