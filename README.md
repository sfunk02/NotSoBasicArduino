# NotSoBasicArduino Journal

## Sam Funk

---
## Table of Contents
* [Hello Functions](#HelloFunctions)
* [NewPing](#NewPing)
* [LedBlinkRevisited](#LedBlinkRevisited)
* [FiniteLedBlink](#FiniteLedBlink)
* [Photoresistor](#Photoresistor)

## HelloFunctions

### Description

For this assignment, I had to code an ultrasonic sensor so that it would detect distance and display it in the serial monitor. Then I had to code a continuous servo to spin at a speed based on the distance detected by the ultrasonic sensor. The servo spins one way from 0-45cm and the other way from 45cm-90cm.

### Code

```C++
/*
Sam Funk
HC-SRO4 and Continuous Servo - servo speed changes based on distance measured
12/18/20
*/

const int out=13;
const int in=12;
#include <Servo.h>
Servo myservo;

void setup() {
Serial.begin(9600);
pinMode(in, INPUT);
pinMode(out, OUTPUT);
myservo.attach(9);
}

void loop() {
long dur;
long dis;
long tocm;
digitalWrite(out, LOW);
delayMicroseconds(2);
digitalWrite(out, HIGH);
delayMicroseconds(10);
digitalWrite(out, LOW);
dur=pulseIn(in, HIGH);
tocm=microsecondsToCentimeters(dur);
Serial.println(String(tocm));
delay(100);
myservo.write(tocm*2);
}
long microsecondsToCentimeters(long microseconds)
{
return microseconds / 29 / 2;
}
```

### Reflection

While completing this assignment I learned how to:
* use functions
* code an ultrasonic sensor
* code a continuous servo

---

## NewPing

### Description

For this assignment, I had to use the NewPing library to code an ultrasonic sensor that detects distance. I made an LED blink based on the distance detected. (closer was faster)

### Code

```C++
/*
Sam Funk
NewPing() - uses NewPing controlled HC-SR04 sensor to blink an LED based on the distance detected.
  (closer is faster)
12/18/20
*/

#include <NewPing.h>

#define TRIGGER_PIN 12
#define ECHO_PIN 11
#define MAX_DISTANCE 200

NewPing myHC_SR04(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE);

void setup() {
  Serial.begin(9600);
  pinMode(9, OUTPUT);
}

void loop() {
  Serial.println(myHC_SR04.ping_cm());
  delay(5);
  digitalWrite(9, HIGH);
  delay(myHC_SR04.ping_cm()*10);
  digitalWrite(9, LOW);
  delay(myHC_SR04.ping_cm()*10);
}
```

### Reflection

While completing this assignment I learned how to:
* 

---

## LedBlinkRevisited

### Description

For this assignment, I had to wire and code an LED to blink on and off at a set rate.

### Code
```C++
/*
Sam Funk
LED Blink Revisited
Blinks an LED at a set rate.
*/

void setup() {
  Serial.begin(9600);
  pinMode(7, OUTPUT);
}

void loop() {
  digitalWrite(7, HIGH);
  delay(500);
  digitalWrite(7, LOW);
  delay(500);
}
```

### Reflection

While completing this assignment I (re)learned how to:
* setup an Arduino
* power a pin
* turn a pin on and off
* wire an LED

---

## FiniteLedBlink

### Description

For this assignment, I used the same wiring as the LED Blink assignment, but altered the code so the LED would only blink 5 times.

### Code
```C++
/*
Sam Funk
November 25, 2020
Finite LED Blinker: blinks an LED a finite number of times, then stops.
*/

int counter = 0;    //This is a variable we will use to count the number of times the LED blinks.
int LED = 7;        //This sets the LED pin on the Arduino
void setup() {
  Serial.begin(9600);
  pinMode(LED, OUTPUT); //Sets the pin to output
}

void loop() {
  if (counter < 5) {      //This only activates if the LED has blinked less than 5 times
    Serial.println(counter);
    digitalWrite(LED, HIGH);  //Turns the LED on
    delay(250);
    digitalWrite(LED, LOW);   //Turns the LED off
    delay(250);
    counter++;              //Adds one to the counter variable
  }
  else if (counter >= 5) {
    digitalWrite(LED, LOW); //After the LED has blinked 5 times, it will turn off
  }
}
```

### Reflection

While completing this assignment I learned how to:
* use variables
* code something to happen a set number of times

---

## Photoresistor

### Description

For this assignment, I had to wire and code a photoresistor so that it would turn on an LED light when light levels in the room decreased. 

### Code

```C++
/*
Sam Funk
Photoresistor- lights up an LED based on how dark the room is
12-17-20
*/

int Photo = A0;
int lightlevel;
int LED = 8;

void setup() {
  pinMode(LED, OUTPUT);
  pinMode(Photo, OUTPUT);
  Serial.begin(9600);
}

void loop() {
lightlevel = analogRead(Photo);
Serial.println(lightlevel);
delay(250);

if (lightlevel < 6) {
  digitalWrite(LED, HIGH);
  
}

else {
  digitalWrite(LED, LOW);
}
}
```

### Reflection

While completing this assignment I learned how to:
* Code a photoresistor
* Use an analog pin to transfer signal strength data

---
