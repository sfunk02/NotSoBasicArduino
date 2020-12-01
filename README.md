# NotSoBasicArduino Journal

## Sam Funk

---
## Table of Contents
* [Hello Functions](#HelloFunctions)
* [NewPing](#NewPing)
* [LedBlinkRevisited](#LedBlinkRevisited)
* [FiniteLedBlink](#FiniteLedBlink)

## HelloFunctions

### Description



### Evidence



### Image



### Reflection

While completing this assignment I learned how to:
* 

---

## NewPing

### Description



### Evidence



### Image



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


### Reflection

While completing this assignment I learned how to:
* use variables
* code something to happen a set number of times

---
