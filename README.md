## CubeSat 
![](https://i0.wp.com/asiatimes.com/wp-content/uploads/2021/07/CubeSat.png?resize=1568%2C1029&ssl=1)

>  What is CubeSat


  CubeSat or Cube Satellite is a type of miniaturized satellite used for space research. It is as smaller as that of 1U of CubeSat=10 cm with mass of 1-1.33kg(s). The CubeSat Project began as a collaborative effort between Prof. Jordi Puig-Suari at California Polytechnic State University (Cal Poly), San Luis Obispo, and Prof. Bob Twiggs at Stanford University’s Space Systems Development Laboratory (SSDL). 
-  ![image](https://github.com/Prajwal1591/SI-2024-Cubesat/assets/174081452/3b5c551a-351d-4d06-acc6-8e87180cf455)
> ## Why Cubesat


   CubeSats are beneficial as-
 1. As weight and size is small, therefore it is cost effective.
 2. CubeSats can be used for a wide range of missions including Earth observation, scientific research, technology demonstration, communications, and more
 3. CubeSats adhere to standardized sizes (e.g., 1U, 2U, 3U, etc.), which makes them easier to design, build, and integrate into launch vehicles.
 4. CubeSats can be used to test new technologies or techniques in space with lower financial risk compared to larger, more expensive satellites.



> ## Dispenser System
 A dispenser system refers to a mechanism or device used to release satellites, payloads, or CubeSats into space from a launch vehicle.
 It provides attachment to the launching vehicles.
 The first dispenser for CubeSats was the Poly-Picosatellite Orbital Deployer (P-POD). It was developed by Cal Poly, San Luis Obispo.


 > ##
![image](https://github.com/Prajwal1591/SI-2024-Cubesat/assets/174081452/1499b083-6855-44c7-bee3-13c9ce5b6976)

 
> ## Minimal Payload


  It refers to the basic set of components and functionalities necessary to support communication tasks between the satellite and ground stations or between satellites in space.
  The minimal payload is the basic equipment or instruments they carry to achieve their mission goals. It could be something as simple as a small camera for taking pictures of Earth or A basic radio for sending and receiving signals. These payloads are designed to fit within the CubeSat's small size.
![SmartSelect_20240711_174010_Drive](https://github.com/Prajwal1591/SI-2024-Cubesat/assets/174081452/015c7014-89b7-40d6-a4b1-6a0922787006)     



> ## CubeSat Architecture
 CubeSat architecture is the standardized design and structure of these small satellites. CubeSats are characterized by their modular and scalable architecture, which enables rapid and cost-effective development, deployment, and operation in space.
- ---
> ## CubeSat Communication System
- Communication system of cubesat acts as a linkage between the satellite in space and the ground satellites. Various components associated with communication system are:-

**Antennas:**
             CubeSats may use deployable antennas that unfold or extend after launch to optimize signal transmission and reception. Some cuesat uses fixed antennas that are integrated in the structure.

  
**Transrecievers:**
           Transceivers transmit signals to ground stations or other satellites and receive signals for command and data retrieval.     
           
  
**Frequency band:**        
           CubeSats operate in various frequency bands allocated for space communication, such as UHF (Ultra High Frequency), S-band, X-band, and others.

**Command and Telemetry:**     
           CubeSats transmit telemetry data to ground stations, providing information about the satellite's health, status, and operational parameters.    
           
  
  > ## Micro processors and Micro controller

  Microprocesor is a subset of microcontrollers as microcontrollers are made up of microprocessor with some peripheral participants(such as touch semsors, bluetooth, wi-fi and many more).
Microprocessors and microcontrollers are integral components in satellite systems, contributing to overall functionality, data processing capabilities, communication efficiency, and mission success in various Earth observation, communication, scientific exploration, and technology demonstration missions.   


*1. Uses of Micro-proessor:-*
- Microprocessors are used for overall control and management of system.
- It handles commands & data processing, and manages communication with ground station.
- Microprocessors contribute to satellite navigation systems by processing data from onboard sensors.

*2. Uses of Micro-controllers:-*
- Microcontrollers are utilized in satellites for embedded systems applications, such as controlling subsystems and instruments.
- Microcontrollers play a role in managing power distribution and ensuring efficient energy usage.
- Microcontrollers often implement fault detection mechanisms and autonomous recovery procedures to relieve anomalies and ensure satellite operational reliability.
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
