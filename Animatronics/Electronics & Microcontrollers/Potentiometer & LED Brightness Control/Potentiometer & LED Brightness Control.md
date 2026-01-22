Lesson 2: Potentiometer & LED Brightness Control
--------------------------------------------------------------

### 1. Introduction

Ask the question: *"How can we control the brightness of an LED, not just turn it on or off?"* Explain that real-world devices don't work with just two states—they need to vary their output based on input. Today, we learn about **analog signals** and how to read sensors like a potentiometer to create dynamic control.

### 2. Setup

Ensure everyone still has their **VS Code** and **PlatformIO** project open.

-   **Target Board:** Arduino Mega 2560 (from the ELEGOO Mega R3 Ultimate Kit.)

-   **Analog vs. Digital:** Explain the difference:

    -   **Digital:** Only two states: HIGH (1) or LOW (0)—like a light switch.

    -   **Analog:** Continuous range of values (0-1023 on the Mega 2560)—like a volume knob.

-   **Pulse Width Modulation (PWM):** Explain that the Arduino uses PWM to simulate analog output on digital pins. The faster it switches on/off, the brighter the LED appears.

### 3. The Coding Activity

Replace the code in `src\main.cpp` with the following. Type it out to build muscle memory:

```C++
#include <Arduino.h>

int potPin = A0;      // Potentiometer connected to analog pin A0
int ledPin = 9;       // LED connected to PWM pin 9

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
  Serial.println("--- POTENTIOMETER & LED CONTROL ---");
  Serial.println("Turn the potentiometer knob to control LED brightness");
}

void loop() {
  // Read the analog value (0-1023)
  int potValue = analogRead(potPin);
  
  // Convert to LED brightness (0-255)
  int brightness = map(potValue, 0, 1023, 0, 255);
  
  // Set the LED brightness
  analogWrite(ledPin, brightness);
  
  // Print to Serial Monitor to see the values
  Serial.print("Pot Value: ");
  Serial.print(potValue);
  Serial.print(" | Brightness: ");
  Serial.println(brightness);
  
  delay(500); // Update every 500ms
}

```

Experiment by:
- Changing the delay values
- Turning the potentiometer and watching the output
- Modifying the map range to see how it affects brightness

### 4. Hardware Connection

**Parts needed:**
- Board and Breadboard
- 1 Potentiometer (10kΩ)
- 1 LED
- 1 100Ω or 220Ω resistor
- 5 wires

**Wiring:**
-   **Potentiometer:**
    -   Left pin → 5V
    -   Middle pin → A0 (analog pin)
    -   Right pin → GND

-   **LED:**
    -   Long leg (anode) → Pin 9 (PWM pin) with 100Ω resistor in series
    -   Short leg (cathode) → GND

**Breadboard Schematic (Single LED Setup) — with breadboard positions:**

```
Arduino Mega 2560 header                Breadboard (rows 1..30, cols a..j)
------------------------                ----------------------------------
 5V  (J1) ----------------------------> + rail (row 1, cols a-j)
 GND (J2) ----------------------------> - rail (row 30, cols a-j)
 A0  (J3) ----------------------------> Pot middle (row 10, col e)
 D9  (J4) ----------------------------> Resistor end (row 15, col e)

Breadboard component placement (example rows/cols):
 - Potentiometer (3-pin) placed so pins occupy row 10 cols d,e,f
    - Left pin  -> row10 col d  (wire to + rail / 5V)
    - Middle pin-> row10 col e  (wire to Arduino A0)
    - Right pin -> row10 col f  (wire to - rail / GND)

 - LED + Resistor chain placed at row 15:
    - Resistor (100Ω) one end -> row15 col e (wire from D9)
    - Resistor other end -> row15 col f (LED anode)
    - LED cathode -> row15 col g (wire to GND rail)

Wiring summary (explicit jumpers):
 - Jumper: Arduino 5V -> Breadboard + rail (row1 col a)
 - Jumper: Arduino GND -> Breadboard - rail (row30 col a)
 - Jumper: Arduino A0 -> Breadboard row10 col e (pot middle)
 - Jumper: Arduino D9 -> Breadboard row15 col e (resistor)
 - Jumper: Breadboard row30 (GND rail) -> Breadboard row15 col g (LED cathode)

Notes:
 - Use the indicated rows/cols as a consistent classroom example; students may place components on nearby rows but should keep connections consistent.
 - On many breadboards the left/right power rails run the length; use the same labeled row for clarity.
```

-   Click **Build** then **Upload and Monitor** in the PlatformIO pane.

* * * * *

🔍 Key Teaching Points (The "Why")
----------------------------------

-   **Analog vs. Digital:** Digital pins are binary (on/off). Analog pins can measure a range of values, giving us "shades" of control instead of just on/off.

-   **The `analogRead()` Function:** Reads the voltage on an analog pin and returns a value from 0 to 1023 (for 10-bit resolution).

