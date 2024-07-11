# CubeSat 
---
> CubeSat
-  CubeSat or Cube Satellite is a type of miniaturized satellite used for space research.
-  It is as smaller as that of 1U of CubeSat=10 cm with mass of 1-1.33kg(s)
-  ![](https://i0.wp.com/asiatimes.com/wp-content/uploads/2021/07/CubeSat.png?resize=1568%2C1029&ssl=1)
> Dispenser System
- A dispenser system refers to a mechanism or device used to release satellites, payloads, or CubeSats into space from a launch vehicle.
- It provides attachment to the launching vehicles.
- The first dispenser for CubeSats was the Poly-Picosatellite Orbital Deployer (P-POD). It was developed by Cal Poly, San Luis Obispo.
> Minimal Payload
-  It refers to the basic set of components and functionalities necessary to support communication tasks between the satellite and ground stations or between satellites in space.
> CubeSat Architecture
- CubeSat architecture is the standardized design and structure of these small satellites. CubeSats are characterized by their modular and scalable architecture, which enables rapid and cost-effective development, deployment, and operation in space.
> CubeSat Communication System
- Communication system of cubesat acts as a linkage between the satellite in space and the ground satellites. Various components associated with communication system are :-    
1.Antennas:
    CubeSats may use deployable antennas that unfold or extend after launch to optimize signal transmission and reception. Some cuesat uses fixed antennas that are integrated in the structure
2.Transrecievers:
   Transceivers transmit signals to ground stations or other satellites and receive signals for command and data retrieval.
3. Frequency band:
   CubeSats operate in various frequency bands allocated for space communication, such as UHF (Ultra High Frequency), S-band, X-band, and others.
4. Command and Telemetry:
  CubeSats transmit telemetry data to ground stations, providing information about the satellite's health, status, and operational parameters.

---
# LAB EXERCISES
## **Lab-01**
> Introduction to ESP-32

1.Installation and Configuration
## **Lab-02**
1.Blinking lights using ESP-32
## **Lab-03**
> Blinking multiple lights
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

# Lab-04
> Printing Tempersture and Humidity in oled display via ESP-32
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
