# Water-Level-Monitoring-System-Using-IoT
 IoT-based Mini Project for Real-Time Water Level Monitoring using ESP32 and Firebase


Team Members:
B. Umesh Chandra (20241A04I6)
B. Neha (20241A04I7)
Guide: A. Lavanya (Assistant Professor, GRIET)

 Project Overview :
The Water Level Monitoring System is an IoT-based smart solution designed to monitor water levels in tanks, reservoirs, and other water bodies. By integrating ultrasonic sensors, OLED display, buzzer, and ESP32, the system measures water levels in real-time and provides alerts to users through a mobile app interface using Firebase Cloud and Kodular.

 Key Features :
- Real-time water level measurement using Ultrasonic Sensor
- Visual display via OLED
- Audible alert system using Buzzer
- Remote monitoring via IoT (ESP32 + Firebase)
- Android app for user interface (developed using Kodular)
- Cloud database integration with Firebase Realtime Database

Components Used :
ESP32 DevKit V1 – IoT Microcontroller
Ultrasonic Sensor (HC-SR04) – Distance sensing
OLED Display (0.96", I2C) – Level visualization
LED and Buzzer – Alerts and warnings
Push Button & Transistor Circuits – Manual reset/control
Grove Connectors – Plug-and-play sensor integration

 Architecture & Workflow :
Project Workflow:
- Hardware Setup
- Sensors connected to ESP32 via GPIO pins.
- Data Acquisition
- Ultrasonic sensor measures water height.
- Data Display
- OLED shows level status; buzzer/LED give alerts.
- Cloud Storage
- Sensor data sent to Firebase.
- Mobile Monitoring
- User views status through Kodular-based Android app.

 Technologies Used :
Hardware: ESP32, Ultrasonic Sensor, OLED, Buzzer, LED
Software: Arduino IDE, Firebase, Kodular (Mobile App Builder)
Languages: C++ (Arduino), Blockly (Kodular)

Cloud: Firebase Realtime Database

-  Mobile App Interface
- Built using Kodular, enabling:
- Realtime water level display
- Visual alerts
- Data fetching from Firebase
- Responsive UI

  CODE:

#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#include "FirebaseESP32.h"
#define OLED_ADDRESS 0x3C
Adafruit_SSD1306 display(128, 64, &Wire, OLED_ADDRESS);
#define trig 12
#define echo 13
#define THRESHOLD_DISTANCE 50
#define FIREBASE_HOST "iot-lab-569ed-default-rtdb.firebaseio.com"
#define FIREBASE_AUTH "sVp4muWqQHuCU5HGxuaG5WmEWCXf4Aq9AlFsJRzN"
#define WIFI_SSID "IDEAlab01"
#define WIFI_PASSWORD "griet@idealab"
FirebaseData firebaseData;
void setup() {
Serial.begin(9600);
display.begin(SSD1306_SWITCHCAPVCC, OLED_ADDRESS);
display.clearDisplay();
display.setTextColor(SSD1306_WHITE);
display.setTextSize(1);
display.setCursor(0, 0);
display.println("waterlevel_monitoring");
display.setCursor(4, 16);
display.println("System");
display.display();
delay(4000);
display.clearDisplay();
pinMode(trig, OUTPUT);
pinMode(echo, INPUT);
//Connecting to Wi-Fi network
WiFi.begin(WIFI_SSID, WIFI_PASSWORD);
Serial.print("Connecting to Wi-Fi");
while (WiFi.status() != WL_CONNECTED)
{
Serial.print(".");
digitalWrite(25,HIGH);
delay(1000);
digitalWrite(25,LOW);
}
Serial.println();
Serial.print("Connected with IP: ");
digitalWrite(33,HIGH);
digitalWrite(12,HIGH);
delay(500);
digitalWrite(33,LOW);
digitalWrite(12,LOW);
Serial.println(WiFi.localIP());
Serial.println();
Firebase.begin(FIREBASE_HOST, FIREBASE_AUTH);
Firebase.reconnectWiFi(true);
}
void loop() {
ultrasonic();
}
void ultrasonic() {
digitalWrite(trig, LOW);
delayMicroseconds(4);
digitalWrite(trig, HIGH);
delayMicroseconds(10);
digitalWrite(trig, LOW);
long t = pulseIn(echo, HIGH);
long cm = t / 29 / 2;
display.clearDisplay();
display.setCursor(0, 0);
if (cm>= THRESHOLD_DISTANCE) {
display.println("WARNING: Low water level!");
Firebase.setString(firebaseData,"Water Level","WARNING_Low_+water_level!");
Firebase.setInt(firebaseData,"Distance",cm);
}
else{
Serial.print("Water Level: ");
Firebase.setString(firebaseData,"Water Level","Water_Level_Normal");
Firebase.setInt(firebaseData,"Distance",cm);
Serial.print(cm);
Serial.println(" cm");
}
display.display();
display.setCursor(0, 16);
display.print("Distance: ");
display.print(cm);
display.print(" cm");
display.display();
delay(1000);
}
-

 Results :
- Water level detection is accurate up to ±2 cm
- Alerts trigger when the level crosses the defined threshold
- Mobile interface successfully displays and updates status in real-time
- Firebase successfully stores & retrieves sensor readings

 Future Scope :
Add ML algorithms for water usage prediction
Include water quality sensors (pH, turbidity)
Enable automatic pump control using actuators
Improve mobile app with push notifications
Share data with authorities or third-party systems for large-scale monitoring

 Repository Structure :
WaterLevelMonitoring-IoT/
│
├── README.md                   ← Project overview
├── Code/                       ← Arduino source code
│   └── water_level.ino
├── MobileApp/                  ← Kodular AIA file or screenshots
├── CircuitDiagrams/           ← PNG/PDF diagrams
├── Report/                     ← Final PDF project report
│   └── MiniProject_D14.pdf
├── Firebase_Screenshots/       ← Firebase DB setup screenshots
└── Images/                     ← OLED display, sensor setup, results

 Conclusion :
This mini project demonstrates the integration of hardware and cloud to build a smart and affordable IoT solution for efficient water resource management. With real-time data visualization and alerts, this system is highly scalable for use in homes, agriculture, and industries.
