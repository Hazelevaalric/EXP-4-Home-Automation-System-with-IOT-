# EXP-4-Home-Automation-System-with-IOT

# Aim:
	To make a Lamp at home (230 V AC) On / Off using ESP8266, IFTT Google Assistance and Blynk IoT mobile application. 
# Hardware / Software Tools required :
PC with Internet connection
Micro USB cable
Wifi connection for ESP8266 (Use any mobile hotspot or Router)
ESP8266 Board
Mobile Phone with Blynk App installed
IFTT for Google Voice Assistance
9 W Bulb and Relay control
Arduino software 
Jumper Wires

# Procedure:
•	Make the circuit connection as per the diagram. In the mobile, download and “Blynq IoT” application using Google play store and Install it. Create log in ID and Password.
•	Connect the IN pin of the Relay module to D1 pin of NodeMCU (ESP8266).
•	Connect VCC of the Relay of NodeMCU. Connect GND of the Relay to GND of NodeMCU. 
•	Connect your AC bulb to the Relay’s switch terminal securely.
•	Install ESP8266 board in Arduino IDE via Board Manager. Select board: NodeMCU 1.0 (ESP-12E Module).
•	Include necessary libraries: ESP8266WiFi and ESP8266WebServer.
•	In the code, configure Wi-Fi SSID and Password.
•	Set up a web server that responds to /on and /off URLs.
•	Upload the code to the ESP8266 using a micro USB cable.
•	Get Local IP Address After uploading, open Serial Monitor to find the local IP address of ESP8266.
•	Create Applets on IFTTT - For "This", select Google Assistant → "Say a simple phrase". Command: "Turn on the light". For "That", choose Webhooks → "Make a web request". 
•	Repeat to create another applet for command with URL.
•	Test the System - Google Assistant triggers IFTTT → sends Webhook to ESP8266 → turns ON the relay (light).
•	Say "Turn off the ligh to switch it OFF, Say "Turn on the light" to switch it ON.


# Pin Diagram:

<img width="540" height="299" alt="image" src="https://github.com/user-attachments/assets/e851af15-4b22-4f5b-ae74-4d6cd2428a60" />

P1[23]/MCFB1/PWM1[4]/MISO0 37[1] I/OP1 [23] — General purpose digital input/output I MCFB1 — Motor control PWM channel 1,Encoder Interface PHB input. O PWM1 [4] — Pulse Width Modulator 1, channel 4 outputs. I/O MISO 0 — Master In Slave Out for SSP0.

# Circuit Diagram:
<img width="622" height="306" alt="image" src="https://github.com/user-attachments/assets/b1712c29-24fb-4799-82d0-60c7f0e7e1d6" />

# Theory: 


Blynk is an IoT platform for iOS or Android smartphones that is used to control Arduino, Raspberry Pi and NodeMCU via the Internet. This application is used to create a graphical interface or human machine interface (HMI) by compiling and providing the appropriate address on the available widgets.In this experiment we use ESP8266 to control a 220-volt lamp from a web server. But you can also use the same procedure to control fans, lights, AC, or other electrical devices that you want to control remotely.
Relay is an electromechanical device that is used as a switch between high current and low current devices. When the coil in the relay gets fully energized, the contact shifts from the normally open position to the normally closed position. Light bulbs usually operate on 120V or 220V AC power supply. We cannot interface these AC loads directly with the ESP8266 development board, or it will damage the board. We have to use a relay between the ESP8266 and the lamp. 
Google Assistant and IFTTT work together to let you control services with voice commands. When you say a set phrase, Google Assistant processes it and sends it to IFTTT as a trigger. If the phrase matches an applet you've created, IFTTT performs the linked action—like turning on a light or sending a message. Everything runs in the cloud, making it easy to automate tasks with just your voice, as long as the command is correctly matched and all services are online.
When we apply an active high signal to the signal pin of the relay module from any microcontroller like ESP8266, the relay contact moves from the normally open to the normally closed position. It makes the circuit complete, and the output load turns on.


# Program:
```
#include <lpc17xx.h>

#include "delay.h"	//User defined library which conatins the delay routines #include "gpio.h"

#define LED P1_29	// Led is connected to P1.29

/* start the main program */ int main()

{

SystemInit();	//Clock and PLL configuration GPIO_PinFunction(LED,PINSEL_FUNC_0); // Configure Pin for Gpio GPIO_PinDirection(LED,OUTPUT);	// Configure the pin as OUTPUT GPIO_PinWrite(LED,LOW);
while(1)

{

/* Turn On all the leds and wait for 100ms */ GPIO_PinWrite(LED,HIGH);	// Make all the Port pin as high DELAY_ms(100);

GPIO_PinWrite(LED,LOW);	// Make all the Port pin as low DELAY_ms(100);

}

}
```


# Output:

<img width="794" height="580" alt="image" src="https://github.com/user-attachments/assets/2f2e29ce-e278-43d2-8d57-f09b574b5957" />

# Result:
Thus a LED is interfaced with ARM LPC1768 microprocessor and its blinking was verified successfully.
