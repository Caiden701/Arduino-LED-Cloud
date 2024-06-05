#include <FastLED.h> //LED library for LED strip 
#include <IRremote.h> //IR library for remote
 
#define LED_PIN 13                           // LED PIN 
#define NUM_LEDS 45                          // number of LEDs
#define COLOR_ORDER GRB                      //LED order
#define LED_TYPE WS2811                      // LED type
#define MAX_BRIGHTNESS 200                   // watch the power!

IRrecv IR(3); //IR receive Pin

CRGB leds[NUM_LEDS]; //intialize leds 

int mapIRValue(unsigned long irValue);  //map ir recieved values 

//function prototypes
void BlueLightningMode(void); 
void PinkLightningMode(void);
void PurpleLightningMode(void);
void BlueTransitionMode(void);
void PinkTransitionMode(void);
void PurpleTransitionMode(void);
void RainbowMode(uint8_t startingHue);
void CottonCandyMode(void);
void NightLightMode(void); 


void setup() {
  //setup remote
  IR.enableIRIn();
  Serial.begin(9600); 

  //setup LEDs
  delay(3000);
  LEDS.addLeds<LED_TYPE, LED_PIN, COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);
  FastLED.setBrightness(MAX_BRIGHTNESS);
}


void loop() 
{
  if(IR.decode()){
  IR.decodedIRData.decodedRawData;
  unsigned long irValue = IR.decodedIRData.decodedRawData;
  Serial.println(IR.decodedIRData.decodedRawData, HEX); 
  delay(1500);

   int range = mapIRValue(irValue);

  // do something different depending on the range value:
  switch (range) {
     case 0:  // Turn off LED 
    FastLED.clear();
    FastLED.show();
     break;

     case 1: //blue lightning mode
    BlueLightningMode(); 
     break;

     case 2: 
    PinkLightningMode();
     break;

     case 3: 
    PurpleLightningMode();
     break;

     case 4: 
    BlueTransitionMode();
     break;

     case 5:
    PinkTransitionMode();
     break;
     
     case 6:
    PurpleTransitionMode();
     break;

     case 7:
    RainbowMode(random(255));
     break;

     case 8:
    CottonCandyMode();
     break;

     case 9:
    NightLightMode();
     break;
  }
  IR.resume();
  }
}

int mapIRValue(unsigned long irValue) {
  // Use conditional statements to map IR values to the desired range
  if (irValue == 0xBA45FF00) {   
    // Button 0 turn off all LEDS
    return 0;
  } else if (irValue == 0xF30CFF00) { 
    // Button 1 Blue lightning mode
    return 1; } 
    else if (irValue == 0xE718FF00) { 
    // Button 2 Pink lightning mode
    return 2;}
     else if (irValue == 0xA15EFF00){                             
    // Button 3 Purple lightning mode
    return 3;} 
    else if (irValue == 0xF708FF00){
    // Button 4 Transition into Blue
    return 4;}
    else if (irValue == 0xE31CFF00){
    // Button 5 Transition into Pink
    return 5;}
    else if (irValue == 0xA55AFF00){
    //Button 6 transition into Purple
    return 6;}
    else if (irValue == 0xBD42FF00){
    // Button 7 rainbow mode
    return 7;}
    else if (irValue == 0xAD52FF00){
    // Button 8 cotton candy mode
    return 8;}
    else if (irValue == 0xB54AFF00){
    // Button 9 Night light mode 
    return 9;}
    else {

    return random(1,9); // Indicate an unknown or unsupported value
  }
}

// mode functions
// Blue lightning mode function 
void BlueLightningMode(){
  for (int flash = 0; flash < 5; flash++) {  // Repeat the lightning effect 10 times
    fill_solid(leds, NUM_LEDS, CRGB::White);  // Turn off all LEDs
    FastLED.show();
    delay(random(25, 75));  // Random delay before the next lightning flash

    // Light up all LEDs briefly before individual flashes
    fill_solid(leds, NUM_LEDS, CRGB(50, 100, 150));
    FastLED.show();
    delay(100);

    // Shuffle the order of LEDs for random flashes
    for (int i = 0; i < NUM_LEDS; i++) {
      int randomIndex = random(NUM_LEDS);
      leds[randomIndex] = CRGB::Blue;  // Turn off the current LED
      FastLED.show();
      delay(100);  // Duration for each individual LED to be lit
    }
  }
}
  // Pink lightning mode function 
