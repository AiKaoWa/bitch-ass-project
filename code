const int ldrPin = A4;
const int buzzerPin = 6;
const int pirPin = 8;

const int LDR_LIGHT_THRESHOLD = 500;

const int ALARM_DURATION = 1000;
const int ALARM_DELAY = 1000;

void setup() {
  Serial.begin(9600);
  pinMode(buzzerPin, OUTPUT);
  pinMode(pirPin, INPUT);

  Serial.println("system initialized");
}

void loop() {

  int ldrValue = analogRead(ldrPin);
  int pirStatus = digitalRead(pirPin);

  bool isLightPresent = (ldrValue < LDR_LIGHT_THRESHOLD);
  bool isNoMovement = (pirStatus == LOW);

  Serial.println("----- SENSOR READINGS -----");

  Serial.print("LDR Value: ");
  Serial.print(ldrValue);
  Serial.print("  |  ");

  Serial.print("Light Status: ");
  Serial.println(isLightPresent ? "BRIGHT" : "DARK");

  Serial.print("PIR Status: ");
  Serial.print(pirStatus);
  Serial.print("  |  ");
  Serial.println(pirStatus == HIGH ? "MOTION DETECTED" : "NO MOVEMENT");

  if (isLightPresent && isNoMovement) {
    Serial.println("⚠ ALERT: Light ON + No Movement!");
    tone(buzzerPin, 1000, ALARM_DURATION);
    delay(ALARM_DURATION + ALARM_DELAY); 
  } else {
    Serial.println("OK: Conditions Normal.");
    noTone(buzzerPin);
    delay(1000);
  }
  Serial.println("----------------------------\n");
}
