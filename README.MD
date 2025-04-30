Smart IoT Light Scheduler
This project is a web-based application designed for scheduling light control using WebSocket and MQTT technologies. It was developed as part of the Embedded Systems Software Integration course at Rwanda Coding Academy.

Key Features
Responsive and modern interface powered by Tailwind CSS

Real-time scheduling via WebSocket communication

MQTT protocol integration to automate light control

Arduino UNO paired with a relay module for switching lights on/off

Getting Started
1. Arduino Configuration:
Wire the relay module to your Arduino UNO as follows:

VCC ➝ 5V

GND ➝ GND

IN ➝ Digital Pin 8

Ensure proper insulation when connecting the live wire between COM and NO.

Flash the following code onto the Arduino:

int relayPin = 8;

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH); // Start with relay OFF
}

void loop() {
  if (Serial.available() > 0) {
    String cmd = Serial.readStringUntil('\n');
    cmd.trim();
    if (cmd == "ON") {
      digitalWrite(relayPin, LOW); // Turn light ON
    } else if (cmd == "OFF") {
      digitalWrite(relayPin, HIGH); // Turn light OFF
    }
  }
}