void PinkLightningMode(){
  for (int flash = 0; flash < 5; flash++) {  // Repeat the lightning effect 10 times
    fill_solid(leds, NUM_LEDS, CRGB::White);  // Turn off all LEDs
    FastLED.show();
    delay(random(25, 75));  // Random delay before the next lightning flash

    // Light up all LEDs briefly before individual flashes
    fill_solid(leds, NUM_LEDS, CRGB::Plum); //light pink 
    FastLED.show();
    delay(100);

    // Shuffle the order of LEDs for random flashes
    for (int i = 0; i < NUM_LEDS; i++) {
      int randomIndex = random(NUM_LEDS);
      leds[randomIndex] = CRGB(150, 0, 75);;  // dark pink
      FastLED.show();
      delay(100);  // Duration for each individual LED to be lit
    }
  }
}
  // Purple lightning mode function 
void PurpleLightningMode(){
  for (int flash = 0; flash < 5; flash++) {  // Repeat the lightning effect 10 times
    fill_solid(leds, NUM_LEDS, CRGB::White);  // Turn off all LEDs
    FastLED.show();
    delay(random(25, 75));  // Random delay before the next lightning flash

    // Light up all LEDs briefly before individual flashes
    fill_solid(leds, NUM_LEDS, CRGB::Purple); // purple
    FastLED.show();
    delay(100);

    // Shuffle the order of LEDs for random flashes
    for (int i = 0; i < NUM_LEDS; i++) {
      int randomIndex = random(NUM_LEDS);
      leds[randomIndex] = CRGB(80, 0, 100);  // dark purple
      FastLED.show();
      delay(100);  // Duration for each individual LED to be lit
    }
  }
}
  // Blue transition mode function
  void BlueTransitionMode(){
    for (int i=0; i<NUM_LEDS  ; i++)
   {
     leds[i] = CRGB::Blue;
     FastLED.show();
     FastLED.setBrightness(100);
    delay(300);
   }
  }
  
  // Pink transition mode function
  void PinkTransitionMode(){
    for (int i=0; i<NUM_LEDS  ; i++)
   {
     leds[i] = CRGB(150, 0, 75);
     FastLED.show();
     FastLED.setBrightness(100);
    delay(300);
   }
  }
  
  // Purple transition mode function
  void PurpleTransitionMode(){
    for (int i=0; i<NUM_LEDS  ; i++)
   {
     leds[i] = CRGB(80, 0, 100); //dark purple
     FastLED.show();
     FastLED.setBrightness(100);
    delay(300);
   }
  }
  
  //rainbow mode function
  void RainbowMode(uint8_t startingHue){
  static uint8_t hue = startingHue;
  fill_rainbow(leds, NUM_LEDS, hue, 7);
  FastLED.show();
  hue += 50;  // Adjust the increment value for the speed of color transition
  }

  //Cotton Candy Mode
  void CottonCandyMode(){
    for (int i = 0; i < NUM_LEDS; i++) {
  int randomIndex = random(NUM_LEDS);

  if (i % 2 == 0) {
    leds[randomIndex] = CRGB(150, 0, 75); //dark pnk
  } else {
    leds[randomIndex] = CRGB::Blue;  // Turn on the current LED with blue color
  }

  FastLED.show();
  delay(100);  // Duration for each individual LED to be lit
}

  }
  
  //night light mode
  void NightLightMode(){
    //Set all LEDs to a specific color
     fill_solid(leds, NUM_LEDS, CRGB(135, 150, 135));
    // Send the data to the LEDs to update the colors
     FastLED.show();
     delay(1000);
  }

