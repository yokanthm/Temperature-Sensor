🌡️ Arduino Temperature Monitor using LCD & LM35 Sensor
This project reads the ambient temperature using an LM35 temperature sensor, converts the analog reading to Celsius, and displays the result on a 16x2 LCD screen. It also prints the temperature to the Serial Monitor.

🔧 Components Used:
Component	Quantity
Arduino Uno R3	1
LM35 Temperature Sensor	1
16x2 LCD Display	1
10kΩ Potentiometer	1
Jumper Wires	As needed
Breadboard (optional)	1

🔌 Circuit Connections:
🔹 LM35 Sensor:
LM35 Pin	Connected To
VCC	5V
GND	GND
OUT	A0

🔹 16x2 LCD:
LCD Pin	Arduino Pin
RS	12
E	11
D4	5
D5	4
D6	3
D7	2
VSS	GND
VDD	5V
VO	Center pin of 10k Potentiometer
RW	GND
A (Backlight +)	5V
K (Backlight -)	GND

🔹 Potentiometer (for LCD contrast):
One end to 5V

Other end to GND

Middle pin (wiper) to VO (Pin 3 of LCD)

🧾 Arduino Code Explanation:
cpp
Copy
Edit
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);  // RS, E, D4-D7
int tempPin = A0;  // Analog input for LM35

void setup() {
    lcd.begin(16, 2);
    lcd.print("Temp: ");
    Serial.begin(9600);  // For serial output
}

void loop() {
    int reading = analogRead(tempPin);        // Read analog voltage
    float voltage = reading * 5.0 / 1024.0;    // Convert to voltage
    float tempC = voltage * 100;              // Convert voltage to °C

    lcd.setCursor(6, 0);                      // Position to print temp
    lcd.print(tempC);                         // Display temperature
    lcd.print(" \337C");                      // Display °C symbol (ASCII 223)

    Serial.print("Temperature: ");
    Serial.print(tempC);
    Serial.println(" °C");

    delay(1000); // Update every second
}
📟 Output:
LCD Display:

makefile
Copy
Edit
Temp: 74.71 °C
Serial Monitor:

makefile
Copy
Edit
Temperature: 74.71 °C
🧠 Learning Outcomes:
Use of analog sensors with Arduino.

Displaying data on an LCD screen.

Serial communication for debugging.

Voltage to temperature conversion.
