# Automatic-Irrigation-System
int soilMoistureSensor = A0; // Soil moisture sensor connected to A0
int relay = 7;               // Relay connected to digital pin 7
int threshold = 300;         // Threshold value for soil moisture

void setup() {
  pinMode(soilMoistureSensor, INPUT); // Set soil moisture sensor pin as input
  pinMode(relay, OUTPUT);             // Set relay pin as output
  Serial.begin(9600);                 // Start serial communication at 9600 baud
}

void loop() {
  int sensorValue = analogRead(soilMoistureSensor); // Read the value from the soil moisture sensor
  Serial.print("Soil Moisture: ");
  Serial.println(sensorValue); // Print the soil moisture value to the serial monitor

  if (sensorValue < threshold) {
    digitalWrite(relay, LOW);  // Turn on the water pump
    Serial.println("Pump ON");
  } else {
    digitalWrite(relay, HIGH); // Turn off the water pump
    Serial.println("Pump OFF");
  }
  delay(1000); // Wait for 1 second before taking the next reading
}
