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
