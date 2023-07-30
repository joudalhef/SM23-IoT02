# Introduction
The TASK is How to connect more than one microcontroller with each other to transfer data and send data from one microcontroller and receive it from another one                  (via a button thats controls the LED) .
# Used by
[tinkercad](https://www.tinkercad.com/things/hGAZohs4LpK-incredible-vihelmo/editel?tenant=circuits)
# Components
1- Arduino Uno R3 (2)

2- Blue LED (1)

3- Pushbutton (1)

4- 220 Ω Resistor (2)
# Circuit
![Incredible Vihelmo](https://github.com/joudalhef/SM23-IoT02/assets/139080884/a3959eea-eebf-4c35-b15f-3ec645eaec40)
# Start similation
https://github.com/joudalhef/SM23-IoT02/assets/139080884/c9ad2930-8091-47e3-bd9e-b7c924a7f206
# Code Arduino Uno R3 (1)
#include <Wire.h>

int pushButton = A0;

int x = 0;

void setup()

{

  Wire.begin();
  
  pinMode(pushButton, INPUT);
  
}

void loop()

{

   Wire.beginTransmission(1);
   
   x = digitalRead(pushButton);
   
   Wire.write(x);
   # Code Arduino Uno R3 (2)
   #include <Wire.h>
   
int pinLed=13;

int x =0;

void setup()

{
  Wire.begin(1);
  
  Wire.onReceive(receiveEvent); 
  
  pinMode(pinLed, OUTPUT);
  
}

void loop()

{
  delay(100);
  
}

void receiveEvent(int howMany){

x = Wire.read();
  
  if (x == 1){
  
        digitalWrite(pinLed,HIGH);
  }
  
  else{
  
        digitalWrite(pinLed,LOW);
  }
  
}
   
   Wire.endTransmission();
   
   delay(500);
}



