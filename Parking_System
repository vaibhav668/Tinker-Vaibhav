#include <LiquidCrystal.h>

// LCD pins: RS, E, D4, D5, D6, D7
LiquidCrystal lcd(7, 6, 5, 4, 3, 2);

// Ultrasonic
int trig = 8;
int echo = 13;

// LEDs
int green = 9;
int yellow = 10;
int red = 11;

// Buzzer
int buzzer = 12;

void setup(){
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);

  pinMode(green, OUTPUT);
  pinMode(yellow, OUTPUT);
  pinMode(red, OUTPUT);
  pinMode(buzzer, OUTPUT);

  lcd.begin(16, 2);
  lcd.print("System Ready");
  delay(1000);
  lcd.clear();
}

void loop(){
  // Trigger ultrasonic
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  long duration = pulseIn(echo, HIGH);
  int distance = duration * 0.034 / 2;

  // Display distance
  lcd.setCursor(0,0);
  lcd.print("Dist: ");
  lcd.print(distance);
  lcd.print(" cm   "); // clear extra chars

  if(distance > 40){
    digitalWrite(green,HIGH);
    digitalWrite(yellow,LOW);
    digitalWrite(red,LOW);
    digitalWrite(buzzer,LOW);

    lcd.setCursor(0,1);
    lcd.print("SAFE       ");
  }
  else if(distance > 20){
    digitalWrite(green,LOW);
    digitalWrite(yellow,HIGH);
    digitalWrite(red,LOW);
    digitalWrite(buzzer,LOW);

    lcd.setCursor(0,1);
    lcd.print("SLOW       ");
  }
  else{
    digitalWrite(green,LOW);
    digitalWrite(yellow,LOW);
    digitalWrite(red,HIGH);
    digitalWrite(buzzer,HIGH);

    lcd.setCursor(0,1);
    lcd.print("STOP ");
  }

  delay(300);
}
