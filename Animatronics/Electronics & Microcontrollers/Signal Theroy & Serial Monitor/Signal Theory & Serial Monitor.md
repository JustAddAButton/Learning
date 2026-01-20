Lesson 1: The Robot's Voice (Serial Communication)
--------------------------------------------------

### 1\. Introduction

Ask the question: *"How do we know what a robot is thinking?"* Explain that unlike a computer screen, a microcontroller like the **Mega 2560** is "blind" and "silent" unless we give it a way to talk to us. Today, we build that bridge.

### 2\. Setup

Have everyone open **VS Code** and initialize their first **PlatformIO** project.

-   **Target Board:** Arduino Mega 2560 (from the ELEGOO Mega R3 Ultimate Kit.)

-   **The Anatomy of a Script:** Explain the two "rooms" of a C++ script:

    -   `void setup()`: Runs **once** (like waking up in the morning).

    -   `void loop()`: Runs **forever** (like breathing or a heart beating).

-   **Install PlatformIO (pip):**
```
   python -m pip install --upgrade pip
   python -m pip install platformio
```

-   **Create a new project for Arduino Mega 2560:**
 - Click the left nave PlatformIO icon and follow steps to creating new project.

### 3\. The Coding Activity

Type the following into their `src\main.cpp`. Avoid copy-pasting to build "muscle memory" for syntax like semicolons.

```C++
#include <Arduino.h>

void setup() {
  // Initialize serial communication at 9600 bits per second
  Serial.begin(9600);
  Serial.println("--- SYSTEM ONLINE ---");
  Serial.println("Initial checks complete...");
}

void loop() {
  Serial.println("The robot is waiting for a command...");
  delay(2000); // Wait 2 seconds so the screen doesn't scroll too fast
}

```

Play with changing the text in Serial.println.

### 4\. Hardware Connection

-   Connect the **USB Cable** to the ELEGOO Mega R3 Board.

-   Expand the PlatformIO pane and click the project tasks in the General folder **Build then Upload and Monitor**.

* * * * *

🔍 Key Teaching Points (The "Why")
----------------------------------

-   **The Baud Rate (9600):** Explain this is the "speed" of the conversation. If the computer and the board aren't at the same speed, you get gibberish text (aliens talking).

-   **The Semicolon ( ; ):** In C++, the semicolon is the "period" at the end of a sentence. Without it, the "brain" gets confused.

-   **The Delay:** Explain that microcontrollers are *too* fast. Without `delay()`, the robot would scream "I am waiting" thousands of times per second, crashing the Serial Monitor.

* * * * *

📺 Recommended Class Resource
-----------------------------

-   **[How to use the Arduino Serial Monitor](https://www.youtube.com/watch?v=j2qrRxQ9mSs)**

    -   **Classroom Use:** Play the first 3 minutes of this video to show students what the "output" should look like once they hit upload.

🔨 Exercise
------------------------------

### Parts needed
  - Board and Breadboard
  - 2 wires
  - 1 LED
  - 1 100Ω resistor

### Code
```C++
#include <Arduino.h>

int redLedPin = 2; // Pin Red LED is connected to
int count = 0;

void setup()
{
	pinMode(redLedPin, OUTPUT); // Set led pin to output
	Serial.begin(9600);			// Set serial to the 9600 band
	while (!Serial); // Allow serial to initialise
	Serial.println("Enter Y to turn on the LED:");
}

void loop()
{
	if (Serial.available())
	{
		char ch = Serial.read();
		if (ch == 'y' || ch == 'Y')
		{
			digitalWrite(redLedPin, HIGH);
			Serial.println("You have turned on the LED!!");
			Serial.print("The LED was off for ");
			Serial.print(count);
			Serial.println(" seconds");
			Serial.println("If you want to switch it off, simply enter N or n!");
			count = 0;
		}
		if (ch == 'n' || ch == 'N')
		{
			digitalWrite(redLedPin, LOW);
			Serial.println("You have turned off the LED!!");
			Serial.print("The LED was on for ");
			Serial.print(count);
			Serial.println(" seconds");
			Serial.println("If you want to switch it on, simply enter Y or y!");
			count = 0;
		}
	}
	delay(1000);
	count += 1;
}

```
### Example
![example](files/example1.jpg)


### Test
- Press Y, Press N to see what happens
- Change values to see how the logic changes
- Understand what the if condition is doing and 