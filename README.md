# Bluetooth Home Control Automation (Arduino UNO)

## Project Overview
This project implements a home automation system that allows wireless control of electrical appliances using a smartphone over Bluetooth. By integrating the HC-05 Bluetooth module with Arduino UNO, the system provides real-time device control through simple commands sent from a mobile app. The logic and control flow are programmed in C/C++ for responsive and reliable operation.

## Components Used
- Arduino UNO microcontroller  
- HC-05 Bluetooth module for wireless communication  
- Relay module to switch electrical appliances  
- Breadboard and jumper wires for connections  
- Power supply for the circuit  
- Smartphone with Bluetooth serial controller app  

## Circuit Connections
- HC-05 Bluetooth module connected to Arduino (VCC to 5V, GND to ground, TX to Arduino RX, RX to Arduino TX via voltage divider)  
- Relay module connected to Arduino digital pins controlling individual appliances  
- Appliances wired to relay Normally Open (NO) contacts for safe switching  

## Working Principle
- The smartphone app pairs with HC-05 via Bluetooth  
- Commands like 'a', 'b', 'c' etc., sent from the app are received by Arduino  
- Arduino decodes commands to bring relays HIGH or LOW to turn devices ON/OFF  
- Real-time control of multiple appliances wirelessly  

## Sample Arduino Code Snippet
long int ac = 2;
long int bulb = 3;
long int heater = 4;
long int fan = 5;
char x;

void setup() {
pinMode(ac, OUTPUT);
pinMode(bulb, OUTPUT);
pinMode(heater, OUTPUT);
pinMode(fan, OUTPUT);
digitalWrite(ac, LOW);
digitalWrite(bulb, LOW);
digitalWrite(heater, LOW);
digitalWrite(fan, LOW);
Serial.begin(9600);
}

void loop() {
if(Serial.available() > 0) {
x = Serial.read();
if(x == 'a') digitalWrite(ac, HIGH);
if(x == 'b') digitalWrite(ac, LOW);
if(x == 'c') digitalWrite(bulb, HIGH);
if(x == 'd') digitalWrite(bulb, LOW);
if(x == 'e') digitalWrite(heater, HIGH);
if(x == 'f') digitalWrite(heater, LOW);
if(x == 'g') digitalWrite(fan, HIGH);
if(x == 'h') digitalWrite(fan, LOW);
}
}


## How to Use
1. Pair your smartphone Bluetooth with HC-05 module (default password 1234 or 0000).  
2. Open a Bluetooth serial controller app on the phone.  
3. Connect to the HC-05 module via the app.  
4. Send pre-defined characters to turn appliances ON/OFF.  

## Features
- Wireless control of home devices using smartphone Bluetooth  
- Easy to extend by adding more relay channels and commands  
- Simple hardware and cost-effective implementation  
- Safe switching of high voltage appliances using relay modules  

## Possible Future Enhancements
- Voice control integration  
- Automation with sensors (temperature, motion, light)  
- Wi-Fi or IoT integration for remote internet-based control  


