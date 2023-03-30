# floorcleaningrobot.ino
====== Floor Cleaning Robot ======
 --- //1221B [[denisa.voicu2504@stud.fils.upb.ro |Denisa Florina Voicu]]//
===== Introducere =====

The scope of this project is to create a floor cleaning device that will make your cleaning days easier.This robot that resembles Roomba will have  HC-SR04 ultrasonic distance sensors that will allow the robot to avoid obstacles so that it can move freely until the room is properly cleaned.It will also have an IR Module that will help it to avoid falling from stairs.

===== Descriere generală =====

A robot that cleans your house's floor.The robot will have 3xHC-SR04 Ultrasonic Module on the sides and in the front that detect obstacles,also an IR Module to avoid falling down the stairs.The robot will be powered by a 7.4V Lithium-Ion Battery.Because the battery is too powerful we will use a voltage regulator to convert it to 5V.We switch the button to ON and the vacuum will start working after we cut the connection from the internal battery and power it from our power supply.For the motor driver, we connect the two enable pins to 5V and also the driver voltage pin to 5V because we are using 5V motors.

{{:pm:prj2022:agmocanu:screenshot_773_.png?800|}}


===== Hardware Design =====

**List of components:**
  * Arduino Micro
  * HC-SR04 Ultrasonic Module x3
  * L293D Motor Driver 
  * 5Volt N20 Motors x2
  * N20 Motor Wheels x2
  * Switch 
  * LM7805 Voltage Regulator 
  * 7.4V Lithium-Ion Battery 
  * IR Module 
  * Perfboard 
  * Castor Wheel 
  * Plastic Board
  * Generic Portable Vacuum Cleaner 
  * 1.5V Battery x2

**Electric scheme:**

{{:pm:prj2022:agmocanu:scheme.png?600 |}}
=====   Software Design   =====

I used Arduino IDE to write and upload the code.

**Defining the pins:**

  const int trigPin1 = 3;
  const int echoPin1 = 5;
  const int trigPin2 = 6;
  const int echoPin2 = 9;
  const int trigPin3 = 10;
  const int echoPin3 = 16;
  int irpin =2;
   
**Defining the variables:**


  long duration1;
  long duration2;
  long duration3;
  int distanceleft;
  int distancefront;
  int distanceright;
  int a=0;
  #define in1 4
  #define in2 7
  #define in3 8
  #define in4 14  
    
**This section is used to move forward and backward:**

  if(s==LOW)
  { 
    digitalWrite(4, LOW);
    digitalWrite(7, HIGH);
    digitalWrite(8, LOW);
    digitalWrite(14, HIGH);
    delay(1000);
    a=1;
        }

If it detects the abscence of the floor the robot will not move forward and it will turn around :

    if ((a==0)&&(s==HIGH)&&(distanceleft <= 15 && distancefront > 15 && distanceright <= 15) || (a==0)&&(s==HIGH)&&(distanceleft > 15 && distancefront > 15 && distanceright > 15))
**This section is used to move right:**

    digitalWrite(4, LOW);
    digitalWrite(7, HIGH);
    digitalWrite(8, LOW);
    digitalWrite(14, HIGH);
    delay(1000);
    a=1;

   if ((a==1) &&(s==HIGH) ||(s==HIGH) && (distanceleft <= 15 && distancefront <= 15 && distanceright > 15) || (s== HIGH) && (distanceleft <= 15 && distancefront <= 15 && distanceright > 15) || (s==HIGH) && (distanceleft <= 15 && distancefront > 15 && distanceright > 15) || (distanceleft <= 15 && distancefront > 15 && distanceright > 15))
  
  {
    digitalWrite(4, HIGH);
    digitalWrite(7, LOW);
    digitalWrite(8, LOW);
    digitalWrite(14, HIGH);
    delay(100);
    a=0;
  }
  
**This section is used to move left:**

   if ((s==HIGH)&&(distanceleft > 15 && distancefront <= 15 && distanceright <= 15) ||(s==HIGH)&& (distanceleft > 15 && distancefront > 15 && distanceright <= 15) ||(s==HIGH)&& (distanceleft > 15 && distancefront <= 15 && distanceright > 15) )
  
    {
    digitalWrite(4, LOW);
    digitalWrite(7, HIGH);
    digitalWrite(8, HIGH);
    digitalWrite(14, LOW);
  }
===== Rezultate Obţinute =====

{{:pm:prj2022:agmocanu:8e95dd60-b363-4607-ac94-cc64d884a5ed.jpg?500|}}
{{:pm:prj2022:agmocanu:50eecb7e-d8ab-43a8-bd69-f4ee3f8738d1.jpg?300|}}

===== Concluzii =====
Building a robot is not easy and you need to pay a lot of attention to details,to do your research properly and have patience because it doesn't work perfectly from the beggining.I wanted to create something useful,something that I would enjoy using at home and something that would make me proud.I think it is complicated when you are starting but after a while,all that hard work pays off.
===== Download =====
[[https://github.com/DenisaVoicu/floorcleaningrobot.ino/blob/main/arduino-vacuum-cleaner.ino]]

===== Jurnal =====
  * 21/April/2022 Project Theme and Idea
  * 11/May/2022 finished Milestone 1
  * 27/May/2022 finished Milestone 2
  * 01/June/2022 Made a few changes
===== Bibliografie/Resurse =====
  * ''https://components101.com/sensors/ir-sensor-module''
  * ''https://www.electroschematics.com/hc-sr04-datasheet/''
  * ''https://components101.com/ics/7805-voltage-regulator-ic-pinout-datasheet''
  * ''https://lastminuteengineers.com/l293d-dc-motor-arduino-tutorial/''
  * ''https://www.youtube.com/watch?v=JlrvP6vElCk''
  * ''https://www.youtube.com/watch?v=bSuWnjCqjf8''

<html><a class="media mediafile mf_pdf" href="?do=export_pdf">Export to PDF</a></html>
