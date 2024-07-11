# Introduction to CubeSat
------
# Lab-01
### Introduction to ESP-32
1.Installation and Configuration
# Lab-02
1.Blinking lights
# Lab-04
- 
```python
#include<Wire.h>
#include<Adafruit_GFX.h>
#include<Adafruit_SSD1306.h>
#include<Adafruit_Sensor.h>
#include "DHT.h"


#define SCREEN_WIDTH 128   //Display's width
#define SCREEN_HEIGHT 64   //display's height
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

#define DHT11PIN 26

DHT dht(DHT11PIN,DHT11);
void setup(){
   Serial.begin(9600);
   dht.begin();
  if (!display.begin(SSD1306_SWITCHCAPVCC,0X3C)) {
    Serial.println(F("SSD1306 allocation failed"));
    for (;;);
  }
  delay(2000);
  display.clearDisplay();
  display.setTextSize(1);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,00);
  display.display();
  delay(2000);
  dht.begin();
  }
  void loop(){
    delay(5000);
   float humi = dht.readHumidity();
   float temp = dht.readTemperature();
   if(isnan(humi) || isnan(temp)){
    Serial.println("Failed to read from DHT sensor");
   }

   display.clearDisplay();
   
  display.setTextSize(1);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,00);
  display.println("Temperature:");
  display.setTextSize(2);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,10);
  display.print(temp);
  display.print("C");

  
  display.setTextSize(1);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,35);
  display.println("Humidity:");
  display.setTextSize(2);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0,45);
  display.print(humi);
  display.print("%");

  display.display();
  

  }
```
>code for mytiple blinking lights
```python
#define LED1 2
#define LED2 4
#define LED3 5
#define LED4 18
#define LED5 19

void setup(){
  pinMode(LED1,OUTPUT);
  pinMode(LED2,OUTPUT);
  pinMode(LED3,OUTPUT);
  pinMode(LED4,OUTPUT);
  pinMode(LED5,OUTPUT);
  
}

void loop(){
  digitalWrite(LED1,HIGH);
  delay()100;
  digitalWrite(LED1,LOW);
  delay(100);
  digitalWrite(LED2,HIGH);
  delay()100;
  digitalWrite(LED2,LOW);
  delay(100);
  digitalWrite(LED3,HIGH);
  delay()100;
  digitalWrite(LED3,LOW);
  delay(100);
  digitalWrite(LED4,HIGH);
  delay()100;
  digitalWrite(LED4,LOW);
  delay(100);
  digitalWrite(LED5,HIGH);
  delay()100;
  digitalWrite(LED5,LOW);
  delay(100);
}
```
