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

## PCB DESIGN 
PCB layout<br>

<img src="https://user-images.githubusercontent.com/111337119/185677694-1a21e1b9-0a35-45e9-ab3d-ed4b38497f87.png" width=500 >

 Real implimentation<br>
 <img src="https://user-images.githubusercontent.com/111337119/185677868-7bb0e1ad-c46e-4f60-b4ba-679a4cf731fa.png" width=500 >

 <img src="https://user-images.githubusercontent.com/111337119/185678151-b0dc96ba-62d8-402f-a941-505ffce7d9da.png" width=500 >
 
 <img src="https://user-images.githubusercontent.com/111337119/185678239-32d745da-b037-4654-8348-48badb8f25b5.png" width=500 >
 
 ## Results
 
When the cover of IR sensor 1 which is connected to the port B pin 2 is removed the motor 1 will be activated and the fan connected to motor 1 will start spinning. When the sensor 2 connected to the Port B pin 1 of the microcontroller is uncovered (note that sensor 1 is also uncovered) the motor 1 will remain active and same process will happen when the sensor three is uncovered the Port B pin 0 interrupt will occur and the fan connected to motor 1 will turn off and fan of motor 2 will start spinning.<br>
Drive link to Implementing video -<br> https://drive.google.com/file/d/1fnrCYs5rXdZHivi_sKwrCcKetv8XF70b/view?usp=sharing<br>
## Code
The code used in implementing this water tank consists of two function the main function and the interrupt function. The main function runs until the water level fills pass the two sensors at the bottom of the tank and the motor 1 turns on. When the topmost sensor detects water the interrupt function will be called as that sensor is connected to the RB0 pin of the microcontroller and the motor 1 turns off and motor 2 will turn on as programmed in the below code. <br>
<br>

            // PIC16F877A Configuration Bit Settings

            // 'C' source line config statements

            // CONFIG
            #pragma config FOSC = HS        // Oscillator Selection bits (HS oscillator)
            #pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
            #pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
            #pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
            #pragma config LVP = OFF        // Low-Voltage (Single-Supply) In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for             programming)
            #pragma config CPD = OFF        // Data EEPROM Memory Code Protection bit (Data EEPROM code protection off)
            #pragma config WRT = OFF        // Flash Program Memory Write Enable bits (Write protection off; all program memory may be written to by EECON control)
            #pragma config CP = OFF         // Flash Program Memory Code Protection bit (Code protection off)

            // #pragma config statements should precede project file includes.
            // Use project enums instead of #define for ON and OFF.

            //#include <xc.h>
            #include<htc.h> 

            #define _XTAL_FREQ 20000000

            void __interrupt() isr(void) 
            {
               if(RB2 == 1 && RB1 == 1)
                {   
                   RC0 = 0;
                    RC1 = 1;
                    __delay_ms(500);
                    RC1 = 0;    
                }<br>
                INTF = 0;
    
            }
            void main(void)
                        {
                GIE = 1;   
                INTE = 1; 
                INTF = 0;
                //PEIE = 1 ;  
               INTEDG = 1;
    
                TRISB0 = 1;//SWITCH 03
                            TRISB1 = 1;//SWITCH 02
                TRISB2 = 1;//SWITCH 01
                TRISC0 = 0;
                TRISC1 = 0;
                //PORTB = 0X00;
                PORTC = 0X00;
      
    while(1)
    {        
        if(RB2 == 1 && RB1 == 0 && RB0 == 0){
            RC0 = 1;
            RC1 = 0; 
        }<br>
        if(RB2 == 1 && RB1 == 1 && RB0 == 0){
            RC0 = 1;
            RC1 = 0;
        }else if(RB2 == 0){
            RC0 = 0;
            RC1 = 0;
        }
    }
    return;
            }

## Coclusion
The lab was a tough one. We had to overcome many difficulties and learn a lot of new things to make the system work. However, we enjoyed a lot as we were able to get the outcome we needed. Soldering PCBs working with them and relay modules, IR sensors are few of the main things out of the many things we learnt in this lab.<br>


