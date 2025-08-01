#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
int tempPin = A0;

void setup() {
  lcd.begin(16, 2);
  lcd.print("Temp: ");
  Serial.begin(9600);  // ✅ Start Serial Monitor
}

void loop() {
  int reading = analogRead(tempPin);
  float voltage = reading * 5.0 / 1024.0;
  float tempC = voltage * 100;

  // Display on LCD
  lcd.setCursor(6, 0);
  lcd.print("     ");
  lcd.setCursor(6, 0);
  lcd.print(tempC);
  lcd.print((char)223);
  lcd.print("C");

  // ✅ Display on Serial Monitor
  Serial.print("Temperature: ");
  Serial.print(tempC);
  Serial.println(" °C");

  delay(1000);
}
