🏫 Day 1: The Robot's Voice (Serial Communication)
--------------------------------------------------

### 1\. The Hook (5 Minutes)

Ask the class: *"How do we know what a robot is thinking?"* Explain that unlike a computer screen, a microcontroller like the **Mega 2560** is "blind" and "silent" unless we give it a way to talk to us. Today, we build that bridge.

### 2\. The Setup (15 Minutes)

Have everyone open **VS Code** and initialize their first **PlatformIO** project.

-   **Target Board:** Arduino Mega 2560 (from the ELEGOO Mega R3 Ultimate Kit.

-   **The Anatomy of a Script:** Explain the two "rooms" of a C++ script:

    -   `void setup()`: Runs **once** (like waking up in the morning).

    -   `void loop()`: Runs **forever** (like breathing or a heart beating).

### 3\. The Coding Activity (20 Minutes)

Have students type the following into their `main.cpp`. Avoid copy-pasting so they build "muscle memory" for syntax like semicolons.

C++

```
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

### 4\. Hardware Connection (10 Minutes)

-   Connect the **USB Cable** to the ELEGOO Mega R3 Board.

-   Click the **Upload (→)** arrow in the blue VS Code status bar.

-   Click the **Serial Monitor (Plug icon)**.

* * * * *

🔍 Key Teaching Points (The "Why")
----------------------------------

-   **The Baud Rate (9600):** Explain this is the "speed" of the conversation. If the computer and the board aren't at the same speed, you get gibberish text (aliens talking).

-   **The Semicolon ( ; ):** In C++, the semicolon is the "period" at the end of a sentence. Without it, the "brain" gets confused.

-   **The Delay:** Explain that microcontrollers are *too* fast. Without `delay()`, the robot would scream "I am waiting" thousands of times per second, crashing the Serial Monitor.

* * * * *

📺 Recommended Class Resource
-----------------------------

-   **[How to use the Arduino Serial Monitor](https://www.google.com/search?q=https://www.youtube.com/watch%3Fv%3DgM6uO6s82H4)**

    -   **Classroom Use:** Play the first 3 minutes of this video to show students what the "output" should look like once they hit upload.

* * * * *

✅ Day 1 Learning Check
----------------------

Before they leave, every student should be able to:

1.  Identify the **USB-B port** on their Mega board.

2.  Change the text in `Serial.println` to their own custom "Robot Name."

3.  Successfuly **Upload** and see that name appearing on their screen.