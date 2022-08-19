# Microcoputer-lab
## Objective 

The main objective of this lab is for you to develop a small water level controlling system of a water tank using the knowledge of interrupts and other programming techniques of PIC16f877a from all the labs we did throughout the course<br>
## Introduction
In this lab we develop a small water level controlling system of a water tank using the knowledge of interrupts and other programming techniques of PIC16F877A. Three sensors which is placed in the water tank as below are used here to check the water level of the water tank. Two DC motors are used are used to pump water in when the water level is low and pump water out when the water level is high. Where motor 1 is used to pump water into the tank and the motor 2 is used to suck water out of the tank. The two motors work according to the three sensors. When the first sensor detects water level, and the others doesn’t the motor 1 activates and starts filling water into the tank and when the water level goes up to the second sensor the motor 1 stays on and keeps the water filling and when third sensor detects the water level the motor 1 turns off and the motor 2 activates and start sucking water out of the tank<br>

<img src="https://user-images.githubusercontent.com/111337119/185675962-05771fed-4d09-4597-ab0e-297f93a8f563.png" width=500 >
you can see the complete process in the following table<br>
<br>

<img src="https://user-images.githubusercontent.com/111337119/185676404-4b1960e6-5896-4773-a798-2ed3b8c88ed5.png" width=500 >

## Apparatus

•	PIC16F877A Microcontroller<br>
•	PCB<br>
•	2x 330Ω Resistors, 1X 1kΩ resistor<br>
•	2x LEDS<br>
•	2x Motors attached to plastic motor fans<br>
•	2x relay modules<br>
•	2x 22pFcapacitors<br>
•	Crystal oscillator<br>
•	Jumping wires<br>
•	Breadboard<br>
•	2x batteries<br>

## Procedure
•	The code needed to activate the sensors is programmed by the MPLAB software with the use of C programming. Here for the programming part interrupt functions were used in addition to the main function.<br>
•	Next the software-based implementation was done using proteus software using LEDS as a substitution for the motors and switches as a substitution for the water level sensors. <br>
•	There after the PCB was made and the soldering of the PIC holder, LEDS, Capacitors, oscillators and resistors were done, and the power was given. Also, three LEDS were soldered initially instead of motors to check if the code and the microcontroller was working properly with the sensor variations.<br>
•	After it worked the motors were connected with the use of relays and the motors were worked according to the variation of the IR Sensor as given in the above table 1<br>
## Proteus schematic diagram used to verify the code before physical implementation

<img src="https://user-images.githubusercontent.com/111337119/185677402-713ec84a-15bd-4641-82c0-237f04c1f9af.png" width=500 >
## PCB Design
PCB layout<br>

<img src="https://user-images.githubusercontent.com/111337119/185677694-1a21e1b9-0a35-45e9-ab3d-ed4b38497f87.png" width=500 >
 ## Real Implementation
 <img src="https://user-images.githubusercontent.com/111337119/185677868-7bb0e1ad-c46e-4f60-b4ba-679a4cf731fa.png" width=500 >

 <img src="https://user-images.githubusercontent.com/111337119/185678151-b0dc96ba-62d8-402f-a941-505ffce7d9da.png" width=500 >
 
 <img src="https://user-images.githubusercontent.com/111337119/185678239-32d745da-b037-4654-8348-48badb8f25b5.png" width=500 >
## Results
When the cover of IR sensor 1 which is connected to the port B pin 2 is removed the motor 1 will be activated and the fan connected to motor 1 will start spinning. When the sensor 2 connected to the Port B pin 1 of the microcontroller is uncovered (note that sensor 1 is also uncovered) the motor 1 will remain active and same process will happen when the sensor three is uncovered the Port B pin 0 interrupt will occur and the fan connected to motor 1 will turn off and fan of motor 2 will start spinning.<br>
Drive link to Implementing video -<br> https://drive.google.com/file/d/1fnrCYs5rXdZHivi_sKwrCcKetv8XF70b/view?usp=sharing<br>