-   **The `map()` Function:** Converts one range of numbers to another. We use it to convert the pot's 0-1023 value to the LED's 0-255 brightness range.

-   **PWM (Pulse Width Modulation):** The Arduino rapidly switches the pin on and off. The longer it's "on," the brighter the LED. This creates the illusion of varying brightness on a digital pin.

-   **Why Pin 9?** Not all pins support PWM. On the Mega 2560, look for pins marked with ~ (like 9, 10, etc.).

* * * * *

📺 Recommended Class Resource
-----------------------------

-   **[Understanding Analog Input on Arduino](https://youtu.be/BMMnOAzcqoE?si=1yGkaIRhWmqqCtSA)**

    -   **Classroom Use:** Play the first 4 minutes to show how potentiometers work and what the Serial Monitor should display.

-   **[Pulse Width Modulation (PWM) - Electronics Basics 23](https://youtu.be/GQLED3gmONg?si=Fi3Is3n1VJyJlO1U)**

    -   **Classroom Use:** Play this to help students understand why PWM makes the LED appear to have different brightness levels.

🔨 Exercise
------------------------------

**Parts needed**
  - Board and Breadboard
  - 1 Potentiometer (10kΩ)
  - 2 LEDs (different colors if available)
  - 2 resistors (100Ω or 220Ω each)
  - 7 wires

**Breadboard Schematic (Dual LED Setup) — with breadboard positions:**

```
Arduino Mega 2560 header                Breadboard (rows 1..30, cols a..j)
------------------------                ----------------------------------
 5V  (J1) ----------------------------> + rail (row 1, cols a-j)
 GND (J2) ----------------------------> - rail (row 30, cols a-j)
 A0  (J3) ----------------------------> Pot middle (row 10, col e)
 D9  (J4) ----------------------------> Resistor1 end (row 15, col e)
 D10 (J5) ----------------------------> Resistor2 end (row 17, col e)

Breadboard component placement (example rows/cols):
 - Potentiometer placed so pins occupy row 10 cols d,e,f
    - Left pin  -> row10 col d  (wire to + rail / 5V)
    - Middle pin-> row10 col e  (wire to Arduino A0)
    - Right pin -> row10 col f  (wire to - rail / GND)

 - Red LED + Resistor chain at row 15:
    - Resistor1 one end -> row15 col e (wire from D9)
    - Resistor1 other end -> row15 col f (Red LED anode)
    - Red LED cathode -> row15 col g (wire to GND rail)

 - Green LED + Resistor chain at row 17:
    - Resistor2 one end -> row17 col e (wire from D10)
    - Resistor2 other end -> row17 col f (Green LED anode)
    - Green LED cathode -> row17 col g (wire to GND rail)

Wiring summary (explicit jumpers):
 - Jumper: Arduino 5V -> Breadboard + rail (row1 col a)
 - Jumper: Arduino GND -> Breadboard - rail (row30 col a)
 - Jumper: Arduino A0 -> Breadboard row10 col e (pot middle)
 - Jumper: Arduino D9 -> Breadboard row15 col e (resistor1)
 - Jumper: Arduino D10 -> Breadboard row17 col e (resistor2)
 - Jumper: Breadboard row30 (GND rail) -> Breadboard row15 col g (LED cathodes)

Notes:
 - Use the indicated rows/cols as a consistent classroom example; students may place components on nearby rows but should keep connections consistent.
 - On many breadboards the left/right power rails run the length; use the same labeled row for clarity.
```

**Code Challenge:**
```C++
#include <Arduino.h>

int potPin = A0;       // Potentiometer
int redLedPin = 9;     // First LED (PWM pin)
int greenLedPin = 10;  // Second LED (PWM pin)

void setup() {
  Serial.begin(9600);
  pinMode(redLedPin, OUTPUT);
  pinMode(greenLedPin, OUTPUT);
  Serial.println("--- DUAL LED BRIGHTNESS CONTROL ---");
}

void loop() {
  int potValue = analogRead(potPin);
  int brightness = map(potValue, 0, 1023, 0, 255);
  
  // Make the red LED brighter as pot increases
  analogWrite(redLedPin, brightness);
  
  // Make the green LED brighter as pot decreases (inverse)
  analogWrite(greenLedPin, 255 - brightness);
  
  Serial.print("Red: ");
  Serial.print(brightness);
  Serial.print(" | Green: ");
  Serial.println(255 - brightness);
  
  delay(500);
}

```

**Test & Explore:**
- Turn the potentiometer slowly and watch both LEDs change
- Can you see how the red LED gets brighter while the green gets dimmer?
- What happens if you change the map range values?
- Add a third LED connected to another PWM pin and control its brightness independently

**Challenge:** Modify the code to make one LED pulse while the other stays at a fixed brightness based on the potentiometer value.
