# Arduino-LED-Cloud
#LED Strip Controller with IR Remote
This project controls a WS2811 LED strip using an IR remote. It features various lighting modes that can be activated via specific buttons on the remote.
The project utilizes the FastLED library for LED control and the IRremote library for IR remote communication.

Components:
WS2811 LED Strip
Arduino (or compatible microcontroller)
IR Remote
IR Receiver
Power supply for LED strip
Connecting wires
Libraries
FastLED
IRremote

Circuit Diagram:
Connect the LED strip data pin to pin 13 on the Arduino.
Connect the IR receiver output pin to pin 3 on the Arduino.
Connect the power supply to the LED strip and Arduino appropriately.
Code Description

Constants:
LED_PIN: Pin number connected to the LED strip data line.
NUM_LEDS: Number of LEDs in the strip.
COLOR_ORDER: Color order of the LEDs (GRB for WS2811).
LED_TYPE: Type of LED strip (WS2811).
MAX_BRIGHTNESS: Maximum brightness for the LEDs.
IR Remote
IRrecv IR(3): Initializes the IR receiver on pin 3.
mapIRValue(unsigned long irValue): Maps the IR value received to a corresponding mode.

Functions:
BlueLightningMode: Displays a blue lightning effect.
PinkLightningMode: Displays a pink lightning effect.
PurpleLightningMode: Displays a purple lightning effect.
BlueTransitionMode: Gradually transitions LEDs to blue.
PinkTransitionMode: Gradually transitions LEDs to pink.
PurpleTransitionMode: Gradually transitions LEDs to purple.
RainbowMode(uint8_t startingHue): Displays a rainbow effect.
CottonCandyMode: Displays an alternating blue and pink effect.
NightLightMode: Sets LEDs to a soft night light color.

Setup:
void setup() {
  IR.enableIRIn();
  Serial.begin(9600); 

  delay(3000);
  LEDS.addLeds<LED_TYPE, LED_PIN, COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);
  FastLED.setBrightness(MAX_BRIGHTNESS);
}
- Initializes the IR receiver.
- Sets up the LED strip with the specified parameters.

LOOP:
int mapIRValue(unsigned long irValue) {
  if (irValue == 0xBA45FF00) return 0;
  if (irValue == 0xF30CFF00) return 1;
  if (irValue == 0xE718FF00) return 2;
  if (irValue == 0xA15EFF00) return 3;
  if (irValue == 0xF708FF00) return 4;
  if (irValue == 0xE31CFF00) return 5;
  if (irValue == 0xA55AFF00) return 6;
  if (irValue == 0xBD42FF00) return 7;
  if (irValue == 0xAD52FF00) return 8;
  if (irValue == 0xB54AFF00) return 9;
  return random(1, 9);
}
-Continuously checks for IR signals.
-Maps the received IR value to a specific mode.
-Executes the corresponding mode function.

IR Value Mapping:
int mapIRValue(unsigned long irValue) {
  if (irValue == 0xBA45FF00) return 0;
  if (irValue == 0xF30CFF00) return 1;
  if (irValue == 0xE718FF00) return 2;
  if (irValue == 0xA15EFF00) return 3;
  if (irValue == 0xF708FF00) return 4;
  if (irValue == 0xE31CFF00) return 5;
  if (irValue == 0xA55AFF00) return 6;
  if (irValue == 0xBD42FF00) return 7;
  if (irValue == 0xAD52FF00) return 8;
  if (irValue == 0xB54AFF00) return 9;
  return random(1, 9);
}
-Maps specific IR values to mode indices.

Usage
1. Upload the code to your Arduino.
2. Connect the LED strip and IR receiver as per the circuit diagram.
3. Use the IR remote to switch between different lighting modes.

Remote Control
Button 0: Turn off LEDs
Button 1: Blue lightning mode
Button 2: Pink lightning mode
Button 3: Purple lightning mode
Button 4: Transition to Blue
Button 5: Transition to Pink
Button 6: Transition to Purple
Button 7: Rainbow mode
Button 8: Cotton Candy mode
Button 9: Night light mode

Troubleshooting
1. Ensure the IR receiver is connected correctly.
2. Verify the LED strip connections and power supply.
3. Check if the correct IR values are mapped in mapIRValue.
4. check the configuration of the LEDs RGB GRB etc..
